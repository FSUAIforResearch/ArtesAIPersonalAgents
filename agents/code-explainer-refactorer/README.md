# Research Code Explainer & Refactorer Agent

> **One-Sentence Summary**: Decodes undocumented "legacy lab scripts" (Python, R, MATLAB, Bash), flags silent scientific bugs, and prepares laptop scripts to run on HPC clusters like FSU's Research Computing Center (RCC).

[**⬅ Back to Main Catalog**](../../README.md)

---

## Overview

Every research lab has at least one script written three years ago by a graduated student—full of single-letter variables (`x1`, `tmp2`), hardcoded desktop paths (`C:\Users\Dave\Desktop\final_v3.csv`), unseeded random numbers, and zero comments.

The **Research Code Explainer & Refactorer** helps researchers and students understand unfamiliar code in plain English, refactors messy scripts into clean, modular functions without changing their mathematical behavior, and includes a dedicated skill to make laptop code ready for batch execution on **FSU's Research Computing Center (RCC) SLURM cluster**.

- **Recommended Model in ArtesAI**: `OpenAI (gpt-5.6-luna)` (Reasoning Effort: `High`) or `Anthropic (claude-sonnet-5)` / `claude-opus-4-7` (Creativity: `Low`)
- **Estimated Setup Time**: ~5 minutes

---

## How to Build This Agent & Its Skills in ArtesAI

In ArtesAI, **create the companion Skills first** under your account **Settings → My Skills** (Part 1). That way, while you are building the **Personal Agent** (Part 2), you can immediately attach and test the skills inside the right-hand **Preview** chat pane before clicking **Create** (Part 3).

### Part 1: Create the Companion Skills First (`Settings → My Skills`)

1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and click **Settings**.
2. Click **My Skills** on the left, then click **`+ New Skill`** in the top-right corner.
3. Open each standard skill file below and copy its parts into the **Create Skill** modal (**Name** = `name:` from the top `---` block, **Description** = `description:` from the top `---` block, leave **Always On** unchecked/`Ad Hoc`, and paste the Markdown body below `---` into the dark editor box):
   - **[`plain-english-walkthrough-bug-audit`](./skills/line-by-line-walkthrough.md)** (`/walkthrough`): Breaks an unfamiliar script into logical stages, explains the underlying math/algorithm in plain English, and flags "silent scientific bugs" (e.g., data leakage, unseeded RNGs, floating-point traps, or hardcoded paths).
   - **[`hpc-slurm-cluster-readiness`](./skills/hpc-slurm-readiness.md)** (`/hpc-ready`): Converts a slow laptop script with hardcoded paths and GUI plots into a headless command-line script with `argparse`, seed control, and a companion **SLURM `.sh` batch submission script** tailored for FSU RCC.

---

### Part 2: Create the Personal Agent

#### 0. Launch "Quick Create"
1. In the left maroon FSU sidebar, click **Explore Agents** (or switch to the **Agents** tab).
2. Under **My Agents** (*Agents created by me*), click the **`+ Create`** button next to the **My Agents** heading (or click the dashed **`+ Create`** card).
3. In the **Quick Create** popup box, enter **`Research Code Explainer & Refactorer`** as the **Agent Name** and click **`Let's go`**.

#### 1. Instructions (System Prompt)
1. Open [`system-prompt.md`](./system-prompt.md), copy the text, and paste it into the **Specific Instructions** field.
2. **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** to save on context tokens.

#### 2. Name & Identity
In the **Name & Identity** panel, copy and paste the fields below (you'll see them update live in the right-hand **Preview** pane):

- **Name**:
  ```text
  Research Code Explainer & Refactorer
  ```
- **Short Description**:
  ```text
  Explains undocumented research scripts (Python, R, MATLAB, Bash), audits for silent scientific bugs, and prepares code for HPC/SLURM clusters.
  ```
- **Welcome Message** *(replace the default "Welcome to the Chat!" text in the rich-text editor box)*:
  ```text
  Welcome to the Research Code Explainer & Refactorer!

  Paste an unfamiliar or legacy research script (Python, R, MATLAB, Julia, or Bash) below. I will explain what it does, check for silent scientific/numerical bugs, and help you refactor it cleanly.

  How to Attach Companion Skills (Click "+" in the chat bar -> "Skills >"):
  • plain-english-walkthrough-bug-audit (/walkthrough) — Decode cryptic variable names, explain the algorithm block-by-block, and audit for silent bugs
  • hpc-slurm-cluster-readiness (/hpc-ready) — Convert hardcoded laptop code into a fast, CLI-driven script with a companion SLURM sbatch script for FSU RCC
  ```

#### 3. Knowledge & Tools *(Optional)*
If your lab has a standard SLURM submission template for FSU's Research Computing Center (RCC) or a lab coding style guide, you can upload it here so `/hpc-ready` automatically uses your lab's partition and conda environment names.

#### 4. Capabilities & Model
In the **Capabilities & Model** tab, configure the toggles and model as follows:

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | **OFF** | Not needed for code explanation, debugging, or SLURM script generation. |
| **Add Files & Images** | **ON** | Lets you upload `.py`, `.R`, `.m`, or `.sh` script files (or screenshots of terminal tracebacks) directly into the chat. |
| **Web Search** | **OFF** *(or ON)* | Keep **OFF** for general debugging/refactoring, or toggle **ON** if you work with niche scientific libraries and want the agent to check live package docs. |
| **Generate Artifacts** | **ON** | **Essential for this agent**—renders refactored Python/R scripts and `submit_job.sh` SLURM scripts in clean side-by-side code panels. |
| **Model (`Change` button)** | • **OpenAI**: `gpt-5.6-luna` *(Default, set **Reasoning Effort**: `High`)*<br>• **Anthropic**: `claude-sonnet-5` or `claude-opus-4-7` *(set **Creativity**: `Low`)* | Setting **Reasoning Effort** to `High` on `gpt-5.6-luna` (or using `claude-sonnet-5`/`claude-opus-4-7` with `Low` Creativity) is ideal for catching subtle mathematical bugs and vectorizing nested loops. |

#### 5. Starter Prompts *(Optional)*
In **5. Starter Prompts**, click **Add Starter Prompt** and enter the **Title** and **Prompt** fields below, then click **Create**:

| Title | Prompt |
| :--- | :--- |
| `Walkthrough & Silent Bug Audit (/walkthrough)` | `Run /walkthrough on the script I paste next to explain it in plain English and check for silent scientific bugs.` |
| `Prepare Script for FSU HPC / SLURM (/hpc-ready)` | `Run /hpc-ready on the script I paste next to vectorize slow loops, add CLI arguments, and generate a SLURM sbatch script.` |
| `Full Code Audit + HPC Refactor` | `Run both /walkthrough and /hpc-ready on the research script I paste next.` |

---

### Part 3: Test with Skills in the Preview Pane & Click Create
1. In the **Preview** chat pane on the right side of the Agent Builder (or after clicking **Create**), click the **`+` button** on the left side of the message input bar (`+ Type a message...`) → hover over **`Skills >`** → click `plain-english-walkthrough-bug-audit` and `hpc-slurm-cluster-readiness` to attach them.
2. Open [`example-input.md`](./example-input.md), copy the sample undocumented Monte Carlo simulation script, paste it into the chat, and compare your output with [`example-output.md`](./example-output.md).
3. Click **Create** at the bottom of the screen to save your **Research Code Explainer & Refactorer** agent!

---

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Core scientific software mentor persona and refactoring rules |
| [`skills/line-by-line-walkthrough.md`](./skills/line-by-line-walkthrough.md) | Skill for explaining unfamiliar code and catching silent research bugs |
| [`skills/hpc-slurm-readiness.md`](./skills/hpc-slurm-readiness.md) | Skill for converting laptop code into CLI + SLURM batch jobs |
| [`example-input.md`](./example-input.md) | Sample undocumented Python lab script with slow loops and hardcoded paths |
| [`example-output.md`](./example-output.md) | Sample plain-English walkthrough, vectorized refactor, and SLURM job script |

---

## Modify & Play: Ideas to Try

Once you have the baseline agent running, try customizing it for your workflow:

1. **Add a Cross-Language Translator Skill (`/translate`)**:
   - *Try this*: Create a third skill called `/translate` that converts legacy **MATLAB**, **SAS**, or **SPSS** syntax into open-source **Python (`numpy`/`scipy`/`statsmodels`)** or **R**, including a short verification snippet to confirm both languages output identical numbers.
2. **Customize SLURM Defaults for Your FSU RCC Partition**:
   - *Try this*: Edit [`skills/hpc-slurm-readiness.md`](./skills/hpc-slurm-readiness.md) to pre-fill your lab's specific FSU RCC partition/account name (`#SBATCH --partition=...` or `#SBATCH --account=...`) and your conda/mamba environment activation lines.
3. **Socratic Teaching Mode for Students**:
   - *Try this*: If you are a faculty member sharing this agent with students in a computational course, modify `system-prompt.md` so the agent explains the bug and gives a 2-line hint rather than writing the entire refactored script for them.

