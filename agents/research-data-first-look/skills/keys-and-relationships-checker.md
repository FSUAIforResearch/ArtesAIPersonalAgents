---
name: keys-and-relationships-checker
description: Audits primary and composite keys, distinguishes exact duplicate rows from conflicting repeated keys and repeated measures, and verifies cross-sheet parent-child joins. Use for /check-keys or relational integrity and duplicate checks.
---

# Keys, Duplicates, & Cross-Sheet Relationships Checker (`/check-keys`)

## When to Apply This Skill
Activate this workflow whenever the user types `/check-keys`, attaches this skill for a full dataset profile, or asks to check primary/composite keys, duplicate records, repeated measures, or cross-sheet table joins.

## Step-by-Step Instructions
1. **Audit Candidate Primary & Composite Keys (`## 6. Identifiers, Keys, and Duplicates`)**:
   - Identify the intended primary key or composite key for each sheet (e.g., `Site_ID`, `Participant_ID`, `Participant_ID + Visit_Number`, `Participant_ID + Visit_Number + Analyte`).
   - Output a summary table with these exact columns:
     `Candidate key | Rows | Unique keys | Repeated groups | Extra rows | Assessment`
   - **Use Strict Duplicate Terminology**:
     - **Exact duplicate row**: Every stored field across the compared rows is 100% identical. Identify the affected key(s) and extra row count.
     - **Conflicting repeated key**: The candidate primary/composite key repeats, but one or more non-key fields differ. Never call conflicting records "exact duplicates."
     - **Legitimate repeated-measures records**: Never label longitudinal visits or multiple analytes as duplicate rows merely because `Participant_ID` repeats.
2. **Verify Cross-Sheet Relationships & Join Safety (`## 7. Cross-Sheet Relationships`)**:
   - Check every child-to-parent link across the workbook (`Child -> parent | Linking fields | Observed matches | Unmatched | Relationship assessment`).
   - Do **not** silently trim whitespace, change capitalization, or normalize identifiers before comparing keys across sheets (for example, preserve `"P010 "` with a trailing space and report that it matches other child rows with `"P010 "` but fails to match `"P010"` in the parent table as stored).
   - Flag orphan child keys (identifiers present in a child sheet but absent from the parent sheet, such as `ST99` or `P999`) and flag when duplicated parent keys (such as a duplicated `Participant_ID` or `Visit_Records` key) make a many-to-one join ambiguous.
