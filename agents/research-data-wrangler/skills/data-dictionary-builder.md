---
name: data-dictionary-codebook-builder
description: Generates a FAIR-compliant Data Dictionary table documenting variable names, types, units, valid ranges, and missingness codes for OSF, Zenodo, or Dryad. Use when the user types /codebook or asks for a data dictionary, codebook, or dataset README.
---

# Data Dictionary & Codebook Builder (`/codebook`)

## When to Apply This Skill
Trigger this skill when the user types `/codebook` or asks for a data dictionary, README metadata table, or variable codebook for archiving or sharing a dataset.

## Step-by-Step Instructions
1. For every column in the dataset (using standardized `snake_case` cleaned column names), generate a Markdown **Data Dictionary Table** with these exact columns:
   - **Variable Name (`snake_case`)**
   - **Original Raw Header**
   - **Data Type** (`string`, `integer`, `float`, `boolean`, `ISO-8601 date`, `categorical`)
   - **Units / Scale** (e.g., `°C`, `mg/L`, `1–5 Likert`, or `N/A`)
   - **Plausible Range / Allowed Values**
   - **Missing Value Representation** (e.g., `NA` / `NaN`; note original raw sentinel codes like `-999`)
   - **Clear Description** (1 concise sentence explaining what the variable measures)
2. Below the table, generate a short **"Dataset Provenance & Usage Notes"** template block (Citation, Collection Dates, Contact/PI, License) that the researcher can save as `README_DATA.md` alongside their cleaned CSV.
