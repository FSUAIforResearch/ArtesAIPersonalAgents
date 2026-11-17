# Example Output: Research Data First Look

Below is an example of what your ArtesAI **Research Data First Look** agent will generate when given [`Research Data First Look - Showcase Study.xlsx`](./Research%20Data%20First%20Look%20-%20Showcase%20Study.xlsx) and the prompt in [`example-input.md`](./example-input.md):

This output was generated with ArtesAI using gpt-6-luna on 2026/11/17.
---

# Workbook Profile and Analysis Readiness Report

## 1. Dataset status

**Not ready for analysis.** The workbook’s intended hierarchy is understandable, and its summary counts agree with the underlying tables. But the data contain blocking key and join problems, orphan records, rule violations, mixed-type and malformed entries, date inconsistencies, and duplicate keys. **I did not modify or clean the workbook.**

## 2. Workbook inventory

| Sheet | Role | Data rows | Variables | Notes |
|---|---|---:|---:|---|
| `Study_Overview` | Workbook guide and summary | 5 listed tables; narrative content also present | 8 columns in the layout | Five `ROWS(...)` formulas have cached counts of 5, 19, 58, 93, and 31. Each agrees with the corresponding underlying table row count. |
| `Sites` | Research locations | 5 | 8 | Excel table `tblSites`. |
| `Participants` | Participant enrollment | 19 | 8 | Excel table `tblParticipants`; only 18 distinct IDs because `P006` occurs twice. |
| `Visit_Records` | Repeated study visits | 58 | 8 | Excel table `tblVisits`; one exact repeated record and one conflicting repeated key. |
| `Lab_Results` | Biomarker measurements | 93 | 7 | Excel table `tblLabResults`; one exact repeated record and one conflicting repeated key. |
| `Data_Dictionary` | Field definitions and validation rules | 31 documented fields | 8 | Excel table `tblDictionary`; documents field roles, allowed values, missingness, and validation rules. |

The overview counts match the data tables exactly: **Sites 5; Participants 19; Visit_Records 58; Lab_Results 93; Data_Dictionary 31.**

## 3. Structure and join safety

The workbook describes a hierarchical, repeated-measures structure:

- `Sites`: one row per site; intended key `Site_ID`.
- `Participants`: one row per participant; intended key `Participant_ID`.
- `Visit_Records`: one row per participant and visit; intended key `Participant_ID + Visit_Number`.
- `Lab_Results`: one row per participant, visit, and analyte; intended key `Participant_ID + Visit_Number + Analyte`.

**Joins are not currently safe.** `Participants` has duplicate `Participant_ID` values; `Visit_Records` has repeated composite keys; there is a site foreign key not present in `Sites`; some participant IDs in child tables contain trailing whitespace or have no parent record. The exact duplicate parent and visit keys also make some joins ambiguous.

## 4. Variable profile

**Notation:** `nonmissing / missing`; date ranges use evaluated formula results and exclude non-date text. `Formula-derived` identifies cells stored as formulas. Category counts reflect exact stored labels, including spelling, case, and whitespace. Numeric ranges exclude nonnumeric text.

### `Sites` — 5 rows

| Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule |
|---|---|---:|---:|---|---|
| `Site_ID` | Text | 5 / 0 | 5 | `ST01`:1, `ST02`:1, `ST03`:1, `ST04`:1, `ST05`:1 | Primary key; unique, nonblank; documented range `ST01-ST99`. |
| `Site_Name` | Text | 5 / 0 | 5 | `North River Clinic`:1; `Lakeside Research Center`:1; `Pine Ridge Community Lab`:1; `Coastal Mobile Unit`:1; `Highland Outreach Site`:1 | Site display name; nonblank. |
| `Region` | Text | 5 / 0 | 5 | `North`:1, `Central`:1, `South`:1, `East`:1, `West`:1 | Documented categories. |
| `Site_Type` | Text | 5 / 0 | 4 | `Clinic`:2, `Research Center`:1, `Community Lab`:1, `Mobile Unit`:1 | Documented categories. |
| `Status` | Text | 5 / 0 | 2 | `Active`:4, `Inactive`:1 | Documented categories. |
| `Install_Date` | Date and text; 4 formula-derived dates | 5 / 0 | 5 | Dates: 2024-03-15 to 2024-07-11; text: `unknown` (1) | Date; valid date required. |
| `Latitude` | Numeric | 5 / 0 | 5 | 25.7617 to 91.2 | Decimal degrees; −90 to 90. |
| `Longitude` | Numeric | 5 / 0 | 5 | −87.2169 to −80.1918 | Decimal degrees; −180 to 180. |

### `Participants` — 19 rows

| Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule |
|---|---|---:|---:|---|---|
| `Participant_ID` | Text | 19 / 0 | 18 | `P001`–`P005`:1 each; `P006`:2; `P007`–`P018`:1 each | Primary key; unique, nonblank. |
| `Site_ID` | Text | 19 / 0 | 6 | `ST01`:5, `ST02`:4, `ST03`:3, `ST04`:3, `ST05`:3, `ST99`:1 | Foreign key to `Sites.Site_ID`. |
| `Age` | Integer | 19 / 0 | 18 | 17 to 58 | Years; 18 to 80. |
| `Sex` | Text | 19 / 0 | 3 | `Female`:8, `Male`:10, `female`:1 | Documented categories: `Female`; `Male`. |
| `Study_Group` | Text | 19 / 0 | 2 | `Intervention`:9, `Control`:10 | Documented categories. |
| `Consent_Status` | Text | 19 / 0 | 2 | `Yes`:17, `Y`:2 | Documented categories: `Yes`; `No`. |
| `Enrollment_Date` | Date and text; 18 formula-derived dates | 19 / 0 | 18 | Dates: 2026-08-03 to 2026-08-20; text: `2026-02-30` (1) | Date; valid date in August 2026. |
| `Baseline_Score` | Integer | 19 / 0 | 18 | 52 to 108 | Points; 0 to 100. |

### `Visit_Records` — 58 rows

| Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule |
|---|---|---:|---:|---|---|
| `Participant_ID` | Text | 58 / 0 | 20 | `P001`:3, `P002`:4, `P003`:3, `P004`:3, `P005`:3, `P006`:3, `P007`:3, `P008`:4, `P009`:3, `P010`:2, `P010 `:1, `P011`:3, `P012`:3, `P013`:4, `P014`:3, `P015`:3, `P016`:3, `P017`:3, `P018`:3, `P999`:1 | Foreign key to participant; no leading/trailing spaces. The label `P010 ` includes a trailing space. |
| `Visit_Number` | Integer | 58 / 0 | 4 | 1 to 4 | Expected 1, 2, or 3; unique with `Participant_ID`. |
| `Visit_Date` | Date and text; 57 formula-derived dates | 58 / 0 | 46 | Evaluated dates: 2026-09-02 to 2026-10-30; text: `09/31/2026` (1) | Valid date; later visits must not precede earlier visits. |
| `Visit_Status` | Text | 58 / 0 | 2 | `Completed`:57, `Missed`:1 | Documented categories. |
| `Study_Hours` | Numeric | 57 / 1 | 11 | 2.5 to 8.9 | Hours; required when completed, blank when missed. |
| `Quiz_Score` | Integer | 57 / 1 | 37 | 60 to 112 | Points; 0–100 when completed, blank when missed. |
| `Satisfaction` | Integer | 57 / 1 | 4 | 3 to 6 | 1–5 when completed, blank when missed. |
| `Adherence_Pct` | Numeric and text | 57 / 1 | 12 | Numeric: 0.72 to 0.94; text: `N/A` (1) | Percent; 0%–100% when completed, blank when missed. |

### `Lab_Results` — 93 rows

| Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule |
|---|---|---:|---:|---|---|
| `Participant_ID` | Text | 93 / 0 | 17 | `P001`:6, `P002`:7, `P003`:6, `P004`:6, `P005`:7, `P006`:6, `P007`:6, `P008`:6, `P009`:6, `P010`:4, `P010 `:2, `P011`:6, `P012`:6, `P013`:6, `P014`:6, `P015`:6, `P999`:1 | Foreign key to participant; no leading/trailing spaces. |
| `Visit_Number` | Integer | 93 / 0 | 3 | 1 to 3 | Foreign key to participant/visit composite key. |
| `Analyte` | Text | 93 / 0 | 3 | `Cortisol`:47, `CRP`:45, `C-Reactive Protein`:1 | Documented categories: `Cortisol`; `CRP`. |
| `Result_Value` | Numeric and text | 92 / 1 | 78 | Numeric: −1.2 to 19.9; text: `below detection` (1) | Numeric when present; nonnegative by analyte; missing is allowed. |
| `Unit` | Text | 93 / 0 | 3 | `ng/mL`:47, `mg/L`:45, `g/L`:1 | `Cortisol: ng/mL`; `CRP: mg/L`. |
| `Result_Date` | Date; 93 formula-derived dates | 93 / 0 | 44 | 2026-08-30 to 2026-10-15 | Valid date on or after corresponding visit date. |
| `Lab_Batch` | Text | 93 / 0 | 4 | `B1`:23, `B2`:24, `B3`:22, `B4`:24 | Documented categories. |

## 5. Missingness and type assessment

Percentages use each sheet’s data-row count as the denominator.

| Sheet | Variable | Missing | Percentage | Assessment |
|---|---|---:|---:|---|
| `Visit_Records` | `Study_Hours` | 1 | 1/58 = 1.7241% | Blank at row 9 (`P003`, visit 2), although the visit is `Completed`; violates the conditional requiredness rule. |
| `Visit_Records` | `Quiz_Score` | 1 | 1/58 = 1.7241% | Blank at row 42 (`P014`, visit 2, `Missed`); permitted by the conditional rule. |
| `Visit_Records` | `Satisfaction` | 1 | 1/58 = 1.7241% | Blank at row 42 (`P014`, visit 2, `Missed`); permitted by the conditional rule. |
| `Visit_Records` | `Adherence_Pct` | 1 | 1/58 = 1.7241% | Blank at row 42 (`P014`, visit 2, `Missed`); permitted by the conditional rule. |
| `Lab_Results` | `Result_Value` | 1 | 1/93 = 1.0753% | Blank at row 55 (`P009`, visit 3, `CRP`); missing is explicitly allowed by the dictionary. |

These are **true blank cells**. They are distinct from nonblank text entries: `unknown` in `Sites.Install_Date`; `2026-02-30` in `Participants.Enrollment_Date`; `09/31/2026` in `Visit_Records.Visit_Date`; `N/A` in `Visit_Records.Adherence_Pct`; and `below detection` in `Lab_Results.Result_Value`.

Formula-derived dates also need review. `Visit_Records.Visit_Date` has 18 formulas and `Lab_Results.Result_Date` has 32 formulas using September day arguments 31–47. Excel evaluates these to dates in October. Those cached results are dates, but the formula inputs’ intended dates should be confirmed. Separately, the literal `09/31/2026` is stored as text and is not a valid calendar date.

## 6. Identifiers, keys, and duplicates

| Candidate key | Rows | Unique keys | Repeated groups | Extra rows | Assessment |
|---|---:|---:|---:|---:|---|
| `Sites.Site_ID` | 5 | 5 | 0 | 0 | Unique in the observed table. |
| `Participants.Participant_ID` | 19 | 18 | 1 | 1 | `P006` repeats at rows 7 and 20. These are an **exact duplicate row** across all stored fields; the primary-key rule is nevertheless violated. |
| `Visit_Records.Participant_ID + Visit_Number` | 58 | 56 | 2 | 2 | `P002 + 1` at rows 5 and 56 is an exact duplicate row. `P008 + 2` at rows 24 and 57 is a **conflicting repeated key**. |
| `Lab_Results.Participant_ID + Visit_Number + Analyte` | 93 | 91 | 2 | 2 | `P002 + 1 + Cortisol` at rows 8 and 92 is an exact duplicate row. `P005 + 2 + CRP` at rows 29 and 93 is a conflicting repeated key. |

## 7. Cross-sheet relationships

Counts below compare the identifiers **exactly as stored**—no trimming or normalization.

| Child → parent | Linking fields | Observed matches | Unmatched | Relationship assessment |
|---|---|---:|---:|---|
| `Participants` → `Sites` | `Site_ID` | 18/19 | 1 | `P018` row 19 uses `ST99`, absent from `Sites`. `Sites.Site_ID` itself is unique. |
| `Visit_Records` → `Participants` | `Participant_ID` | 56/58 | 2 | Row 31 stores `P010 ` with a trailing space; row 58 uses `P999`, absent from `Participants`. The three visit rows for `P006` match two parent rows because `Participants` duplicates that key. |
| `Lab_Results` → `Participants` | `Participant_ID` | 90/93 | 3 | Rows 60–61 store `P010 ` with a trailing space; row 94 uses `P999`. Six `P006` lab rows match two participant rows. |
| `Lab_Results` → `Visit_Records` | `Participant_ID + Visit_Number` | 93/93 | 0 | Every lab key has a matching visit key as stored, including the whitespace-bearing `P010 ` pair. Four lab rows link to duplicated parent visit keys: the two analytes at `P002 + 1` and the two at `P008 + 2`. |

## 8. Data-dictionary rule checks

| Sheet and field | Affected rows | Evidence |
|---|---|---|
| `Sites.Install_Date` | 5 | `ST04`: stored text `unknown`; valid date required. |
| `Sites.Latitude` | 6 | `ST05`: `91.2`, outside −90 to 90. |
| `Participants.Participant_ID` | 7, 20 | `P006` repeats; rows are exact duplicates, but the dictionary requires a unique key. |
| `Participants.Site_ID` | 19 | `P018`: `ST99` does not exist in `Sites`. |
| `Participants.Age` | 5 | `P004`: `17`, below the documented minimum of 18. |
| `Participants.Sex` | 10 | `P009`: `female`, not the documented case-sensitive label `Female` or `Male`. |
| `Participants.Consent_Status` | 7, 20 | `P006`: `Y`, not the documented `Yes` or `No`. |
| `Participants.Enrollment_Date` | 16 | `P015`: text `2026-02-30`, an impossible date and not in August 2026. |
| `Participants.Baseline_Score` | 13 | `P012`: `108`, above 100. |
| `Visit_Records.Participant_ID` | 31, 58 | Row 31: `P010 ` has a trailing space and fails exact parent matching. Row 58: `P999` has no participant parent. |
| `Visit_Records.Participant_ID + Visit_Number` | 5, 56; 24, 57 | `P002 + 1` repeats exactly; `P008 + 2` repeats with differing non-key fields. |
| `Visit_Records.Visit_Number` | 59 | `P013`: visit `4`; documented values are 1, 2, 3. |
| `Visit_Records.Visit_Date` | 16; 49 | `P005` visit 3 (row 16, evaluated 2026-09-10) precedes visit 2 (row 15, 2026-09-20). `P016` visit 3 (row 49) is stored as text `09/31/2026`. |
| `Visit_Records` conditional fields | 9; 42 | Completed `P003`, visit 2 has blank `Study_Hours` at row 9. Missed `P014`, visit 2 has `Study_Hours=5.5` at row 42, although the rule says blank when missed. The other three conditional fields at row 42 are blank as required. |
| `Visit_Records.Quiz_Score` | 21 | `P007`, visit 2: `112`, above 100. |
| `Visit_Records.Satisfaction` | 26 | `P009`, visit 1: `6`, above 5. |
| `Visit_Records.Adherence_Pct` | 34 | `P011`, visit 3: nonnumeric text `N/A`; the field is required for a completed visit. |
| `Lab_Results.Participant_ID` | 60, 61, 94 | Rows 60–61 store `P010 ` with trailing space; row 94 uses `P999`, absent from `Participants`. |
| `Lab_Results.Analyte` | 33 | `P006`, visit 1: `C-Reactive Protein`, not the documented label `CRP`. |
| `Lab_Results.Result_Value` | 40, 65 | `P007`, visit 2, Cortisol: text `below detection` where numeric when present is required; `P011`, visit 2, CRP: −1.2, below zero. The blank result at row 55 is allowed. |
| `Lab_Results.Unit` | 25 | `P004`, visit 3, CRP: `g/L`; documented unit is `mg/L`. |
| `Lab_Results.Result_Date` | 68 | `P012`, visit 1, Cortisol: 2026-08-30, before corresponding visit date 2026-09-13 (visit row 35). |

The workbook documents permitted missingness for `Lab_Results.Result_Value`; that blank is not treated as an error. The other blank fields in the missed visit are permitted by their conditional rules.

## 9. Priority issues

### Must be resolved before analysis

- Duplicate participant key `P006`, repeated visit keys, and repeated lab composite keys—including conflicting records.
- Orphan or exact-match failures: `ST99`, `P999`, and trailing-space `P010 ` identifiers.
- Documented range and label violations, including age, scores, satisfaction, latitude, consent, sex, and analyte.
- Invalid or questionable dates, including the impossible text dates, visit chronology reversal, lab date before visit, and overflowed `DATE(...)` formula arguments.
- CRP unit mismatch and negative lab result.
- Completed-visit blank `Study_Hours`, and nonblank `Study_Hours` on a missed visit.

### May be acceptable only if documented

- Blank `Lab_Results.Result_Value` at row 55: explicitly allowed by the dictionary.
- `below detection` may represent a censored measurement, but the file does not document how it should be represented analytically.
- Formula-derived dates evaluate to dates, but the overflowed formula arguments leave their intended dates uncertain.

### Unsupported or unresolved

- Whether exact duplicate records should be retained or removed, and which conflicting repeated-key records are authoritative.
- Whether `female`, `Y`, `C-Reactive Protein`, `N/A`, and `below detection` are valid aliases or source-entry errors.
- Whether `P010 ` is an intended distinct identifier or whitespace error.
- Whether `0.72`–`0.94` adherence values represent proportions equivalent to 72%–94%, or another convention. The dictionary says percent but does not specify the storage scale.
- The intended dates for malformed date text and overflowed date formulas, and how to reconcile orphan IDs.

## 10. Readiness assessment

**Not ready for analysis.** Although the workbook has a documented structure and its formula-derived overview counts reconcile with the data tables, blocking issues affect keys, joins, dates, units, allowed values, and conditional completeness. Before any cleaning, preserve the raw workbook and log all approved row- or value-level changes.

## 11. Questions before analysis

1. Should the exact duplicate rows be retained, removed, or resolved another way? What is the authoritative record for the conflicting `P008 + 2` visit and `P005 + 2 + CRP` lab keys?
2. Is the repeated `P006` participant row a duplicate enrollment, or are these intended to be separate records requiring distinct IDs?
3. Should trailing whitespace be removed from `P010 ` in visit and lab records, or does it signify a distinct identifier?
4. Are `female`, `Y`, and `C-Reactive Protein` approved aliases for the dictionary labels? If so, what mappings are authorized?
5. How should `N/A` and `below detection` be interpreted and represented? Should the latter be retained as a censored result rather than treated as missing?
6. What is the intended unit and scale for adherence values such as `0.78`—a proportion or a percent value?
7. What are the correct values for `2026-02-30`, `09/31/2026`, the overflowed date formulas, and the visit chronology reversal?
8. What are the authoritative participant/site records for `P999` and `ST99`, and should unmatched child records be retained, corrected, or excluded?