# FSU ArtesAI Personal Agent Examples

Welcome to the **FSU ArtesAI Personal Agent Examples** repository! This collection provides ready-to-use blueprints for building Personal Agents in Florida State University's **ArtesAI** platform.

### How to Get Started
1. **Pick an Agent to Try**: Browse the **Research** and **Teaching** tables below and click on any agent that matches your workflow.
2. **Copy-Paste into ArtesAI (~5 Minutes)**: Every agent's guide walks you through copying its **Companion Skills** (`skills/`), **System Prompt** (`system-prompt.md`), and optional **Knowledge** files into your ArtesAI account.
3. **Test & Customize**: Run the ready-made sample prompt in `example-input.md` to see how the agent works, then use the **"Modify & Play"** ideas at the bottom of the guide to tailor it to your own lab, course, or department!

---

## Example Agents Catalog

### Research

| Agent | What It Does |
| :--- | :--- |
| [**Abstract Synthesizer**](./agents/abstract-synthesizer/README.md) | Turns collections of paper abstracts, reading notes, or PDF excerpts into structured synthesis narratives, methodology comparison tables, and research gap analyses without inventing citations. |
| [**Research Paper Matchmaker**](./agents/research-paper-matchmaker/README.md) | Connects research papers to your specific project in plain language, explaining what each paper offers, what does not apply, and how they rank—or finds relevant real papers with links. |
| [**Grant Compass**](./agents/grant-compass-agent/README.md) | Helps FSU faculty and research staff discover and verify funding opportunities (including FSU limited-submission checks), evaluate project-to-sponsor fit, and build proposal checklists, timelines, and sponsor-aligned outlines. |
| [**Grant & Abstract Coach**](./agents/grant-abstract-coach/README.md) | Coaches and advises researchers on their draft NSF 1-Page Project Summaries and NIH SF424 Summary/Narrative/Aims documents, simulates reviewer panel critiques, and guides Broader Impacts planning without ghostwriting text. |
| [**Research Data First Look**](./agents/research-data-first-look/README.md) | Inspects uploaded CSV files and multi-sheet Excel workbooks before analysis to produce an exact, non-destructive audit of variables, missingness, keys, cross-sheet joins, codebook rules, and analysis readiness. |
| [**Research Data Wrangler**](./agents/research-data-wrangler/README.md) | Turns column headers, a few sample rows, or data-cleaning decisions into reproducible R (`tidyverse`) or Python (`pandas`) cleaning scripts and FAIR-compliant Data Dictionaries (codebooks). |
| [**Scientific Figure Recreator**](./agents/scientific-figure-recreator/README.md) | Inspects an uploaded scientific figure or plot screenshot and generates self-contained, publication-styled code in Python, R (`ggplot2`), Stata, or MATLAB using synthetic data. |
| [**Research Code Explainer & Refactorer**](./agents/code-explainer-refactorer/README.md) | Decodes undocumented legacy lab scripts (Python, R, MATLAB, Bash), flags silent scientific bugs, and prepares laptop scripts to run on FSU's Research Computing Center (RCC) SLURM cluster. |
| [**Research-to-LaTeX Agent**](./agents/research-to-latex/README.md) | Converts research notes, Markdown reports, tables, equations, or draft documents into clean, compile-ready LaTeX source code or user-provided `.tex` templates without inventing results or references. |
| [**Lab Onboarding Assistant**](./agents/lab-onboarding-agent/README.md) | Helps new undergraduate and graduate researchers get oriented in a lab by answering documentation-grounded questions about projects, contacts, tools, first-week checklists, and data-handling policies. |

### Teaching

| Agent | What It Does |
| :--- | :--- |
| [**Syllabus & Rubric Builder**](./agents/syllabus-rubric-builder/README.md) | Turns rough course notes into an FSU Simple Syllabus draft, measurable Bloom's Taxonomy learning objectives, an `ai.fsu.edu` Traffic-Light AI policy, analytic grading rubrics, and a 16-week schedule. |
| [**FSU Accessibility Reviewer**](./agents/accessibility-reviewer/README.md) | Reviews uploaded course syllabi, documents, slides, flyers, web/Canvas pages, and caption files for accessibility under WCAG 2.1 AA, ADA Title II, and FSU guidelines, returning a rating (`Good` to `Very Bad`) and app-specific fixes. |

---

## Guides & Tips for Getting the Most Out of ArtesAI Agents

- [**Step-by-Step ArtesAI Quick Start Guide (`docs/quick-start-guide.md`)**](./docs/quick-start-guide.md): Full walkthrough of how to create Companion Skills (`Settings → My Skills`), configure the 5-step Personal Agent Builder, and set the **Capabilities & Model** toggles in ArtesAI.
- [**System Prompts vs. Skills: What's the Difference? (`docs/system-prompts-vs-skills.md`)**](./docs/system-prompts-vs-skills.md): Learn how System Prompts and Skills work together and when to put instructions in a System Prompt vs. a reusable Skill.
- [**What Goes in an Agent's Knowledge? (`agents/grant-compass-agent/knowledge/README.md`)**](./agents/grant-compass-agent/knowledge/README.md): Explore upload-ready reference packets, what each contains, why an agent uses them, and how to attach them in **Step 3: Knowledge & Tools**.
- **Start Simple, Then Layer Skills**: Test an agent with just its `system-prompt.md` first, then attach skills one at a time so you can see how each skill shapes the output.
- **Experiment with "Modify & Play"**: At the bottom of every agent's `README.md`, you'll find concrete ideas for tweaking tone, output formats, and domain rules.

---

## Adding Your Own Agent Example

Want to share an agent you built for your FSU course, lab, or office?
1. Duplicate the [`_agent-template`](./agents/_agent-template/README.md) folder inside [`agents/`](./agents/) and rename it in lowercase `kebab-case` (e.g., `agents/your-agent-name`).
2. Fill in `system-prompt.md`, add your `skills/`, and include a realistic `example-input.md` and `example-output.md`.
3. Add a link to your new folder in the **Example Agents Catalog** table above.
4. Read our [**Contributing Guidelines (`CONTRIBUTING.md`)**](./CONTRIBUTING.md) for the full folder layout, skill description character limits (`< 300` chars), and Pull Request checklist!

---

## Having Trouble? Submit an Issue (A Note on Scope)

These examples are intended to be **customizable starting points and educational blueprints**—not turnkey, fully fledged software products. Because every research lab, academic discipline, and course has its own workflows and edge cases, you are encouraged to adapt the prompts, tweak the skills, and always verify outputs before relying on them for courses, publications, or grant submissions.

If you run into trouble setting up an agent, notice outdated instructions as ArtesAI evolves, or find a prompt or skill that isn't behaving as expected, please [**open a GitHub Issue**](https://github.com/FSUAIforResearch/ArtesAIPersonalAgents/issues) with:
- The **agent and skill name(s)** you were using
- The **model** selected in ArtesAI
- A brief description of what you expected vs. what happened

If you have a refined version of one of these agents that you would like to share please consider submitting a pull request using our contributing guidelines!


