---
name: rules-and-readiness-auditor
description: Checks stored data against data-dictionary validation rules (ranges, categories, units, chronology, conditional blanks), prioritizes blocking issues, and produces a Readiness Assessment and Questions Before Analysis. Use for /audit-readiness.
---

# Data-Dictionary Rules & Readiness Auditor (`/audit-readiness`)

## When to Apply This Skill
Activate this workflow whenever the user types `/audit-readiness`, attaches this skill for a full dataset profile, or asks to validate a dataset against a data dictionary/codebook and determine whether it is ready for analysis.

## Step-by-Step Instructions
1. **Run Record-by-Record Data-Dictionary Rule Checks (`## 8. Data-Dictionary Rule Checks`)**:
   - When a data dictionary, codebook, or validation sheet is present, test every documented rule against the stored records: allowed numeric/date ranges, permitted category labels (case-sensitive), required units by analyte/measure, date chronology (e.g., later visits not preceding earlier visits; lab result dates on or after visit dates), conditional completeness rules, and key/referential rules.
   - Present a table of all observed violations:
     `Sheet and field | Affected rows | Evidence` (naming the specific record key and exact stored value for each violation).
   - Explicitly note when missing values are permitted by the dictionary so allowed blanks are not misclassified as errors.
2. **Categorize Priority Issues (`## 9. Priority Issues`)**:
   - Group findings into three clear subsections:
     - `### Must be resolved before analysis`: Blocking issues such as duplicate parent/composite keys, unmatched/whitespace-mismatched foreign keys, malformed dates, out-of-range values, unit mismatches, and chronology errors.
     - `### May be acceptable only if documented`: Permitted missing values, censored text entries (e.g., `"below detection"`), or severe group imbalances that require analytical documentation.
     - `### Unsupported or unresolved`: Decisions that cannot be made from the file alone without researcher confirmation.
3. **Deliver the Final Readiness Verdict (`## 10. Readiness Assessment`)**:
   - Assign one status (`Ready for analysis`, `Usable with documented limitations`, `Not ready for analysis`, or `Unable to assess`) and explain why using only observed and documented evidence. Remind the user that any subsequent data cleaning should preserve the raw file and log all approved row/value changes.
4. **List Researcher Decision Questions (`## 11. Questions Before Analysis`)**:
   - Provide a numbered list of specific, actionable questions the researcher must answer to authorize data cleaning (covering duplicate removal vs. retention, conflicting key reconciliation, whitespace trimming, category aliases, text-in-numeric fields, unit conversions, malformed dates, and orphan IDs).
