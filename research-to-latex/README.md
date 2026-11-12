# Research-to-LaTeX Agent

> **One-Sentence Summary**: Give the agent research notes, Markdown reports, assignment instructions, experimental results, or draft documents, and it converts them into a clean, editable LaTeX project/draft.

[Back to Main Catalog](../README.md)

## Overview

This agent helps researchers, students, and faculty turn existing research materials into structured, editable LaTeX drafts. It preserves supplied findings, technical details, uncertainty, and limitations, and flags missing information instead of inventing results or references. It can also revise an existing LaTeX document or work within a researcher-provided template.

- **Model in the supplied configuration**: `OpenAI (gpt-5.4)`.
- **Inputs**: Notes, Markdown reports, assignment instructions, results, tables, equations, draft sections, and LaTeX templates.
- **Outputs**: LaTeX source and, when supported, `.tex` artifacts; larger drafting tasks also include an outline and researcher checklist.

## What Was Supplied and What Was Added

The name, description, welcome message, knowledge-source settings, capabilities, model settings, starter prompts, and Specific Instructions below come from the agent creator. These are recorded settings, not an independent verification of the current ArtesAI interface or model limits.

[`system-prompt.md`](./system-prompt.md) preserves the supplied Specific Instructions, with two missing Markdown code-fence closures repaired and a clarification that downloadable `.tex` files contain raw LaTeX. It intentionally retains the full instructions rather than meeting the template's approximate 250-word recommendation, so the creator's existing workflow remains documented and works without companion skills.

The three companion skills, fictional sample input, illustrative response, and sample `.tex` file were authored for this repository. The skills are optional additions; they were not part of the creator's reported ArtesAI configuration. The sample response has not been generated or verified in ArtesAI, and the sample LaTeX has not been compiled here.

## How to Build This Agent in ArtesAI

If you already built the agent, use these instructions to compare your settings; you do not need to create it again.

### Part 1: Optional Companion Skills

The base agent supports all four starter prompts without these skills. To add reusable, more focused workflows, create the skills under **Settings → My Skills → + New Skill**, following the repository's setup convention:

1. Open a skill file below.
2. Copy its frontmatter `name` into **Name** and `description` into **Description**.
3. Leave **Always On** unchecked (`Ad Hoc`).
4. Copy only the Markdown body below the second `---` into **Skill Instructions**, then create the skill.

| File | Skill name | When to attach it |
| :--- | :--- | :--- |
| [Convert Markdown](./skills/convert-markdown-to-latex.md) | `markdown-to-latex-converter` | Converting a Markdown report, including its tables, equations, and code. |
| [Use a template](./skills/draft-with-latex-template.md) | `latex-template-drafter` | Drafting within a supplied document class, template, or manuscript structure. |
| [Review a draft](./skills/review-latex-draft.md) | `latex-draft-reviewer` | Checking and improving existing LaTeX while preserving research meaning. |

### Part 2: Create or Configure the Personal Agent

#### 0. Open the Agent Builder

Following the repository's navigation instructions, go to **Explore Agents → My Agents → + Create**, enter **Research-to-LaTeX Agent**, and select **Let's go**. For an existing agent, open its editor instead. Interface labels may differ from the recorded setup.

#### 1. Instructions

Copy [`system-prompt.md`](./system-prompt.md) into **Specific Instructions**.

The creator also supplied default **Platform Instructions**, recorded separately in [`platform-instructions.md`](./platform-instructions.md). To reproduce that reported configuration, retain those defaults or use the recorded text if needed. The general repository template recommends clearing defaults to save context; that is an alternative configuration, not the one reported by the creator. Keep platform text separate from Specific Instructions.

The platform text requests double-dollar delimiters for chat mathematics. The Specific Instructions explicitly require normal LaTeX conventions in source code. Check this behavior during testing, especially if you retain the platform defaults.

#### 2. Name & Identity

**Name**:

```text
Research-to-LaTeX Agent
```

**Short Description**:

```text
Give the agent research notes, Markdown reports, assignment instructions, experimental results, or draft documents, and it converts them into a clean, editable LaTeX project/draft.
```

**Welcome Message** (the text displayed at the start of a chat):

```markdown
**Welcome to the Research-to-LaTeX Agent!**

Turn your research materials into clean, editable LaTeX drafts. Provide research notes, Markdown reports, experimental results, assignment instructions, draft sections, or other supporting documents, and this agent can organize them into a structured LaTeX paper or report.

The agent preserves your original research and will flag missing information rather than inventing results, citations, or other details.

**Try uploading a research document or pasting your notes and asking:**

*"Turn this into a LaTeX research paper draft."*
```

#### 3. Knowledge & Tools

Add the following website sources using the limits and usage instructions supplied by the creator. These are LaTeX formatting references, not sources of new research claims or citations.

**Source 1**:

- **URL**: https://www.overleaf.com/learn
- **Maximum pages to use**: `30`.
- **When to use**:

```text
Use this source when creating, converting, formatting, editing, or troubleshooting LaTeX. Consult it for reliable Overleaf guidance on LaTeX document structure, commands, packages, equations, tables, figures, images, lists, labels, references, formatting, and common LaTeX errors.
```

**Source 2**:

- **URL**: https://www.overleaf.com/learn/latex/Bibliography_management_in_LaTeX
- **Maximum pages to use**: `10`.
- **When to use**:

```text
Use this source when the user needs LaTeX citations, references, bibliographies, BibTeX or BibLaTeX support, .bib files, citation commands, or bibliography formatting. Use it to format citation information provided by the user, but never invent missing sources, references, authors, publication details, DOIs, or citation data.
```

No persistent uploaded knowledge files were supplied. Users can attach their own research materials, `.tex` templates, `.bib` files, and figure files for a particular task. Do not assume referenced files have been provided.

#### 4. Capabilities & Model

| Setting | Supplied value | Purpose |
| :--- | :--- | :--- |
| Image Creation | `Off` | This agent converts existing research materials. |
| Add Files & Images | `On` | Lets users supply research documents, templates, and figures. |
| Web Search | `Off` | Live web search is not part of the reported workflow. |
| Generate Artifacts | `On` | Enables document artifacts where supported. |
| Model Type | `OpenAI` | Creator's selection. |
| Model | `gpt-5.4` | Creator's selection. |
| Max Response Tokens | `128000` | Recorded UI setting; verify that your selected model accepts it. |
| Verbosity | `Auto` | Creator's selection. |
| Reasoning Effort | `High` | Creator's selection. |

Website knowledge sources and live Web Search are configured separately in the supplied setup. Verify that both website sources finish processing in ArtesAI; listing their URLs here does not verify successful ingestion.

#### 5. Starter Prompts

Add each **Title** and **Prompt** pair below:

| Title | Prompt |
| :--- | :--- |
| Improve my LaTeX draft | Review the LaTeX draft I provide and improve its structure, consistency, and LaTeX formatting without changing the meaning of my research or inventing missing information. |
| Use my LaTeX template | Use the LaTeX template and research materials I provide to create a draft while preserving the template's required document class, structure, formatting, and commands. |
| Convert a Markdown report | Convert my Markdown research or technical report into well-structured LaTeX. Preserve the original information, tables, equations, code, and section organization where appropriate. |
| Turn my research into LaTeX | Use the research materials I provide to create a clean, editable LaTeX draft. Preserve my findings and technical details, organize the material appropriately, and clearly mark missing information rather than inventing it. |

### Part 3: Test the Agent

1. Open the agent's **Preview** pane or a new chat and paste the request and report from [`example-input.md`](./example-input.md). Start without companion skills to verify the base agent.
2. Compare behavior with [`example-output.md`](./example-output.md). Wording can differ; check the preserved values, equation, limitations, missing-information notices, and LaTeX structure.
3. Confirm that a generated `.tex` artifact contains raw LaTeX, with no Markdown fences, outline, or checklist embedded in the file.
4. Open the generated source in Overleaf using pdfLaTeX. The standalone [`main.tex`](./main.tex) is an illustrative comparison file. Record compilation errors or missing references; do not label either output compiled until checked.
5. If using companion skills, attach one with **+ → Skills** and repeat the relevant workflow. For the template skill, provide an actual template. For the review skill, provide an actual `.tex` draft.
6. Save the agent if you made changes. To document a real run, replace or supplement the illustrative response with your actual ArtesAI output and record the run date, model, attached skills, and compilation result.

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [README.md](./README.md) | Setup, supplied settings, and testing instructions. |
| [system-prompt.md](./system-prompt.md) | Supplied Specific Instructions, with formatting repairs and artifact clarification. |
| [platform-instructions.md](./platform-instructions.md) | Supplied default Platform Instructions, recorded separately. |
| [skills/convert-markdown-to-latex.md](./skills/convert-markdown-to-latex.md) | Optional Markdown conversion workflow. |
| [skills/draft-with-latex-template.md](./skills/draft-with-latex-template.md) | Optional template-based drafting workflow. |
| [skills/review-latex-draft.md](./skills/review-latex-draft.md) | Optional LaTeX editing and review workflow. |
| [example-input.md](./example-input.md) | Fictional research report and a pasteable conversion request. |
| [example-output.md](./example-output.md) | Illustrative outline, LaTeX response, and researcher checklist. |
| [main.tex](./main.tex) | Raw LaTeX matching the illustrative response. |

## Remaining Validation by the Agent Creator

- Confirm that the recorded model settings save successfully and both website sources process successfully in ArtesAI.
- Run the example in ArtesAI and compile the resulting `.tex` file in Overleaf. No actual ArtesAI response or compilation result was supplied for this repository entry.
- Create the optional skills in your own ArtesAI account only if you want to use them; adding these files to GitHub does not create platform skills.
- Submit the repository changes through your team's normal GitHub process when ready. Local edits do not publish the contribution.

## Modify & Play: Ideas to Try

1. Supply a lab, course, thesis, or journal template and check that its document class and required commands survive conversion.
2. Provide a real bibliography alongside a draft and check that every citation key maps to supplied source information.
3. Combine two reports with conflicting measurements and check that the agent flags the conflict instead of choosing a value.
4. Adapt the optional review skill to a department's style guide while keeping all research-integrity guardrails.
