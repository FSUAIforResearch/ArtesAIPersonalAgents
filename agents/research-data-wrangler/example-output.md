# Example Output: Research Data Wrangler

Below is the expected output when you run the prompt from [`example-input.md`](./example-input.md) in your ArtesAI **Research Data Wrangler** agent:

---

## 1. Data Quality Audit

I inspected your 6-row sample from the Apalachicola Bay water quality dataset and identified **7 distinct data hygiene issues** that need to be handled programmatically before statistical analysis:

| Raw Column Header | Detected Anomalies in Sample | Recommended Programmatic Fix |
| :--- | :--- | :--- |
| `Site ID` | Case inconsistency & trailing whitespace (`"AB-01"` vs. `"ab-01 "`); exact duplicate row (`AB-02` on `2026-06-14` appears twice). | Strip whitespace, convert to uppercase, and deduplicate exact repeat records with logging. |
| `Sample Date` | 3 different date formats mixed together (`YYYY-MM-DD`, `MM/DD/YYYY`, and `DD-Mon-YYYY`). | Parse flexibly with `pd.to_datetime(..., format='mixed')` and standardize to ISO-8601 (`YYYY-MM-DD`). |
| `Water Temp (C)` | Embedded unit string (`"29.1 C"`) and a unit entry error (`84.2` recorded in °F instead of °C on row `AB-03`, confirmed by observer note). | Strip `" C"`, convert to float, and convert values `> 50` from °F to °C via `(F - 32) * 5/9` while flagging the conversion in a QA column. |
| `Salinity ppt` | Clean numeric values in sample (`18.5`–`31.2`), though header contains spaces. | Rename to `salinity_ppt` and validate estuarine bounds (`0` to `45` ppt). |
| `Dissolved_O2_mgL` | Sentinel value `-999` used for probe calibration error. | Replace `-999` (and any value `< 0`) with `NaN`. |
| `Turbidity_NTU` | Text string `"missing"` mixed with floats, plus physically impossible negative turbidity (`-4.2`). | Coerce `"missing"` and negative values (`< 0`) to `NaN` and log sensor errors. |
| `Observer Notes` | Free-text field containing critical QA context. | Preserve intact as `observer_notes` and add an automated `qa_flags` column to track programmatic corrections. |

---

## 2. Reproducible Cleaning Pipeline (`/clean-script` — R `tidyverse`)

Save the script below as `clean_water_quality.R`. It reads your raw file from `data_raw/` without modifying it, logs every transformation in a `qa_flags` column, runs validation checks, and writes the cleaned CSV to `data_clean/`:

```r
# ==============================================================================
# Reproducible Data Cleaning Pipeline: Apalachicola Bay Water Quality (tidyverse)
# Reads:  data_raw/apalachicola_water_raw.csv
# Writes: data_clean/apalachicola_water_clean.csv
# ==============================================================================

library(readr)
library(dplyr)
library(stringr)
library(lubridate)

raw_path   <- "data_raw/apalachicola_water_raw.csv"
clean_path <- "data_clean/apalachicola_water_clean.csv"

# ------------------------------------------------------------------------------
# Stage 1: Read Raw Data Safely & Standardize Column Names
# ------------------------------------------------------------------------------
df_raw <- read_csv(raw_path, col_types = cols(.default = col_character()), trim_ws = FALSE)
initial_rows <- nrow(df_raw)
message(sprintf("[AUDIT] Loaded %d raw rows from %s", initial_rows, raw_path))

df_dedup <- df_raw |>
  rename(
    site_id          = `Site ID`,
    sample_date      = `Sample Date`,
    water_temp_c     = `Water Temp (C)`,
    salinity_ppt     = `Salinity ppt`,
    dissolved_o2_mgl = Dissolved_O2_mgL,
    turbidity_ntu    = Turbidity_NTU,
    observer_notes   = `Observer Notes`
  ) |>
  distinct()

dups_dropped <- initial_rows - nrow(df_dedup)
message(sprintf("[AUDIT] Removed %d exact duplicate row(s).", dups_dropped))

# ------------------------------------------------------------------------------
# Stage 2 & 3: String Normalization, Date Parsing, & Sentinel Value Handling
# ------------------------------------------------------------------------------
sentinel_tokens <- c("-999", "-999.0", "missing", "N/A", "na", "null", "")

df_clean <- df_dedup |>
  mutate(
    qa_flags = "",
    # Standardize site_id & parse mixed date formats (YYYY-MM-DD, MM/DD/YYYY, DD-Mon-YYYY)
    site_id = str_to_upper(str_trim(site_id)),
    sample_date = as_date(parse_date_time(str_trim(sample_date), orders = c("ymd", "mdy", "dmy"))),

    # Strip embedded unit strings (e.g., "29.1 C" -> 29.1)
    water_temp_c = as.numeric(na_if(str_remove_all(water_temp_c, "[^0-9.-]"), "")),

    # Flag & convert accidental Fahrenheit entries (> 50 C) to Celsius
    is_fahrenheit = !is.na(water_temp_c) & water_temp_c > 50,
    qa_flags = if_else(is_fahrenheit, paste0(qa_flags, "temp_converted_from_F;"), qa_flags),
    water_temp_c = if_else(is_fahrenheit, round((water_temp_c - 32) * 5 / 9, 2), water_temp_c),

    # Convert sentinel missing tokens to NA across numeric sensor columns
    across(
      c(salinity_ppt, dissolved_o2_mgl, turbidity_ntu),
      ~ suppressWarnings(as.numeric(if_else(str_trim(.x) %in% sentinel_tokens, NA_character_, str_trim(.x))))
    ),

    # Replace physically impossible negative DO or Turbidity values with NA and log QA flag
    qa_flags = if_else(!is.na(dissolved_o2_mgl) & dissolved_o2_mgl < 0,
                       paste0(qa_flags, "dissolved_o2_mgl_negative_to_na;"), qa_flags),
    dissolved_o2_mgl = if_else(!is.na(dissolved_o2_mgl) & dissolved_o2_mgl < 0, NA_real_, dissolved_o2_mgl),

    qa_flags = if_else(!is.na(turbidity_ntu) & turbidity_ntu < 0,
                       paste0(qa_flags, "turbidity_ntu_negative_to_na;"), qa_flags),
    turbidity_ntu = if_else(!is.na(turbidity_ntu) & turbidity_ntu < 0, NA_real_, turbidity_ntu)
  ) |>
  select(-is_fahrenheit)

# ------------------------------------------------------------------------------
# Stage 4: Automated Sanity Checks / Assertions
# ------------------------------------------------------------------------------
stopifnot("Error: Missing site_id detected!" = sum(is.na(df_clean$site_id)) == 0)
stopifnot("Error: Unparsed sample_date!"     = sum(is.na(df_clean$sample_date)) == 0)
stopifnot("Error: Temp out of bounds!"       = all(df_clean$water_temp_c >= 0 & df_clean$water_temp_c <= 45, na.rm = TRUE))
stopifnot("Error: Salinity out of bounds!"   = all(df_clean$salinity_ppt >= 0 & df_clean$salinity_ppt <= 45, na.rm = TRUE))

message("\n[AUDIT] Missing Values Summary in Cleaned Dataset:")
print(colSums(is.na(df_clean)))

# ------------------------------------------------------------------------------
# Stage 5: Export Clean Dataset
# ------------------------------------------------------------------------------
dir.create(dirname(clean_path), recursive = TRUE, showWarnings = FALSE)
write_csv(df_clean, clean_path)
message(sprintf("\n[SUCCESS] Wrote %d cleaned rows to %s", nrow(df_clean), clean_path))
```

**To run from RStudio or your terminal:**
```bash
Rscript clean_water_quality.R
```
*(Need Python instead? Ask `/clean-script` for the `pandas` version!)*

---

## 3. Data Dictionary & Codebook (`/codebook`)

Copy the table below into `README_DATA.md` when uploading your dataset to OSF, Zenodo, or FSU DigiNole:

| Variable Name (`snake_case`) | Original Raw Header | Data Type | Units / Scale | Plausible Range / Allowed Values | Missing Value Representation | Clear Description |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `site_id` | `Site ID` | `string` | N/A | `AB-01` to `AB-99` | None allowed (Primary Key part) | Standardized uppercase identifier for the Apalachicola Bay monitoring station. |
| `sample_date` | `Sample Date` | `ISO-8601 date` | `YYYY-MM-DD` | `2026-01-01` to `2026-12-31` | None allowed (Primary Key part) | Calendar date on which the field water sample was collected. |
| `water_temp_c` | `Water Temp (C)` | `float` | `°C` (Celsius) | `5.0` to `40.0` | `NaN` (blank in CSV) | Surface water temperature measured at 0.5m depth, standardized to degrees Celsius. |
| `salinity_ppt` | `Salinity ppt` | `float` | `ppt` (parts per thousand) | `0.0` to `40.0` | `NaN` (blank in CSV) | Estuarine salinity concentration in parts per thousand. |
| `dissolved_o2_mgl` | `Dissolved_O2_mgL` | `float` | `mg/L` | `0.0` to `20.0` | `NaN` (raw sentinel `-999` recoded) | Dissolved oxygen concentration in milligrams per liter. |
| `turbidity_ntu` | `Turbidity_NTU` | `float` | `NTU` | `0.0` to `500.0` | `NaN` (raw `"missing"` or `< 0` recoded) | Nephelometric turbidity units measuring water cloudiness/suspended particulates. |
| `observer_notes` | `Observer Notes` | `string` | Free text | Any text | `NaN` (blank in CSV) | Unedited field notes recorded by the sampling crew. |
| `qa_flags` | *(Derived in cleaning)* | `string` | Semicolon-delimited codes | e.g., `temp_converted_from_F;` | Empty string `""` if no flags | Automated audit trail of programmatic unit conversions or range exclusions applied during cleaning. |

