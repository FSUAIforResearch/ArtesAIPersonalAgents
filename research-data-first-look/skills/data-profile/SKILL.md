---
name: data-profile
description: Inspect and explain CSV or Excel research data before analysis, including variables, missingness, identifiers, repeated records, linked sheets, formulas, and documented quality rules.
---

# Data Profile

## Purpose

Inspect a readable dataset before analysis and produce a factual, plain-language description of its contents, structure, relationships, and readiness.

Use this skill when the user asks to:

- profile, inspect, understand, or describe a dataset;
- review a CSV or Excel workbook before analysis;
- explain variables, sheets, tables, records, or data structure;
- identify missing values or possible data-quality issues;
- check repeated identifiers or repeated measurements;
- identify exact duplicate records;
- evaluate relationships between workbook sheets;
- compare stored data with a supplied data dictionary;
- verify formula-derived workbook summaries; or
- determine what must be resolved before later work.

Do not use this skill to:

- clean or modify data;
- recommend a statistical test or model;
- select a visualization;
- perform scientific interpretation; or
- make causal conclusions.

## Required inputs

Use at least one of:

- a readable CSV file;
- a readable Excel workbook;
- a pasted table;
- a variable list or schema;
- a data dictionary;
- documented validation rules; or
- a sufficiently detailed description of a dataset.

If record-level data are unavailable, profile only what can be verified from the supplied schema or documentation.

Do not invent:

- observations;
- categories;
- ranges;
- counts;
- units;
- missingness;
- identifiers;
- relationships;
- validation rules; or
- research context.

## Evidence classifications

Classify material findings using the following terms.

### Verified finding

Directly observed or calculated from the supplied data.

### Metadata-supported finding

Established by a supplied data dictionary or other documentation.

### Inferred interpretation

A reasonable interpretation of names, patterns, formulas, or workbook structure that is not explicitly documented.

### Requires confirmation

Cannot be resolved from the available data or metadata.

Do not present an inferred interpretation as a verified or metadata-supported finding.

## Evidence priority

When evidence conflicts, use the following order:

1. Directly observed stored data establish what is actually present.
2. Supplied metadata establish intended meaning, validation rules, permitted values, expected formats, units, and allowed missingness.
3. Workbook formulas, labels, and sheet structure provide supporting structural evidence.
4. Names and patterns may support cautious inference.

Report conflicts explicitly.

Do not silently change observed data to match documentation.

Do not ignore a documented rule because the stored data violate it.

## Procedure

### 1. Confirm readability and scope

Determine what can be read.

Report:

- file or dataset type;
- number of readable sheets or tables;
- exact sheet or table names;
- inaccessible or unsupported components;
- whether formulas can be identified;
- whether a data dictionary or other metadata are present; and
- whether the complete relevant dataset was inspected.

If the complete relevant data cannot be read, state the limitation before reporting any finding that depends on complete coverage.

Do not imply that a displayed sample represents the complete dataset unless that has been verified.

### 2. Inventory every relevant sheet or table

For each sheet or table, report:

- exact name;
- exact dimensions;
- number of observation rows;
- number of variables;
- apparent purpose;
- apparent row grain;
- apparent structural type; and
- whether it appears to contain data, metadata, calculations, instructions, or output.

Row grain means what one row appears to represent.

Possible structural types include:

- cross-sectional;
- repeated measures;
- longitudinal;
- time series;
- hierarchical;
- network or relational;
- wide;
- long;
- matrix;
- model output;
- metadata;
- mixed; or
- unclear.

Distinguish observation rows from:

- column headers;
- title rows;
- notes;
- instructions;
- subtotals;
- blank rows; and
- formatting-only rows.

Describe purpose and grain as inferred unless documentation confirms them.

Do not infer that rows represent people, students, patients, sites, experiments, or another real-world entity unless the data or metadata support that interpretation.

### 3. Inspect formulas and workbook summaries

Identify formula-derived totals, counts, dates, calculated fields, and summaries when formulas can be read.

For each important formula-derived value:

- identify it as formula-derived;
- explain what it appears to calculate;
- compare its result with the underlying data when possible;
- report whether it agrees with the underlying records; and
- flag formula errors or unexplained disagreements.

Do not describe formula-derived values as manually entered or self-reported unless the workbook establishes that fact.

Do not infer that a displayed result is a formula if the formula itself cannot be verified.

### 4. Profile every variable

Use each variable’s exact stored name.

For every relevant variable, report:

- sheet or table;
- exact variable name;
- stored data type;
- likely semantic type;
- likely role;
- documented units;
- exact observed minimum and maximum or exact stored categories;
- exact category counts when categories are displayed;
- distinct-value count when useful;
- missing-value count;
- missing-value percentage;
- applicable metadata rule;
- evidence classification; and
- status or concern.

Possible roles include:

- identifier;
- foreign key;
- outcome;
- predictor;
- grouping variable;
- time variable;
- spatial variable;
- uncertainty variable;
- measurement;
- unit field;
- administrative field;
- calculated field;
- free text; or
- unclear.

The stored data type describes how values are represented in the file.

The semantic type describes what the values appear to mean.

For example, a date stored as text must be reported as a text field with a likely date role. Do not claim that it was successfully parsed unless that can be verified.

Preserve stored labels exactly.

Do not silently merge similar labels into one category.

### 5. Calculate missingness

For each variable:

1. identify the applicable observation population;
2. count missing cells across all applicable observation rows;
3. divide the missing count by the applicable observation count;
4. report the count, denominator, and percentage.

Use:

`missing percentage = missing count / applicable observation count × 100`

Recalculate the result before reporting it.

Distinguish blank cells from stored labels that may represent missingness, including:

- `NA`;
- `N/A`;
- `Unknown`;
- `Not recorded`;
- `offline`;
- `-999`; and
- other documented missing-value codes.

Do not automatically convert stored labels to missing values.

A nonnumeric text value in a numeric field is a type inconsistency, not a blank missing value, unless metadata explicitly define that text as a missing-value code.

If metadata permit a field to be missing, describe the observation as permitted missingness rather than a confirmed error.

For conditional missingness rules, verify the condition for every missing value.

For example, when missingness is allowed only if a status equals `Review`, verify the associated status before classifying the blank as permitted.

Do not call missingness expected, optional, or by design unless metadata establish that fact.

### 6. Count and reconcile categories

For every categorical variable:

1. identify every distinct stored label;
2. calculate the exact frequency of each label;
3. calculate the number of nonmissing applicable records;
4. sum the category frequencies;
5. verify that the frequency total equals the nonmissing population;
6. recalculate any frequencies that do not reconcile.

Do not use approximate category counts when complete data are readable.

Do not use `≈`, approximately, about, or roughly for a count that can be calculated exactly.

If only selected categories are displayed:

- label the list as a partial preview;
- report the exact number of distinct stored labels; and
- state that the displayed categories do not form a complete list.

Before finalizing, check every parenthetical category count against the stored records.

Do not report a category-frequency list whose counts fail to reconcile.

### 7. Report exact observed ranges

For every numeric field with a complete readable population:

- calculate the exact numeric minimum;
- calculate the exact numeric maximum;
- report them as the observed range;
- keep the observed range separate from the documented valid range.

Do not describe a calculated observed range as rough or approximate.

When a numeric field also contains text or blanks, report separately:

- exact numeric minimum and maximum;
- the exact nonnumeric stored values and affected records;
- the missing count; and
- the applicable metadata rule.

A value may be part of the exact observed range without being documented as valid.

Do not declare a numeric value invalid when no validation rule or valid scale was supplied.

### 8. Assess identifiers and candidate keys

Identify likely identifiers and candidate keys.

For each candidate key, check:

- whether values are unique;
- whether values are missing;
- whether values follow a documented format;
- whether exact duplicate rows exist;
- whether repeated key values exist;
- whether another variable creates a valid composite key; and
- whether repeated values form an intentional sequence.

A repeated identifier is not automatically a duplicate record.

For repeated-measures data, evaluate candidate composite keys such as:

`Participant_ID + Visit`

`Student_ID + Week`

or:

`Sensor_ID + Timestamp`

Report separately:

- exact duplicate rows;
- repeated candidate keys;
- repeated composite keys with identical records;
- repeated composite keys with conflicting records;
- intentional repeated observations; and
- unresolved repeated records.

A gap in an identifier sequence is not proof that a record is missing unless documentation establishes that identifiers must be consecutive.

### 9. Verify exact duplicate records

Compare every stored field when determining whether records are identical.

When every stored field matches, report:

`Verified exact duplicate records in the supplied data`

Identify the records using the most meaningful key available.

Do not use likely duplicate, possible duplicate, or apparent duplicate when exact equality has been verified.

Verifying an exact duplicate does not authorize deleting it.

Record deletion remains a proposed cleaning action requiring user confirmation.

When a key repeats but another field differs, report:

`Repeated key with conflicting stored values`

Identify which fields differ.

Do not call conflicting records identical.

### 10. Assess repeated and dependent observations

Look for:

- repeated measurements;
- paired measurements;
- multiple observations per identifier;
- clustering by site, class, household, laboratory, or another group;
- nesting;
- longitudinal sequences;
- multiple raters;
- multiple outcomes per observation; and
- wide-to-long relationships.

Report the observed structure without claiming that observations are statistically independent or dependent unless the design is documented.

When describing balance, distinguish:

- balance among identifiers stored in the repeated-record table; and
- complete coverage of the population represented in a parent table.

Do not infer an intervention or treatment effect from observed change over time.

### 11. Describe repeated-measures coverage precisely

Distinguish:

- identifiers with the expected number of repeated records;
- identifiers with the expected sequence plus extra records;
- identifiers with incomplete sequences;
- identifiers with malformed sequence fields; and
- child identifiers absent from the documented parent table.

An identifier with an extra exact duplicate or conflicting record still has a repeated-measures structure.

Do not exclude it from the repeated-measures population solely because it has more records than expected.

When the expected record count or sequence is inferred rather than documented, label it as inferred.

Do not claim that a repeated-record schedule is complete unless metadata establish the expected schedule.

### 12. Assess cross-sheet and hierarchical relationships

For each likely relationship, identify:

- parent sheet;
- child sheet;
- parent key;
- child foreign key;
- likely cardinality;
- whether the relationship is documented or inferred; and
- whether the stored types are compatible.

Possible cardinalities include:

- one-to-one;
- one-to-many;
- many-to-one;
- many-to-many; or
- unresolved.

For multi-level hierarchies, evaluate every level separately.

For example:

- Sites to Sensors; and
- Sensors to Readings.

Compare the complete relevant identifier populations and report:

- identifiers present in both;
- identifiers present only in the parent;
- identifiers present only in the child;
- missing key values;
- duplicate parent keys;
- duplicate child composite keys;
- incompatible stored types; and
- formatting differences that prevent exact matches.

Do not silently standardize:

- leading or trailing whitespace;
- capitalization;
- punctuation;
- leading zeros; or
- numeric and text formats.

If normalized forms might match, report that as a possible explanation requiring confirmation.

### 13. Distinguish coverage gaps from referential-integrity violations

For linked tables, classify findings carefully.

#### Child identifier absent from the parent

Call this a documented referential-integrity violation only when metadata require every child identifier to exist in the parent table.

#### Parent identifier with no child records

Call this a documented violation only when metadata require every parent record to have child records.

Otherwise, report it as:

`Verified parent-table coverage gap requiring clarification`

#### Identifier formatting discrepancy

When a child identifier differs from a parent identifier because of whitespace, capitalization, punctuation, or formatting:

- preserve both exact stored values;
- report that they do not match as stored; and
- state that treating them as equivalent requires confirmation.

Do not silently normalize identifiers before reporting coverage.

### 14. Apply documented validation rules

When metadata are present, check applicable rules for:

- permitted categories;
- numeric limits;
- date limits;
- date ordering;
- required values;
- permitted missingness;
- conditional missingness;
- identifier uniqueness;
- composite-key uniqueness;
- cross-sheet referential integrity;
- cross-variable relationships;
- units; and
- expected formats.

Separate findings into:

- documented violation;
- verified exact duplicate;
- repeated key with conflicting values;
- permitted value or missingness;
- verified coverage gap;
- referential-integrity violation;
- possible inconsistency;
- unusual but not documented as invalid;
- meaning unclear; or
- could not verify.

Do not invent validation rules.

Do not call a value impossible, invalid, or an outlier unless supplied documentation provides a defensible rule.

### 15. Check units and cross-variable rules

When metadata define a relationship between variables, verify the relationship record by record.

Examples include:

- measurement type and unit;
- quality flag and missing reading;
- site assignment and copied site identifier;
- visit number and date order; or
- status and required fields.

Report:

- the affected key;
- the exact stored values;
- the documented relationship rule; and
- whether the relationship conforms.

Do not convert units or recode values unless the user explicitly authorizes a separate cleaning step.

### 16. Check dates, timestamps, and sequences

For date and time variables:

- report exact observed minimum and maximum readable dates;
- identify unreadable or inconsistently stored values;
- identify the affected record using a meaningful key;
- preserve the exact stored malformed value when useful;
- verify chronological ordering when relevant;
- compare repeated-record dates with visit, wave, or sequence labels;
- compare child dates with relevant parent dates when documentation requires it; and
- calculate elapsed time from actual dates before making elapsed-time statements.

Do not assume that labels such as `Week 1`, `Visit 2`, or `Follow-up` represent equal time intervals.

When a chronological violation is verified, identify both dates and the affected key.

Do not include unreadable text values when calculating numeric date minima and maxima.

### 17. Identify transformations and calculated fields

Look for evidence of:

- filtering;
- aggregation;
- recoding;
- binning;
- standardization;
- normalization;
- calculated variables;
- percentages;
- totals;
- scores;
- date-derived variables; and
- workbook formulas.

Report only transformations supported by formulas, documentation, labels, or verifiable relationships.

Do not reverse-engineer an undocumented calculation and present it as certain.

### 18. Check grouping-variable alignment

Compare grouping variables that might represent separate comparison dimensions.

Report when two or more variables are perfectly aligned in the observed data.

For example, if every record in one program belongs to one campus and every record in the other program belongs to another campus, state that the separate relationships of program and campus cannot be distinguished from the supplied data alone.

Do not describe perfectly aligned variables as independent comparison factors.

Do not recommend a statistical method for addressing the alignment.

### 19. Perform an internal consistency review

Before responding, verify that:

- all reported counts use the correct population;
- all percentages use the correct denominator;
- all numeric ranges are exact;
- all reported categories occur in the data;
- all category-frequency totals reconcile;
- all sheet dimensions agree across the response;
- formula-derived totals agree with underlying data when checked;
- duplicate findings use the correct key;
- exact duplicate claims compare every stored field;
- repeated-measures counts correctly distinguish expected sequences from extra records;
- parent-child counts reconcile;
- parent-only records are not called documented violations without a coverage rule;
- child-only records are not called referential violations without a metadata rule;
- permitted missingness is not also called an error;
- conditional missingness rules were evaluated;
- inferred roles are not described as documented facts;
- worksheet row numbers are not substituted for meaningful identifiers;
- the overview and readiness assessment agree with detailed findings; and
- every material issue appears consistently throughout the response.

If a result cannot be verified, report:

`Could not verify`

Do not estimate.

## Required output

Return the following sections.

### A. Quick Overview

Summarize:

- readable inputs;
- sheet or table inventory;
- exact dimensions;
- apparent purpose;
- apparent row grain;
- main structural findings;
- formula-derived summaries;
- available metadata; and
- the most consequential verified issues.

### B. Variable Map

Create a separate table for each data sheet when needed.

Use:

| Sheet | Variable | Stored Type | Likely Role | Units | Observed Values or Range | Missing | Metadata Rule | Status |
|---|---|---|---|---|---|---|---|---|

Preserve exact variable names and stored labels.

When displaying categorical frequencies, use exact reconciled counts.

If there are too many categories to display clearly:

- report the exact category count;
- show only a clearly labeled preview; and
- state that the displayed list is incomplete.

Do not imply that a partial list is complete.

### C. Structure and Dependencies

Explain:

- candidate keys;
- composite keys;
- exact duplicates;
- conflicting repeated keys;
- repeated measurements;
- repeated-measures coverage;
- clustering or nesting;
- hierarchical relationships;
- relationship cardinality;
- cross-sheet coverage;
- identifier-format discrepancies;
- grouping-variable alignment;
- formulas; and
- observed transformations.

### D. Data-Quality Flags

For each flag, state:

- affected sheet;
- affected variable or key;
- affected identifier or composite key;
- exact observed value;
- applicable metadata rule;
- evidence classification;
- why the issue matters; and
- whether confirmation is required.

Distinguish:

- documented violations;
- verified exact duplicates;
- conflicting repeated keys;
- coverage gaps;
- referential-integrity violations;
- possible inconsistencies;
- permitted missingness; and
- unsupported assumptions.

### E. Questions Before Analysis

Ask no more than three questions.

Organize questions by decision type when possible:

1. identifier and relationship resolution;
2. duplicate-key resolution; and
3. nonconforming value, format, type, unit, or missingness resolution.

Ask only questions whose answers would materially affect:

- record inclusion;
- duplicate resolution;
- identifier resolution;
- variable interpretation;
- permitted values;
- units;
- missingness treatment; or
- linkage between tables.

Do not ask questions already answered by the supplied data or metadata.

### F. Readiness Assessment

State:

- what is clearly interpretable;
- what can be safely described, linked, or summarized;
- what must be resolved before later work;
- which issues are blocking;
- which issues are nonblocking;
- which missing values are permitted;
- which fields have restricted usability; and
- which assumptions remain unsupported.

Do not provide a blanket statement that the dataset is ready without specifying what it is ready for.

## Restrictions

- Do not modify the source data.
- Do not silently clean or standardize values.
- Do not delete records.
- Do not recode categories.
- Do not convert units.
- Do not impute missing values.
- Do not filter or aggregate the dataset.
- Do not recommend a statistical test or model.
- Do not recommend a visualization.
- Do not make causal or scientific conclusions.
- Do not infer study design from variable names alone.
- Do not infer respondent uniqueness from row count alone.
- Do not infer observation independence.
- Do not infer that an undocumented field is optional.
- Do not invent units, definitions, categories, or research context.
- Do not estimate a value that can be calculated.
- Do not report an unverified value as factual.
- Do not call a value an outlier without a supplied scale or rule.
- Do not silently normalize identifiers before comparing them.
- Do not describe an exact duplicate as merely likely after exact equality has been verified.
- Do not describe a parent-only identifier as a documented violation unless complete child coverage is required.
- Do not report approximate categorical counts when exact counts are available.
- Do not report an approximate observed range when an exact range is available.
- Do not recommend deleting, recoding, normalizing, converting, or imputing data as a final decision.​