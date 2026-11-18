---
name: reproducible-cleaning-script-generator
description: Writes a defensive, non-destructive R (tidyverse) or Python (pandas) data-cleaning script with audit logging and validation assertions. Defaults to R tidyverse. Use when the user types /clean-script or asks for code to clean or standardize a dataset.
---

# Reproducible Cleaning Script Generator (`/clean-script`)

## When to Apply This Skill
Trigger this skill when the user types `/clean-script` or asks for R (`tidyverse`) or Python (`pandas`) code to clean and standardize their data.

## Step-by-Step Instructions
1. Default to **R (`tidyverse`: `readr`, `dplyr`, `stringr`, `lubridate`, `janitor`)** unless the user explicitly asks for **Python (`pandas`)**, and offer to translate to Python `pandas` if needed.
2. Structure the script into 5 clearly commented stages:
   - **Stage 1: Read Raw Data Safely** (read from `data_raw/` using `readr::read_csv(..., col_types = cols(.default = "c"))` without modifying the source file; standardize column names to `snake_case` via `janitor::clean_names()` or `dplyr::rename()`; log and remove exact duplicate rows via `dplyr::distinct()`).
   - **Stage 2: Type Parsing & String Cleaning** (strip embedded units with `stringr::str_remove_all()`, parse mixed date formats with `lubridate::parse_date_time()`, and normalize text case/whitespace with `stringr::str_squish()` / `str_to_upper()`).
   - **Stage 3: Missing & Sentinel Value Handling** (convert sentinel codes like `"-999"`, `"N/A"`, `"missing"` to standard `NA` and record automated QA flags in a `qa_flags` column).
   - **Stage 4: Automated Sanity Checks / Assertions** (verify primary keys and plausible numeric bounds with `stopifnot()`, and print a clear **Cleaning Audit Summary** showing row counts and missingness per column).
   - **Stage 5: Export Clean Dataset** (create `data_clean/` and save in CSV format with `readr::write_csv()`).
3. Include a short block at the end showing how to run the script in RStudio or from the terminal (`Rscript clean_dataset.R`).
