# Contributing to FSU ArtesAI Personal Agent Examples

Thank you for contributing to the **FSU ArtesAI Personal Agent Examples** repository! Whether you are sharing a new Personal Agent built for your lab, course, or administrative workflow, adding a reusable Skill to an existing agent, or fixing a bug, these guidelines will help ensure your contribution fits cleanly into the catalog.

[**⬅ Back to Main README**](./README.md)

---

## 1. Ways to Contribute

1. **Report an Issue or Suggest an Improvement**:
   - Open a [**GitHub Issue**](https://github.com/FSUAIforResearch/ArtesAIPersonalAgents/issues) describing the agent/skill name, the model used in ArtesAI, and what you observed vs. expected.
2. **Add a Companion Skill to an Existing Agent**:
   - Add a new `.md` file to an existing agent's `skills/` directory and document it in that agent's `README.md`.
3. **Contribute a New Personal Agent Blueprint**:
   - Duplicate the [`agents/_agent-template/`](./agents/_agent-template/README.md) directory and follow the structure and checklist below.

---

## 2. Standard Directory & File Structure

Every agent lives in its own **lowercase `kebab-case` folder** inside [`agents/`](./agents/) (never inside `docs/`, and never with spaces or uppercase directory names):

```text
agents/your-agent-name/
├── README.md                  # Step-by-step ArtesAI setup guide (Parts 1, 2, and 3)
├── system-prompt.md           # Copy-pasteable Specific Instructions (< 350 words)
├── example-input.md           # Self-contained sample prompt(s) wrapped in ```text blocks
├── example-output.md          # Realistic sample output matching example-input.md
├── skills/                    # Lowercase folder containing 1–5 modular skill files
│   ├── first-skill-name.md
│   └── second-skill-name.md
└── knowledge/                 # (Optional) Upload-ready reference files for Step 3
    └── 01_reference_guide.md
```

---

## 3. Design & Formatting Requirements

Before opening a Pull Request, verify that your files follow these repository standards (see [**System Prompts vs. Skills (`docs/system-prompts-vs-skills.md`)**](./docs/system-prompts-vs-skills.md) for background):

### A. `system-prompt.md`
- **Keep It Focused (`~150–350 words`)**: Include only rules that apply to **100% of turns** (`## Your Role & Objective`, `## Core Behaviors & Guardrails`, and `## Default Workflow`).
- **Don't Duplicate Your Skills**: Put specialized multi-step workflows, long rubrics, or language-specific code templates inside `skills/*.md` rather than repeating them in `system-prompt.md`.
- **Self-Contained Baseline**: Ensure `## Default Workflow` works sensibly even if a user tests the agent before attaching optional skills.
- **No UI/Platform Instructions**: Never put human setup directions (e.g., *"Click the `+` button in ArtesAI"*) inside `system-prompt.md`.

### B. `skills/*.md`
- **Valid YAML Frontmatter**: Every skill file must start with a `---` block containing:
  - `name:` in `kebab-case` (matching or closely aligned with the filename).
  - `description:` **strictly under 300 characters** (ArtesAI enforces a `0/300` character limit on skill descriptions). State *what* the skill does and *when* to trigger it.
- **Clean Markdown Body**: Below the second `---` line, include `# Skill Title`, `## When to Apply This Skill`, and `## Step-by-Step Instructions`. Do not include platform UI setup instructions inside the skill body.

### C. `README.md` (Agent Setup Guide)
- Copy the exact section structure from [`agents/_agent-template/README.md`](./agents/_agent-template/README.md):
  1. `# Agent Name`, `> **One-Sentence Summary**: ...`, and ``[**⬅ Back to Main Catalog**](../../README.md)``
  2. `## Overview` (2–3 sentences, `- **Recommended Model in ArtesAI**: OpenAI (gpt-5.6-luna) (Default) or Anthropic (claude-sonnet-5)`, and `- **Estimated Setup Time**: ~5 minutes`)
  3. `## How to Build This Agent & Its Skills in ArtesAI` (`Part 1: Create the Companion Skills First`, `Part 2: Create the Personal Agent` with steps `0`–`5`, and `Part 3: Test with Skills in the Preview Pane & Click Create`)
  4. `## Files in This Folder` (table with clickable relative links)
  5. `## Modify & Play: Ideas to Try` (3–4 numbered customization ideas)
- **No Editorial Meta-Commentary**: Write directly to the FSU faculty member, researcher, or student building the agent. Remove any internal drafting notes or packaging disclaimers before submitting.

### D. `example-input.md` & `example-output.md`
- **Self-Contained & Reproducible**: Wrap sample prompts in ```` ```text ```` code blocks in `example-input.md` so users can copy and paste them immediately into the ArtesAI Preview pane.
- **Zero Sensitive Data, Credentials, or Real PII**: Use only public, open-access, or clearly labeled synthetic/fictional data in examples and optional `knowledge/` files. Never include real student records (FERPA), patient data (HIPAA), unpublished proprietary data, or API keys.

---

## 4. How to Submit a Pull Request

1. **Fork or Branch**: Create a new branch from `main` (e.g., `git checkout -b my-new-agent`).
2. **Build Your Agent Folder**: Copy [`agents/_agent-template/`](./agents/_agent-template/README.md) to `agents/your-agent-name/` and fill in all required files.
3. **Update the Main Catalog**: Add a row for your agent under **`### Research`** or **`### Teaching`** in the root [`README.md`](./README.md#example-agents-catalog) with a link to `./agents/your-agent-name/README.md` and a one-sentence summary.
4. **Run the Pre-PR Checklist**:
   - [ ] Folder and all skill filenames are lowercase `kebab-case` (no `.DS_Store` or scratch files committed).
   - [ ] Every skill's YAML `description:` is `< 300` characters.
   - [ ] `system-prompt.md` is concise and does not duplicate the full text of the skills.
   - [ ] `README.md` instructs users to clear the default **Platform Instructions** in Step 1.
   - [ ] `example-input.md` and `example-output.md` contain no sensitive or proprietary information.
5. **Open a Pull Request**: Push your branch and open a Pull Request against `main` with a short summary of who the agent helps and what skills it includes!
