# Research Data First Look

> **One-Sentence Summary**: Inspects uploaded CSV files and multi-sheet Excel research workbooks before analysis to produce an exact, non-destructive audit of sheet structure, variables, missingness, primary/composite keys, cross-sheet joins, data-dictionary compliance, and analysis readiness.

[**⬅ Back to Main Catalog**](../README.md)

---

## Overview

Before running statistical models or merging multi-table datasets, researchers need to know what is actually inside their files: whether primary and composite keys are unique, whether trailing spaces or orphan IDs will silently drop rows during joins, and whether stored values violate codebook ranges, units, or chronology rules.

**Research Data First Look** inspects your complete CSV or Excel workbook without altering, trimming, recoding, or imputing a single value. It reconciles exact counts across every sheet, separates true blanks from mixed-type text strings (like `"N/A"` or `"below detection"`), distinguishes exact duplicate rows from conflicting repeated keys, and produces a clear **Readiness Assessment** and list of **Questions Before Analysis**.

- **Recommended Model in ArtesAI**: `OpenAI (gpt-5.6-luna)` (Default, Reasoning Effort: `High`) or `Anthropic (claude-sonnet-5)` (Creativity: `Low`)
- **Estimated Setup Time**: ~5 minutes

---

## How to Build This Agent & Its Skills in ArtesAI

In ArtesAI, **create the companion Skills first** under your account **Settings → My Skills** (Part 1). That way, when you build the **Personal Agent** (Part 2), you can immediately attach and test the skills inside the right-hand **Preview** pane before clicking **Create** (Part 3).

### Part 1: Create the Companion Skills First (`Settings → My Skills`)

1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and click **Settings**.
2. Click **My Skills** on the left, then click **`+ New Skill`** in the top-right corner.
3. Open each standard skill file below and copy its parts into the **Create Skill** modal (**Name** = `name:` from the top `---` block, **Description** = `description:` from the top `---` block, leave **Always On** unchecked/`Ad Hoc`, and paste only the Markdown body below the second `---` into the dark editor box):
   - **[`variable-and-missingness-profiler`](./skills/variable-and-missingness-profiler.md)** (`/profile-variables`): Profiles every variable across every sheet (exact stored types, nonmissing/missing counts, reconciled category counts, exact numeric/date ranges) and separates true blanks from mixed-type text entries.
   - **[`keys-and-relationships-checker`](./skills/keys-and-relationships-checker.md)** (`/check-keys`): Audits primary and composite keys, separates exact duplicate rows from conflicting repeated keys and repeated measures, and checks every child-to-parent cross-sheet join.
   - **[`rules-and-readiness-auditor`](./skills/rules-and-readiness-auditor.md)** (`/audit-readiness`): Tests stored records against data-dictionary/codebook rules (ranges, categories, units, chronology, conditional missingness), prioritizes blocking issues, and delivers a **Readiness Assessment** and **Questions Before Analysis**.

---

### Part 2: Create the Personal Agent

#### 0. Launch "Quick Create"
1. In the left maroon FSU sidebar, click **Explore Agents** (or switch to the **Agents** tab).
2. Under **My Agents** (*Agents created by me*), click the **`+ Create`** button next to the **My Agents** heading (or click the dashed **`+ Create`** card).
3. In the **Quick Create** popup box, enter **`Research Data First Look`** as the **Agent Name** and click **`Let's go`**.

#### 1. Instructions (System Prompt)
1. Open [`system-prompt.md`](./system-prompt.md), copy the text, and paste it into the **Specific Instructions** field.
2. **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** to save on context tokens.

#### 2. Name & Identity
In the **Name & Identity** panel, fill in the three fields below (you'll see them update live in the right-hand **Preview** pane):

- **Name**:
  ```text
  Research Data First Look
  ```
- **Short Description**:
  ```text
  Inspects CSV or Excel research workbooks before analysis to audit variables, missingness, keys, cross-sheet joins, codebook rules, and readiness.
  ```
- **Welcome Message** *(replace the default "Welcome to the Chat!" text in the rich-text editor box)*:
  ```text
  Welcome to Research Data First Look!

  Upload a CSV file or multi-sheet Excel workbook (plus a data dictionary or codebook if separate), and I will inspect its structure, variables, keys, relationships, and data-quality issues without modifying your source data.

  How to Attach Companion Skills (Click "+" in the chat bar -> "Skills >"):
  • variable-and-missingness-profiler (/profile-variables) — Profile all variables, ranges, category counts, and blank vs. mixed-type entries
  • keys-and-relationships-checker (/check-keys) — Check primary/composite keys, duplicates vs. conflicting keys, and cross-sheet joins
  • rules-and-readiness-auditor (/audit-readiness) — Audit against data-dictionary rules and generate a Readiness Assessment & Questions Before Analysis
  ```

#### 3. Knowledge & Tools *(Optional)*
If your lab uses a standard codebook, data dictionary, or variable-naming convention across multiple datasets, you can upload it here so the agent checks every uploaded dataset against your lab's rules automatically.

#### 4. Capabilities & Model
In the **Capabilities & Model** tab, configure the toggles and model as follows:

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | **OFF** | Not needed for tabular dataset profiling and quality audits. |
| **Add Files & Images** | **ON** | Required so users can upload `.xlsx` workbooks, `.csv` files, and data dictionaries into the chat. |
| **Web Search** | **OFF** | Keeps the profile 100% grounded in the uploaded dataset and data dictionary. |
| **Generate Artifacts** | **ON** | Renders multi-sheet variable maps, key tables, and rule-violation tables in a clean side-by-side panel. |
| **Model (`Change` button)** | • **OpenAI**: `gpt-5.6-luna` *(Default, `128,000` max tokens, set **Reasoning Effort**: `High`)*<br>• **Anthropic**: `claude-sonnet-5` *(set **Creativity**: `Low`)* | High reasoning effort and low creativity ensure exact row/category counts and strict reconciliation across multi-sheet workbooks. |

#### 5. Starter Prompts *(Optional)*
In **5. Starter Prompts**, click **Add Starter Prompt** and enter the **Title** and **Prompt** fields below, then click **Create**:

| Title | Prompt |
| :--- | :--- |
| `Full Workbook Profile & Readiness` | `Profile this workbook using /profile-variables, /check-keys, and /audit-readiness, and tell me whether it is ready for analysis.` |
| `Profile Variables & Missingness (/profile-variables)` | `Run /profile-variables on my uploaded dataset to inventory every sheet, variable type, exact range/category count, and missing or mixed-type value.` |
| `Check Keys, Duplicates & Joins (/check-keys)` | `Run /check-keys to check primary and composite keys, distinguish exact duplicates from conflicting repeated keys, and test cross-sheet joins.` |
| `Validate Against Data Dictionary (/audit-readiness)` | `Run /audit-readiness to check all stored records against the data dictionary and list what must be resolved before analysis.` |

---

### Part 3: Test with Skills in the Preview Pane & Click Create
1. In the **Preview** chat pane, click the **`+` button** in the message bar → hover over **`Skills >`** → attach `variable-and-missingness-profiler`, `keys-and-relationships-checker`, and `rules-and-readiness-auditor`.
2. Download and attach [`Research Data First Look - Showcase Study.xlsx`](./Research%20Data%20First%20Look%20-%20Showcase%20Study.xlsx) to the chat, paste the prompt from [`example-input.md`](./example-input.md), and compare the result with [`example-output.md`](./example-output.md).
3. Click **Create** at the bottom of the screen to save your **Research Data First Look** agent!

---

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Core non-destructive profiling guardrails and default workbook inventory workflow |
| [`skills/variable-and-missingness-profiler.md`](./skills/variable-and-missingness-profiler.md) | Skill (`/profile-variables`) for variable maps, reconciled category counts, and blank vs. mixed-type audits |
| [`skills/keys-and-relationships-checker.md`](./skills/keys-and-relationships-checker.md) | Skill (`/check-keys`) for primary/composite key checks, exact vs. conflicting duplicates, and cross-sheet joins |
| [`skills/rules-and-readiness-auditor.md`](./skills/rules-and-readiness-auditor.md) | Skill (`/audit-readiness`) for data-dictionary rule checks, priority issues, readiness verdict, and researcher questions |
| [`Research Data First Look - Showcase Study.xlsx`](./Research%20Data%20First%20Look%20-%20Showcase%20Study.xlsx) | Multi-sheet showcase Excel workbook (`Study_Overview`, `Sites`, `Participants`, `Visit_Records`, `Lab_Results`, `Data_Dictionary`) |
| [`example-input.md`](./example-input.md) | Sample prompt to test the agent on the showcase workbook |
| [`example-output.md`](./example-output.md) | Complete 11-section profile output for the showcase workbook |

---

## Modify & Play: Ideas to Try

1. **Test with a Standalone CSV (No Data Dictionary)**:
   - *Try this*: Upload a single raw `.csv` file without a codebook. Watch how the agent profiles observed types, ranges, and candidate keys while labeling undocumented units and validity rules as *inferred* or *requiring confirmation* rather than inventing rules.
2. **Add a Data-Cleaning Code Generator Skill (`/cleaning-script`)**:
   - *Try this*: Once you answer the **Questions Before Analysis** from `/audit-readiness`, create a fourth skill that generates a reproducible R (`tidyverse`) or Python (`pandas`) cleaning script that logs before-and-after row counts without overwriting the raw file.
3. **Upload Your Lab's Standard Codebook to Knowledge**:
   - *Try this*: Upload your project's master data dictionary PDF or Markdown table into **Step 3 (Knowledge & Tools)** so every weekly data export you drop into chat is automatically audited against the same variable definitions.
