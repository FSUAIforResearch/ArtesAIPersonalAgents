# Example Output

## 1. Dataset Status

**Status: Not ready for analysis.**

The workbook is readable and its intended hierarchy is documented, but several issues must be resolved before records are joined or analyzed:

- the participant table contains a duplicate primary-key row;
- the visit and laboratory tables contain both exact and conflicting repeated composite keys;
- participant and site identifiers do not reconcile across sheets;
- three date fields contain text instead of valid dates;
- documented range, category, unit, chronology, and conditional-missingness rules are violated; and
- duplicate parent keys make some apparent many-to-one relationships ambiguous.

No source data were modified, standardized, trimmed, recoded, filtered, or imputed during this assessment.

## 2. Workbook Inventory

| Sheet | Role | Data rows | Variables | Notes |
|---|---|---:|---:|---|
| `Study_Overview` | Documentation and formula-derived summary | Not a source-data table | - | Contains the study hierarchy, testing prompt, and five live record-count formulas. |
| `Sites` | Site-level source data | 5 | 8 | Intended grain is one row per research site. |
| `Participants` | Participant-level source data | 19 | 8 | Intended grain is one row per participant, but only 18 distinct `Participant_ID` values are present. |
| `Visit_Records` | Repeated-measures source data | 58 | 8 | Intended grain is one row per `Participant_ID` and `Visit_Number`. |
| `Lab_Results` | Repeated laboratory measurements | 93 | 7 | Intended grain is one row per participant, visit, and analyte. |
| `Data_Dictionary` | Metadata and validation rules | 31 | 8 | Documents types, units, categories, keys, relationships, missingness, and validation rules. |

Across the four source-data tables, the workbook contains **175 data rows and 31 variables**. Counts in `Study_Overview` agree with the source-table row counts.

## 3. Structural Assessment

The workbook has a **mixed hierarchical and longitudinal repeated-measures structure**:

`Sites` -> `Participants` -> `Visit_Records` -> `Lab_Results`

The documented units of observation are:

- `Sites`: one research site;
- `Participants`: one enrolled participant;
- `Visit_Records`: one participant at one scheduled visit; and
- `Lab_Results`: one analyte result for one participant visit.

`Visit_Records` contains repeated observations nested within participants. `Lab_Results` contains two intended analyte measurements nested within participant visits. The participant and visit levels therefore are not independent rows.

The structure is usable in principle, but duplicate parent keys and exact-string identifier mismatches currently prevent unambiguous joins.

## 4. Variable Profile

### `Sites` - 5 rows

| Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule |
|---|---|---:|---:|---|---|
| `Site_ID` | Text | 5 / 0 | 5 | `ST01`-`ST05` | Primary key; unique and nonblank. |
| `Site_Name` | Text | 5 / 0 | 5 | Five distinct site names | Nonblank label. |
| `Region` | Text | 5 / 0 | 5 | North 1; Central 1; South 1; East 1; West 1 | Documented categories. |
| `Site_Type` | Text | 5 / 0 | 4 | Clinic 2; Research Center 1; Community Lab 1; Mobile Unit 1 | Documented categories. |
| `Status` | Text | 5 / 0 | 2 | Active 4; Inactive 1 | Documented categories. |
| `Install_Date` | Date and text | 5 / 0 | 5 | Valid dates: 2024-03-15 to 2024-07-11; text value `unknown` 1 | Must be a valid date. Four cells are formula-derived dates. |
| `Latitude` | Numeric | 5 / 0 | 5 | 25.7617 to 91.2 | Must be -90 to 90. |
| `Longitude` | Numeric | 5 / 0 | 5 | -87.2169 to -80.1918 | Must be -180 to 180. |

### `Participants` - 19 rows

| Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule |
|---|---|---:|---:|---|---|
| `Participant_ID` | Text | 19 / 0 | 18 | `P006` occurs twice | Intended primary key. |
| `Site_ID` | Text | 19 / 0 | 6 | ST01 5; ST02 4; ST03 3; ST04 3; ST05 3; ST99 1 | Foreign key to `Sites.Site_ID`. |
| `Age` | Numeric integer | 19 / 0 | 18 | 17 to 58 | Must be 18 to 80. |
| `Sex` | Text | 19 / 0 | 3 | Female 8; Male 10; `female` 1 | Expected Female or Male. |
| `Study_Group` | Text | 19 / 0 | 2 | Control 10; Intervention 9 | Documented categories. |
| `Consent_Status` | Text | 19 / 0 | 2 | Yes 17; `Y` 2 | Expected Yes or No. The two `Y` rows are the duplicated P006 record. |
| `Enrollment_Date` | Date and text | 19 / 0 | 18 | Valid dates: 2026-08-03 to 2026-08-20; text value `2026-02-30` 1 | Valid date in August 2026. Eighteen cells are formula-derived dates. |
| `Baseline_Score` | Numeric | 19 / 0 | 18 | 52 to 108 | Must be 0 to 100. |

### `Visit_Records` - 58 rows

| Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule |
|---|---|---:|---:|---|---|
| `Participant_ID` | Text | 58 / 0 | 20 | Includes `P010 ` with trailing space and `P999` | Foreign key to `Participants.Participant_ID`; no surrounding spaces. |
| `Visit_Number` | Numeric integer | 58 / 0 | 4 | Visit 1: 20; visit 2: 19; visit 3: 18; visit 4: 1 | Expected 1, 2, or 3; composite key with participant. |
| `Visit_Date` | Date and text | 58 / 0 | 46 | Valid dates: 2026-09-02 to 2026-10-30; text value `09/31/2026` 1 | Valid date; later visits must not precede earlier visits. Fifty-seven cells are formula-derived dates. |
| `Visit_Status` | Text | 58 / 0 | 2 | Completed 57; Missed 1 | Documented categories. |
| `Study_Hours` | Numeric | 57 / 1 (1.7%) | 11 | 2.5 to 8.9 | Required for Completed; blank for Missed. |
| `Quiz_Score` | Numeric | 57 / 1 (1.7%) | 37 | 60 to 112 | 0 to 100 for Completed; blank for Missed. |
| `Satisfaction` | Numeric integer | 57 / 1 (1.7%) | 4 nonblank values | 3: 19; 4: 18; 5: 19; 6: 1 | 1 to 5 for Completed; blank for Missed. |
| `Adherence_Pct` | Numeric and text | 57 / 1 (1.7%) | 12 | Numeric range 72% to 94%; text value `N/A` 1 | Numeric 0% to 100% for Completed; blank for Missed. |

### `Lab_Results` - 93 rows

| Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule |
|---|---|---:|---:|---|---|
| `Participant_ID` | Text | 93 / 0 | 17 | Includes two `P010 ` rows and one `P999` row | Foreign key to Participants; no surrounding spaces. |
| `Visit_Number` | Numeric integer | 93 / 0 | 3 | Visit 1: 32; visit 2: 31; visit 3: 30 | Must match a participant-visit key. |
| `Analyte` | Text | 93 / 0 | 3 | Cortisol 47; CRP 45; `C-Reactive Protein` 1 | Expected Cortisol or CRP; part of composite key. |
| `Result_Value` | Numeric, text, and blank | 92 / 1 (1.1%) | 78 nonblank values | Numeric range -1.2 to 19.9; `below detection` 1 | Numeric when present and nonnegative. Missing values are allowed. |
| `Unit` | Text | 93 / 0 | 3 | ng/mL 47; mg/L 45; g/L 1 | Cortisol: ng/mL; CRP: mg/L. |
| `Result_Date` | Date | 93 / 0 | 44 | 2026-08-30 to 2026-10-15 | Must be on or after the corresponding visit. All 93 cells are formula-derived dates. |
| `Lab_Batch` | Text | 93 / 0 | 4 | B1 23; B2 24; B3 22; B4 24 | Documented categories B1-B4. |

## 5. Missingness and Type Assessment

The workbook contains **five blank source-data cells**:

| Sheet | Variable | Missing | Percentage | Assessment |
|---|---|---:|---:|---|
| `Visit_Records` | `Study_Hours` | 1 | 1.7% | P003 visit 2 is Completed, so the blank violates the conditional rule. |
| `Visit_Records` | `Quiz_Score` | 1 | 1.7% | The blank occurs on the single Missed visit and is consistent with the dictionary. |
| `Visit_Records` | `Satisfaction` | 1 | 1.7% | The blank occurs on the single Missed visit and is consistent with the dictionary. |
| `Visit_Records` | `Adherence_Pct` | 1 | 1.7% | The blank occurs on the single Missed visit and is consistent with the dictionary. |
| `Lab_Results` | `Result_Value` | 1 | 1.1% | Missing results are explicitly allowed. |

Blank cells must be distinguished from nonblank malformed values. The following nonblank entries create mixed stored types:

- `Sites.Install_Date`: `unknown`;
- `Participants.Enrollment_Date`: `2026-02-30`;
- `Visit_Records.Visit_Date`: `09/31/2026`;
- `Visit_Records.Adherence_Pct`: `N/A`; and
- `Lab_Results.Result_Value`: `below detection`.

## 6. Identifiers, Keys, and Duplicates

| Candidate key | Rows | Unique keys | Repeated groups | Extra rows | Assessment |
|---|---:|---:|---:|---:|---|
| `Sites.Site_ID` | 5 | 5 | 0 | 0 | Valid primary-key candidate. |
| `Participants.Participant_ID` | 19 | 18 | 1 | 1 | P006 is an exact duplicated row, so the intended participant primary key is not unique. |
| `Visit_Records.Participant_ID + Visit_Number` | 58 | 56 | 2 | 2 | P002/visit 1 is an exact duplicate; P008/visit 2 is a conflicting repeated key. |
| `Lab_Results.Participant_ID + Visit_Number + Analyte` | 93 | 91 | 2 | 2 | P002/visit 1/Cortisol is an exact duplicate; P005/visit 2/CRP is a conflicting repeated key. |

Exact duplicate-row assessment:

- `Sites`: 0 duplicate groups and 0 extra rows;
- `Participants`: 1 group containing two identical P006 rows, or 1 extra row;
- `Visit_Records`: 1 group containing two identical P002/visit 1 rows, or 1 extra row; and
- `Lab_Results`: 1 group containing two identical P002/visit 1/Cortisol rows, or 1 extra row.

The P008 visit records and P005 CRP records are **not exact duplicate rows** because their non-key values conflict.

## 7. Cross-Sheet Relationships

| Child -> parent | Linking fields | Observed matches | Unmatched | Relationship assessment |
|---|---|---:|---:|---|
| `Participants` -> `Sites` | `Site_ID` | 18 of 19 rows | 1 | Many-to-one is supported for matched rows because `Sites.Site_ID` is unique. P018 references ST99, which is absent from Sites. |
| `Visit_Records` -> `Participants` | `Participant_ID` | 56 of 58 rows | 2 | Expected many-to-one, but the parent participant key is not unique because P006 is duplicated. `P010 ` and P999 do not match exact participant IDs. Three P006 visit rows also have two possible parent rows. |
| `Lab_Results` -> `Participants` | `Participant_ID` | 90 of 93 rows | 3 | Expected many-to-one, but P006 is duplicated. Two `P010 ` rows and one P999 row are unmatched; six P006 lab rows have two possible participant parents. |
| `Lab_Results` -> `Visit_Records` | `Participant_ID + Visit_Number` | 93 of 93 rows | 0 | Every lab row finds at least one visit key, but the visit key is not unique. Five lab rows reference duplicated visit keys: three for P002/visit 1 and two for P008/visit 2. |

The P010 values demonstrate why identifiers should not be silently trimmed: the trailing-space records match between `Visit_Records` and `Lab_Results`, but they do not match the participant table as stored.

## 8. Data-Dictionary Rule Checks

The following documented violations were observed:

| Sheet and field | Affected rows | Evidence |
|---|---:|---|
| `Sites.Install_Date` | 1 | ST04 stores `unknown` instead of a valid date. |
| `Sites.Latitude` | 1 | ST05 has latitude 91.2, outside -90 to 90. |
| `Participants.Site_ID` | 1 | P018 references missing site ST99. |
| `Participants.Age` | 1 | P004 has age 17, below the allowed minimum of 18. |
| `Participants.Sex` | 1 | P009 stores `female`, not the documented category `Female`. |
| `Participants.Consent_Status` | 2 rows / 1 duplicated ID | Both duplicated P006 rows store `Y`, not Yes or No. |
| `Participants.Enrollment_Date` | 1 | P015 stores text `2026-02-30`, which is not a valid August 2026 date. |
| `Participants.Baseline_Score` | 1 | P012 has 108, above 100. |
| `Visit_Records.Participant_ID` | 2 | `P010 ` has trailing whitespace and P999 has no participant parent. |
| `Visit_Records.Visit_Number` | 1 | P013 contains visit 4; only 1-3 are documented. |
| `Visit_Records.Visit_Date` | 2 distinct problems | P016/visit 3 stores invalid text `09/31/2026`; P005/visit 3 occurs before visit 2. |
| `Visit_Records.Study_Hours` | 2 conditional violations | P003/visit 2 is Completed but blank; P014/visit 2 is Missed but contains 5.5. |
| `Visit_Records.Quiz_Score` | 1 | P007/visit 2 has 112, above 100. |
| `Visit_Records.Satisfaction` | 1 | P009/visit 1 has 6, above 5. |
| `Visit_Records.Adherence_Pct` | 1 | P011/visit 3 stores text `N/A` rather than a numeric percentage. |
| `Lab_Results.Participant_ID` | 3 | Two `P010 ` rows and one P999 row do not match Participants exactly. |
| `Lab_Results.Analyte` | 1 | P006/visit 1 stores `C-Reactive Protein` instead of CRP. |
| `Lab_Results.Result_Value` | 2 distinct problems | P007/visit 2/Cortisol stores `below detection`; P011/visit 2/CRP is -1.2. |
| `Lab_Results.Unit` | 1 | P004/visit 3/CRP uses g/L instead of mg/L. |
| `Lab_Results.Result_Date` | 1 | P012/visit 1/Cortisol is dated 2026-08-30, before the corresponding visit. |

The dictionary permits missing `Lab_Results.Result_Value`, so the one blank result is not itself a violation.

## 9. Priority Issues

### Must be resolved before analysis

1. Resolve the exact P006 duplicate in `Participants` so participant-level joins have a unique parent key.
2. Resolve the repeated visit keys for P002/visit 1 and P008/visit 2.
3. Resolve the repeated laboratory keys for P002/visit 1/Cortisol and P005/visit 2/CRP.
4. Reconcile ST99, P999, and the trailing-space `P010 ` identifiers without silently changing them.
5. Correct or explicitly adjudicate the three malformed date values.
6. Resolve values that violate documented numeric ranges or contain text in numeric fields.
7. Resolve the CRP unit mismatch before combining or comparing laboratory results.
8. Resolve the visit and laboratory chronology violations.

### May be acceptable only if documented

- The blank laboratory result is permitted by the dictionary.
- The text `below detection` may represent censoring rather than an ordinary numeric value, but the workbook does not document how it should be encoded or analyzed.
- The 57-to-1 Completed/Missed distribution is highly imbalanced, but the workbook does not establish whether that distribution is erroneous.

### Unsupported or unresolved

The workbook does not provide enough evidence to decide:

- whether repeated or conflicting key records should be removed, retained, or reconciled;
- whether `Y`, `female`, and `C-Reactive Protein` are approved aliases;
- whether `N/A` means missing, not applicable, or a collection failure;
- whether the g/L value is a mislabeled unit or requires numeric conversion; or
- how a below-detection laboratory result should be represented.

## 10. Readiness Assessment

**Not ready for analysis.**

The workbook has a clear documented design and is suitable for profiling, but it is not ready for reliable participant-level, longitudinal, or laboratory analysis. Primary and composite keys are not consistently unique, some child records do not match parent identifiers, and several documented type, range, category, unit, conditional, and chronology rules are violated.

Analysis could proceed only after the researcher resolves the key conflicts and confirms how the ambiguous values should be handled. Any preparation should preserve the original workbook and document before-and-after row counts and all approved changes.

## 11. Questions Before Analysis

1. Should the second P006 participant row and the exact P002 visit and laboratory duplicates be removed, or do they represent separate source events?
2. Which P008/visit 2 and P005/visit 2/CRP records are authoritative, or should both be retained with an additional distinguishing field?
3. Should `P010 ` be treated as P010, and may identifiers be trimmed with explicit approval?
4. Are `Y`, `female`, and `C-Reactive Protein` approved aliases for the documented categories?
5. What do `N/A` and `below detection` mean, and how should each be represented for analysis?
6. Is the CRP result recorded in g/L correctly labeled, and if so, is an approved unit conversion required?
7. What are the correct dates for ST04 installation, P015 enrollment, and P016 visit 3?
8. Should P018/ST99 and P999 be linked to missing parent records, corrected to existing identifiers, or excluded with approval?
