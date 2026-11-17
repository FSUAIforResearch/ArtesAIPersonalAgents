# Research-to-LaTeX Agent

> **One-Sentence Summary**: Give the agent research notes, Markdown reports, assignment instructions, experimental results, or draft documents, and it converts them into a clean, editable LaTeX project or draft without inventing results or citations.

[**⬅ Back to Main Catalog**](../README.md)

---

## Overview

Turning rough lab notes, Markdown reports, tables, and equations into clean, compile-ready LaTeX—or fitting existing notes into a journal or thesis `.tex` template—takes hours of repetitive formatting and debugging.

The **Research-to-LaTeX Agent** helps FSU faculty, researchers, and students convert existing research materials into structured, editable LaTeX source code. It preserves every supplied measurement, equation, code snippet, and limitation, and uses valid `% TODO:` comments and `\cite{TODO}` placeholders for missing details rather than inventing findings or references.

- **Recommended Model in ArtesAI**: `OpenAI (gpt-5.6-luna)` (Default) or `Anthropic (claude-sonnet-5)`
- **Estimated Setup Time**: ~5 minutes

---

## How to Build This Agent & Its Skills in ArtesAI

In ArtesAI, **create the companion Skills first** under your account **Settings → My Skills** (Part 1). That way, when you build the **Personal Agent** (Part 2), you can immediately attach and test the skills inside the right-hand **Preview** pane before clicking **Create** (Part 3).

### Part 1: Create the Companion Skills First (`Settings → My Skills`)

1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and click **Settings**.
2. Click **My Skills** on the left, then click **`+ New Skill`** in the top-right corner.
3. Open each standard skill file below and copy its parts into the **Create Skill** modal (**Name** = `name:` from the top `---` block, **Description** = `description:` from the top `---` block, leave **Always On** unchecked/`Ad Hoc`, and paste only the Markdown body below the second `---` into the dark editor box):
   - **[`markdown-to-latex-converter`](./skills/convert-markdown-to-latex.md)**: Converts Markdown research reports and notes (including tables, equations, and code blocks) into idiomatic, compile-ready LaTeX.
   - **[`latex-template-drafter`](./skills/draft-with-latex-template.md)**: Populates a user-provided journal, conference, thesis, or course `.tex` template with your research materials while preserving the template's document class, macros, and structure.
   - **[`latex-draft-reviewer`](./skills/review-latex-draft.md)**: Audits and fixes an existing `.tex` draft for syntax errors, unbalanced braces/environments, cross-references, and formatting consistency without altering your research meaning.

---

### Part 2: Create the Personal Agent

#### 0. Launch "Quick Create"
1. In the left maroon FSU sidebar, click **Explore Agents** (or switch to the **Agents** tab).
2. Under **My Agents** (*Agents created by me*), click the **`+ Create`** button next to the **My Agents** heading (or click the dashed **`+ Create`** card).
3. In the **Quick Create** popup box, enter **`Research-to-LaTeX Agent`** as the **Agent Name** and click **`Let's go`**.

#### 1. Instructions (System Prompt)
1. Open [`system-prompt.md`](./system-prompt.md), copy the text, and paste it into the **Specific Instructions** field.
2. **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** to save on context tokens and prevent generic chat math rules (`$$...$$`) from interfering with valid LaTeX source syntax.

#### 2. Name & Identity
In the **Name & Identity** panel, fill in the three fields below (you'll see them update live in the right-hand **Preview** pane):

- **Name**:
  ```text
  Research-to-LaTeX Agent
  ```
- **Short Description**:
  ```text
  Give the agent research notes, Markdown reports, assignment instructions, experimental results, or draft documents, and it converts them into a clean, editable LaTeX project/draft.
  ```
- **Welcome Message** *(replace the default "Welcome to the Chat!" text in the rich-text editor box)*:
  ```text
  Welcome to the Research-to-LaTeX Agent!

  Turn your research materials into clean, editable LaTeX drafts. Provide research notes, Markdown reports, experimental results, assignment instructions, draft sections, or a .tex template, and I will organize them into structured LaTeX while flagging any missing details with % TODO comments rather than inventing results or citations.

  How to Attach Companion Skills (Click "+" in the chat bar -> "Skills >"):
  • markdown-to-latex-converter — Convert a Markdown report (tables, equations, code) into LaTeX
  • latex-template-drafter — Populate your own journal, conference, or thesis .tex template
  • latex-draft-reviewer — Debug and polish an existing .tex draft without changing research meaning
  ```

#### 3. Knowledge & Tools *(Optional)*
You can add the two Overleaf documentation sources below as Website Knowledge Sources so the agent can reference official LaTeX and BibTeX/BibLaTeX syntax rules:

- **Website Source 1**: `https://www.overleaf.com/learn` (Max pages: `30`)
  - *When to use*: `Use this source when creating, converting, formatting, editing, or troubleshooting LaTeX document structure, commands, packages, equations, tables, figures, lists, labels, and common errors.`
- **Website Source 2**: `https://www.overleaf.com/learn/latex/Bibliography_management_in_LaTeX` (Max pages: `10`)
  - *When to use*: `Use this source when formatting LaTeX citations, references, bibliographies, BibTeX or BibLaTeX support, and .bib files provided by the user. Never invent missing sources or DOIs.`

#### 4. Capabilities & Model
In the **Capabilities & Model** tab, configure the toggles and model as follows:

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | **OFF** | Not needed for converting research materials into LaTeX source code. |
| **Add Files & Images** | **ON** | Lets you upload Markdown notes, `.tex` templates, `.bib` files, and draft documents directly in chat. |
| **Web Search** | **OFF** | Keeps the draft strictly grounded in your supplied research materials and prevents hallucinated external citations. |
| **Generate Artifacts** | **ON** | Renders the complete `.tex` source code in a clean side-by-side panel ready to copy into Overleaf. |
| **Model (`Change` button)** | • **OpenAI**: `gpt-5.6-luna` *(Default, `128,000` max tokens, set **Reasoning Effort**: `High`)*<br>• **Anthropic**: `claude-sonnet-5` *(set **Creativity**: `Low`)* | High reasoning effort and low creativity ensure balanced LaTeX environments, accurate table/equation conversion, and strict preservation of your reported values. |

#### 5. Starter Prompts *(Optional)*
In **5. Starter Prompts**, click **Add Starter Prompt** and enter the **Title** and **Prompt** fields below, then click **Create**:

| Title | Prompt |
| :--- | :--- |
| `Convert a Markdown Report` | `Convert my Markdown research or technical report into well-structured LaTeX. Preserve the original information, tables, equations, code, and section organization where appropriate.` |
| `Use My LaTeX Template` | `Use the LaTeX template and research materials I provide to create a draft while preserving the template's required document class, structure, formatting, and commands.` |
| `Improve My LaTeX Draft` | `Review the LaTeX draft I provide and improve its structure, consistency, and LaTeX formatting without changing the meaning of my research or inventing missing information.` |
| `Turn My Research into LaTeX` | `Use the research materials I provide to create a clean, editable LaTeX draft. Preserve my findings and technical details, organize the material appropriately, and clearly mark missing information rather than inventing it.` |

---

### Part 3: Test with Skills in the Preview Pane & Click Create
1. In the **Preview** chat pane, click the **`+` button** in the message bar → hover over **`Skills >`** → attach `markdown-to-latex-converter` (or test the base agent directly).
2. Open [`example-input.md`](./example-input.md), copy and paste the sample Markdown report prompt into the chat, and compare the result with [`example-output.md`](./example-output.md).
3. Click **Create** at the bottom of the screen to save your **Research-to-LaTeX Agent**!

---

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Core role, research-integrity guardrails, LaTeX validity rules, and default workflow |
| [`skills/convert-markdown-to-latex.md`](./skills/convert-markdown-to-latex.md) | Skill for converting Markdown reports, tables, equations, and code into LaTeX |
| [`skills/draft-with-latex-template.md`](./skills/draft-with-latex-template.md) | Skill for populating a user-provided `.tex` template with research materials |
| [`skills/review-latex-draft.md`](./skills/review-latex-draft.md) | Skill for debugging and polishing an existing `.tex` draft |
| [`example-input.md`](./example-input.md) | Sample Markdown technical report with a table, equation, code snippet, and missing items |
| [`example-output.md`](./example-output.md) | Sample output showing the Proposed Structure, compile-ready LaTeX source, and Researcher Checklist |

---

## Modify & Play: Ideas to Try

1. **Populate Your Target Journal or FSU Thesis Template**:
   - *Try this*: Attach `latex-template-drafter` and upload an IEEE, ACM, ACS, or FSU Electronic Thesis & Dissertation (ETD) `.tex` template alongside your rough notes to verify that all custom preamble commands and document classes are preserved.
2. **Pair with a `.bib` File**:
   - *Try this*: Upload your project's `.bib` file with your draft notes so the agent maps your inline references to your actual BibTeX keys and flags any uncited claims with `\cite{TODO}`.
3. **Test Conflict Detection Across Multiple Notes**:
   - *Try this*: Paste two lab updates that report slightly different sample sizes or run times and watch how the agent flags the discrepancy in the **Researcher Checklist** instead of silently picking one number.
4. **Adapt `latex-draft-reviewer` to Your Lab's Notation Style**:
   - *Try this*: Add your lab's preferred macros (e.g., `\mathbb{E}`, `siunitx` units, or `cleveref` `\cref{}`) to [`skills/review-latex-draft.md`](./skills/review-latex-draft.md) so the reviewer standardizes notation across co-authored drafts.
