# Research Data Wrangler Agent

> **One-Sentence Summary**: Turns spreadsheet headers, a few sample rows, or data-cleaning decisions into reproducible **Python (`pandas`) or R (`tidyverse`) cleaning scripts** and **FAIR-compliant Data Dictionaries (codebooks)** ready for OSF, Zenodo, Dryad, or FSU DigiNole.

[**⬅ Back to Main Catalog**](../README.md)

---

## Overview

Once you know what is messy in a dataset—mixed date formats, embedded unit strings (`"29.1 C"`), sentinel missing values (`-999`, `"missing"`), or duplicate rows—manually editing cells in Excel is error-prone and impossible to reproduce.

The **Research Data Wrangler** is a **code and documentation generator** that writes defensive **Python (`pandas`)** or **R (`tidyverse`)** cleaning pipelines (`/clean-script`) and repository-ready **FAIR Data Dictionaries** (`/codebook`). You do not even need to upload your full or sensitive dataset—just paste your column headers and 3–6 sample or synthetic rows, and the agent generates the script and codebook for you.

> **How does this differ from [`Research Data First Look`](../research-data-first-look/README.md)?**
> - **Use [`Research Data First Look`](../research-data-first-look/README.md) (Step 1 — Diagnose & Audit a Full Workbook)**: Upload a **complete** CSV or multi-sheet Excel workbook when you want an exact, row-by-row diagnostic profile of sheet structure, primary/composite keys, cross-sheet joins, and existing codebook violations before deciding how to clean.
> - **Use `Research Data Wrangler` (Step 2 — Generate Cleaning Code & Build a New Codebook)**: Paste just **column headers + 3–6 sample rows** when you want executable **Python (`pandas`) or R (`tidyverse`) cleaning code** (`/clean-script`) that transforms `data_raw/` → `data_clean/` with audit logging, or when you need to **author a new FAIR Data Dictionary (`README_DATA.md`)** (`/codebook`) from scratch.

- **Recommended Model in ArtesAI**: `Anthropic (claude-sonnet-5)` (Creativity: `Low`) or `OpenAI (gpt-5.6-luna)` (Default, Reasoning Effort: `Medium`)
- **Estimated Setup Time**: ~5 minutes

---

## How to Build This Agent & Its Skills in ArtesAI

In ArtesAI, **create the companion Skills first** under your account **Settings → My Skills** (Part 1). That way, while you are building the **Personal Agent** (Part 2), you can immediately attach and test the skills inside the right-hand **Preview** chat pane before clicking **Create** (Part 3).

### Part 1: Create the Companion Skills First (`Settings → My Skills`)

1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and click **Settings**.
2. Click **My Skills** on the left, then click **`+ New Skill`** in the top-right corner.
3. Open each standard skill file below and copy its parts into the **Create Skill** modal (**Name** = `name:` from the top `---` block, **Description** = `description:` from the top `---` block, leave **Always On** unchecked/`Ad Hoc`, and paste the Markdown body below `---` into the dark editor box):
   - **[`data-dictionary-codebook-builder`](./skills/data-dictionary-builder.md)** (`/codebook`): Generates a standardized README codebook table (`Variable`, `Type`, `Units`, `Valid Range`, `Missing Value Code`, `Description`) ready for OSF, Zenodo, Dryad, or FSU's DigiNole repository.
   - **[`reproducible-cleaning-script-generator`](./skills/cleaning-pipeline-generator.md)** (`/clean-script`): Produces a step-by-step, commented `Python (pandas)` or `R (tidyverse)` script that loads raw data read-only, logs every dropped or modified value, runs validation assertions, and exports a clean analysis file.

---

### Part 2: Create the Personal Agent

#### 0. Launch "Quick Create"
1. In the left maroon FSU sidebar, click **Explore Agents** (or switch to the **Agents** tab).
2. Under **My Agents** (*Agents created by me*), click the **`+ Create`** button next to the **My Agents** heading (or click the dashed **`+ Create`** card).
3. In the **Quick Create** popup box, enter **`Research Data Wrangler`** as the **Agent Name** and click **`Let's go`**.

#### 1. Instructions (System Prompt)
1. Open [`system-prompt.md`](./system-prompt.md), copy the text, and paste it into the **Specific Instructions** field.
2. **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** to save on context tokens.

#### 2. Name & Identity
In the **Name & Identity** panel, copy and paste the fields below (you'll see them update live in the right-hand **Preview** pane):

- **Name**:
  ```text
  Research Data Wrangler
  ```
- **Short Description**:
  ```text
  Generates reproducible Python (pandas) or R (tidyverse) data-cleaning scripts and FAIR repository codebooks from column headers and sample rows.
  ```
- **Welcome Message** *(replace the default "Welcome to the Chat!" text in the rich-text editor box)*:
  ```text
  Welcome to the Research Data Wrangler!

  Paste your column headers and 3–6 sample rows from a CSV or spreadsheet (remove any sensitive human-subjects PII first), and I will generate a reproducible Python (pandas) or R (tidyverse) cleaning pipeline and a FAIR Data Dictionary without touching your raw files.

  How to Attach Companion Skills (Click "+" in the chat bar -> "Skills >"):
  • reproducible-cleaning-script-generator (/clean-script) — Generate a defensive, logged Python (pandas) or R (tidyverse) cleaning script
  • data-dictionary-codebook-builder (/codebook) — Build a FAIR-compliant Data Dictionary & Codebook ready for OSF, Zenodo, Dryad, or FSU DigiNole
  ```

#### 3. Knowledge & Tools *(Optional)*
You can upload your lab's naming convention guide or metadata standard (e.g., Darwin Core, BIDS, or CF metadata conventions) here so generated codebooks automatically follow your discipline's standards.

#### 4. Capabilities & Model
In the **Capabilities & Model** tab, configure the toggles and model as follows:

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | **OFF** | Not needed for data cleaning scripts and metadata tables. |
| **Add Files & Images** | **ON** | Lets you attach a sample `.csv`, `.tsv`, or `.xlsx` file directly inside a chat session. |
| **Web Search** | **OFF** | Keeps the agent focused strictly on your dataset schema and standard `pandas` / `tidyverse` syntax. |
| **Generate Artifacts** | **ON** | **Essential for this agent**—places your generated Python/R cleaning script and Markdown codebook in a dedicated artifact box with one-click copy/download. |
| **Model (`Change` button)** | • **Anthropic**: `claude-sonnet-5` *(set **Creativity**: `Low`)*<br>• **OpenAI**: `gpt-5.6-luna` *(Default, set **Reasoning Effort**: `Medium`)* | Setting **Creativity** to `Low` (for Anthropic) keeps `pandas` and `tidyverse` code deterministic and bug-free. |

#### 5. Starter Prompts *(Optional)*
In **5. Starter Prompts**, click **Add Starter Prompt** and enter the **Title** and **Prompt** fields below, then click **Create**:

| Title | Prompt |
| :--- | :--- |
| `Audit CSV + Python Cleaning & Codebook` | `Audit the CSV sample I paste next, run /clean-script in Python (pandas), and build a /codebook data dictionary.` |
| `R Tidyverse Cleaning Script (/clean-script)` | `Audit my sample rows and generate a reproducible R tidyverse /clean-script that logs every row modification.` |
| `Build FAIR Data Dictionary (/codebook)` | `Run /codebook on my dataset headers and sample rows to generate a repository-ready Markdown Data Dictionary.` |

---

### Part 3: Test with Skills in the Preview Pane & Click Create
1. In the **Preview** chat pane on the right side of the Agent Builder (or after clicking **Create**), click the **`+` button** on the left side of the message input bar (`+ Type a message...`) → hover over **`Skills >`** → click `data-dictionary-codebook-builder` and `reproducible-cleaning-script-generator` to attach them.
2. Open [`example-input.md`](./example-input.md), copy the sample messy water-quality CSV snippet, paste it into the chat, and compare your output with [`example-output.md`](./example-output.md).
3. Click **Create** at the bottom of the screen to save your **Research Data Wrangler** agent!

---

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Core data-stewardship persona and non-destructive data cleaning rules |
| [`skills/data-dictionary-builder.md`](./skills/data-dictionary-builder.md) | Skill for building FAIR-compliant data dictionaries and codebooks |
| [`skills/cleaning-pipeline-generator.md`](./skills/cleaning-pipeline-generator.md) | Skill for writing defensive Python/R cleaning pipelines with audit logs |
| [`example-input.md`](./example-input.md) | Sample prompt with a messy 6-row environmental sensor CSV snippet |
| [`example-output.md`](./example-output.md) | Sample data quality audit + `pandas` cleaning script + FAIR codebook |

---

## Modify & Play: Ideas to Try

Once you have the baseline agent running, try customizing it for your lab's software stack:

1. **Switch the Default Language to Python (`pandas`)**:
   - *Try this*: In [`skills/cleaning-pipeline-generator.md`](./skills/cleaning-pipeline-generator.md), change the default language from **R (`tidyverse` + `janitor`)** to **Python 3 (`pandas` + `numpy`)** if your lab works primarily in Python/Jupyter.
2. **Add a Qualtrics / REDCap Survey Export Skill**:
   - *Try this*: Create a skill called `/survey-clean` specifically designed to strip Qualtrics' 3-row metadata headers, recode Likert scales (`"Strongly Disagree"` → `1`), and score reverse-coded survey items.
3. **Privacy-First Schema Mode**:
   - *Try this*: If you work with sensitive human-subjects data (IRB/HIPAA), add a rule to `system-prompt.md` instructing the agent to refuse raw PII and instead ask you to paste only column names and data types (`df.dtypes`).

