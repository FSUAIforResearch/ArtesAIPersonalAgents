---
name: data-profile
description: Inspect and explain CSV or Excel research data before analysis, including variables, missingness, identifiers, repeated records, linked sheets, formulas, and documented quality rules.
---

# Data Profile

## Purpose

Inspect readable data before analysis and produce a factual, plain-language description of contents, structure, relationships, quality, and readiness. Use for CSV or Excel profiling, schema review, missingness, repeated records, linked sheets, formulas, and dictionary validation. Do not clean data, recommend analyses or visualizations, or make causal conclusions.

## Evidence rules

Classify material findings as **Verified finding**, **Metadata-supported finding**, **Inferred interpretation**, or **Requires confirmation**. Stored data establish what is present; metadata establish intended definitions and rules; formulas and structure provide supporting evidence; names and patterns support cautious inference only.

## Procedure

### 1. Confirm readability and scope

Report readable inputs, exact sheet/table names, inaccessible elements, formula availability, metadata availability, and whether the full relevant population was inspected. Never imply a preview is complete without verification.

### 2. Inventory every relevant sheet or table

Report exact dimensions, observation rows, variables, apparent purpose, apparent row grain, structural type, and whether the sheet contains data, metadata, calculations, instructions, or output. Separate headers, titles, notes, subtotals, blanks, and formatting-only rows from observations.

### 3. Inspect formulas and summaries

Identify formula-derived totals, counts, dates, fields, and summaries. Explain what they calculate, compare results with underlying data when possible, and flag errors or disagreements. Do not call verified formulas manually entered.

### 4. Profile every variable

For every variable report exact sheet and name, stored type, likely semantic type and role, documented units, exact numeric range or exact stored categories, exact category frequencies when shown, distinct count when useful, missing count and percentage, metadata rule, evidence classification, and status.

Preserve exact labels. Do not silently merge similar labels.

### 5. Calculate missingness

Use the applicable observation population. Report count, denominator, and percentage. Distinguish blank cells from stored missing-like labels. A text value in a numeric field is a type inconsistency unless metadata define it as a missing code. For conditional missingness, evaluate the condition for every blank.

### 6. Reconcile categories

Count every distinct stored label, calculate exact frequencies, sum them, and confirm the total equals the nonmissing population. Never use approximate counts when complete data are readable. Label partial category previews explicitly.

### 7. Report exact observed ranges

Calculate exact numeric minima and maxima separately from documented valid ranges. If a numeric field contains text or blanks, report the exact numeric range, nonnumeric values and keys, missing count, and validation rule. Do not call values invalid without a documented rule.

### 8. Assess identifiers and keys

Check uniqueness, missingness, format, exact duplicates, repeated keys, composite keys, and intentional sequences. A repeated identifier is not automatically a duplicate. Evaluate keys such as `Participant_ID + Visit`, `Student_ID + Week`, or `Sensor_ID + Timestamp`.

### 9. Verify duplicates

Compare every stored field. If all match, report `verified exact duplicate records in the supplied data`. If the key repeats but fields differ, report `a repeated key with conflicting stored values` and identify differences. Never treat verification as permission to delete.

### 10. Assess repeated and dependent observations

Look for repeated, paired, clustered, nested, longitudinal, multi-rater, or wide-to-long structures. Do not claim statistical independence or treatment effects. Distinguish internal balance from complete parent coverage.

### 11. Describe repeated-measures coverage precisely

Separate identifiers with expected records, expected sequence plus extras, incomplete sequences, malformed sequence fields, and child identifiers absent from the parent. An identifier with an extra duplicate still has repeated-measures structure. Label inferred schedules as inferred.

### 12. Assess cross-sheet and hierarchical relationships

For every hierarchy level identify parent, child, keys, cardinality, documentation status, and stored-type compatibility. Report keys present in both, parent only, child only, missing keys, duplicate parent keys, duplicate child composite keys, incompatible types, and formatting discrepancies.

Never silently trim whitespace, change case, remove punctuation, restore zeros, or convert types before matching.

### 13. Distinguish coverage from referential integrity

Call a child-only key a documented referential-integrity violation only when metadata require parent membership. Call a parent-only key a documented violation only when complete child coverage is required; otherwise call it a verified parent-table coverage gap requiring clarification. Preserve exact formatting discrepancies and require confirmation before equivalence.

### 14. Apply documented rules

Check categories, numeric bounds, dates, ordering, required values, missingness, conditional missingness, uniqueness, relationships, units, cross-variable rules, and formats. Classify each finding precisely as documented violation, exact duplicate, conflicting repeated key, permitted value/missingness, coverage gap, referential-integrity violation, possible inconsistency, unusual but not documented invalid, unclear, or could not verify.

### 15. Check units and cross-variable rules

Verify documented relationships record by record, such as measurement type/unit, quality flag/missing reading, copied site assignment, or visit/date order. Report key, stored values, rule, and conformance. Do not convert or recode.

### 16. Check dates and sequences

Report exact readable date minima and maxima, malformed values, affected keys, chronology, parent-child date constraints, and elapsed time when relevant. Do not include unreadable text in date ranges or assume equal intervals from labels.

### 17. Identify transformations and calculated fields

Report filtering, aggregation, recoding, binning, standardization, normalization, calculated variables, totals, percentages, scores, date-derived fields, and formulas only when supported by formulas, documentation, labels, or verifiable relationships.

### 18. Check grouping-variable alignment

Report perfect alignment among comparison variables and explain that their separate relationships cannot be distinguished from the supplied data alone. Do not recommend a statistical remedy.

### 19. Final consistency review

Before responding, verify that counts use the right population, percentages use the right denominator, ranges are exact, category frequencies reconcile, dimensions agree, formulas agree with data, duplicate terminology is correct, repeated-measures counts distinguish extra records, parent-child counts reconcile, permitted missingness is not called an error, conditional rules were evaluated, identifiers are preferred over row numbers, and every response section agrees. If a result cannot be verified, state `Could not verify`.

## Required output

### A. Quick Overview
Readable inputs, inventory, exact dimensions, apparent purpose and grain, structural findings, formula-derived summaries, metadata, and consequential verified issues.

### B. Variable Map
Use:

| Sheet | Variable | Stored Type | Likely Role | Units | Observed Values or Range | Missing | Metadata Rule | Status |
|---|---|---|---|---|---|---|---|---|

Use exact reconciled category counts and exact numeric ranges.

### C. Structure and Dependencies
Keys, duplicates, conflicting keys, repeated-measures coverage, clustering/nesting, hierarchy, cardinality, cross-sheet coverage, formatting discrepancies, alignment, formulas, and transformations.

### D. Data-Quality Flags
For each flag report sheet, field/key, meaningful identifier, exact value, rule, classification, significance, and confirmation requirement.

### E. Questions Before Analysis
Ask no more than three questions, preferably grouped into identifier/relationship resolution, duplicate resolution, and nonconforming value/format/type/unit/missingness resolution.

### F. Readiness Assessment
State what is interpretable, safe to describe/link, blocking, nonblocking, permitted missingness, restricted in usability, and unsupported.

## Restrictions

Do not modify, clean, standardize, normalize, delete, recode, convert units, impute, filter, or aggregate source data. Do not recommend tests, models, analytical methods, or visualizations. Do not make causal conclusions, infer study design or independence, invent metadata, estimate calculable values, call values outliers without rules, silently normalize identifiers, use approximate category counts or exact ranges, or present cleaning decisions as final.
