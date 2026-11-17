---
name: variable-and-missingness-profiler
description: Profiles every variable in a CSV or Excel workbook, reporting exact stored types, nonmissing/missing counts, reconciled category frequencies, numeric/date ranges, and mixed-type entries. Use for /profile-variables or variable and missingness audits.
---

# Variable & Missingness Profiler (`/profile-variables`)

## When to Apply This Skill
Activate this workflow whenever the user types `/profile-variables`, attaches this skill for a full dataset profile, or asks to inspect variables, data types, category distributions, ranges, or missing values.

## Step-by-Step Instructions
1. **Profile Every Variable Across Every Data Sheet (`## 4. Variable Profile`)**:
   - Do not omit variables that appear administrative or minor.
   - For each data sheet, output a Markdown table with these exact columns:
     `Variable | Observed type | Nonmissing / missing | Unique | Observed values or range | Documented role or rule`
   - **Stored Type vs. Semantic Role**: Report how values are actually stored (e.g., `Date and text` or `Numeric and text` when a numeric/date column contains text strings like `"unknown"`, `"2026-02-30"`, `"09/31/2026"`, `"N/A"`, or `"below detection"`). Note when cells are formula-derived.
   - **Exact Ranges & Reconciled Categories**:
     - For numeric and valid date values, report the exact observed minimum and maximum (excluding unreadable text strings, which must be listed separately with their exact count).
     - For categorical variables, list every distinct stored label (preserving case and spelling differences such as `Female` vs. `female` or `CRP` vs. `C-Reactive Protein`) with its exact frequency, and verify that the category counts sum to the nonmissing row count.
2. **Audit Missingness vs. Mixed Stored Types (`## 5. Missingness and Type Assessment`)**:
   - Calculate `missing percentage = missing count / sheet data-row count × 100`.
   - Present a summary table of all blank source-data cells:
     `Sheet | Variable | Missing | Percentage | Assessment`
   - Evaluate conditional missingness rules record by record (e.g., if a field is required when `Visit_Status = Completed` and blank when `Missed`, verify the status of every row with a blank cell).
   - Explicitly separate **true blank cells** from **nonblank malformed or mixed-type entries** (such as `"unknown"`, `"N/A"`, `"below detection"`, or impossible calendar dates stored as text), listing each mixed-type value by sheet and variable.
