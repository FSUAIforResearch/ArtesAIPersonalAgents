---
name: data-profile
description: Inspect and describe a CSV or Excel research dataset before analysis. Use to inventory tables and variables, calculate missingness, identify keys and duplicates, evaluate repeated-measures and hierarchical structures, check cross-sheet relationships, apply data-dictionary rules, and assess readiness without modifying the source data.
---

# Data Profile

## Goal

Create a complete, exact, and evidence-based profile of a research dataset that can be used before analysis without guessing or silently changing the data.

## Required inputs

- A readable CSV file, Excel workbook, or schema
- Optional data dictionary, codebook, or notes
- Optional research question

If the dataset cannot be read completely enough to support the requested assessment, stop and state what is unavailable.

## Procedure

1. Inventory every accessible worksheet, table, row, column, and variable.
2. Report exact data-row and variable counts for each table.
3. Identify source-data, metadata, dictionary, notes, and summary sheets.
4. Classify each table’s structure and unit of observation.
5. Profile every variable using its exact stored name.
6. Calculate nonmissing count, missing count, missing percentage, unique count, range, or exact category frequencies as applicable.
7. Distinguish numeric values, text, dates, timestamps, formulas, blanks, and mixed stored types.
8. Identify candidate primary and composite keys and test their uniqueness.
9. Separately quantify exact duplicate rows, repeated identifiers, repeated composite keys, and conflicting repeated keys.
10. Detect repeated measures, longitudinal order, clustering, pairing, nesting, folds, replications, and hierarchical dependencies.
11. Identify and test cross-sheet relationships and foreign keys.
12. Count matched and unmatched records for each relationship.
13. Apply documented types, categories, units, ranges, missingness rules, keys, and relationship requirements.
14. Flag malformed types, invalid dates, range violations, inconsistent categories, inconsistent units, whitespace issues, conditional missingness problems, orphan records, high cardinality, imbalance, and unsupported structures.
15. Reconcile all reported counts and denominators.
16. Separate verified observations, documented rules, inferred roles, and unresolved questions.
17. Assess readiness without altering the source data.

## Duplicate terminology

Use these definitions consistently:

- **Exact duplicate row:** all compared fields are identical.
- **Repeated identifier:** an identifier occurs more than once.
- **Repeated composite key:** the same key combination occurs more than once.
- **Conflicting repeated key:** repeated keys contain different non-key values.
- **Legitimate repeated measure:** an identifier repeats because observations occur at different documented occasions, conditions, or levels.

Report both:

- the number of affected key groups; and
- the number of extra rows beyond the first occurrence.

## Relationship terminology

Classify relationships only after checking multiplicity on both sides:

- one-to-one;
- one-to-many;
- many-to-one;
- many-to-many;
- unresolved because a proposed parent key is not unique; or
- unsupported by available evidence.

Report the exact linking fields and unmatched-row counts.

## Evidence rules

Label information as:

- **Observed:** directly calculated or read from the dataset.
- **Documented:** explicitly stated in a dictionary or notes.
- **Inferred:** a plausible role or interpretation not explicitly documented.
- **Unresolved:** insufficient evidence is available.

Do not convert an inference into a fact.

## Output contract

Return:

- dataset_status
- workbook_inventory
- dimensions
- table_grains
- structure
- variable_profiles
- missingness_summary
- identifiers_and_keys
- duplicate_assessment
- relationships_and_dependencies
- referential_integrity
- dictionary_rule_checks
- existing_transformations
- quality_flags
- priority_issues
- unsupported_features
- verified_facts
- documented_rules
- inferred_roles
- readiness_assessment
- clarification_questions

## Validation

Before responding, verify that:

- every relevant sheet and variable is covered;
- exact names and units are preserved;
- missing counts reconcile with total row counts;
- category counts reconcile with nonmissing counts;
- duplicate terminology matches the evidence;
- key-group counts and extra-row counts are distinguished;
- relationship classifications match observed multiplicities;
- unmatched-record counts are exact;
- documented rules are separated from inferred expectations;
- no unsupported cause or scientific conclusion is stated; and
- no source data were modified.

## Prohibited actions

Do not:

- modify, delete, recode, standardize, impute, filter, or aggregate source data;
- silently trim identifiers or normalize categories;
- recommend statistical tests, models, or visualizations;
- make causal or scientific conclusions;
- conceal uncertainty;
- estimate values that can be calculated; or
- claim complete coverage when only a preview or sample was inspected.