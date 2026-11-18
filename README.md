# FSU ArtesAI Personal Agent Examples

Welcome to the **FSU ArtesAI Personal Agent Examples** repository! This collection provides ready-to-use blueprints for building Personal Agents in Florida State University's **ArtesAI** platform.

Each folder in this repository contains everything you need to build a specialized AI assistant in minutes:
- **Step-by-step setup instructions** (`README.md`)
- **A copy-pasteable System Prompt** (`system-prompt.md`)
- **Modular Skills** (`skills/`) to copy into your ArtesAI account
- **Sample Input & Output** (`example-input.md` and `example-output.md`) so you can test your agent right away
- **"Modify & Play" ideas** to customize the agent for your own department, lab, or workflow

> **New to System Prompts & Skills?** Read our quick guide: [**System Prompts vs. Skills: What's the Difference? (`docs/system-prompts-vs-skills.md`)**](./docs/system-prompts-vs-skills.md) to learn how they work together and when to put instructions in a System Prompt vs. a reusable Skill.

> **What goes in an agent's knowledge?** Explore the [Grant Compass Knowledge Pack (`agents/grant-compass-agent/knowledge/`)](./agents/grant-compass-agent/knowledge/README.md) for upload-ready reference packets, what each contains, why the agent uses it, and how to add it in ArtesAI.

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

## Quick Start: How to Build an Agent & Its Skills in ArtesAI

In FSU's ArtesAI, **Skills** and **Personal Agents** are created in two separate places. **Create the Skills first** (`Settings → My Skills`) so that when you open the Personal Agent builder, you can immediately attach and test your skills right inside the right-hand **Preview** chat pane as you build the agent!

### Part 1: Create the Skills First (`Settings → My Skills`)
Every file in an agent's `skills/` folder is a **standard, platform-agnostic skill file** (YAML frontmatter `---` at the top with `name:` and `description:`, followed by the Markdown instructions below `---`).
1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and select **Settings**.
2. In the Account sidebar, click **My Skills** and then click the **`+ New Skill`** button in the top right.
3. Open each skill `.md` file in the agent's `skills/` folder and copy its sections into the **Create Skill** modal:
   - **Name**: Copy the `name:` value from the top frontmatter (e.g., `methodology-matrix-extractor`).
   - **Description (`0/300` characters)**: Copy the `description:` value from the top frontmatter (pre-sized `< 300 chars` to tell the model what the skill is for and when to apply it).
   - **Always On**: Leave **Unchecked (`Ad Hoc`)** *(ArtesAI allows a maximum of 5 `Always On` skills across your entire account, so keeping agent-specific skills `Ad Hoc` saves your global slots)*.
   - **Skill Instructions (`0/30,000` dark editor)**: Copy the Markdown body below the second `---` line into the dark editor and click **Create**.

### Part 2: Create the Personal Agent (Quick Create + 5-Step Builder)
1. **Open the Agent Builder (`Quick Create`)**:
   - In the left maroon FSU sidebar, click **Explore Agents** (or select the **Agents** tab).
   - Scroll to the **My Agents** (*Agents created by me*) section and click the **`+ Create`** button next to **My Agents** (or the dashed **`+ Create`** card).
   - In the **Quick Create** popup box, enter the **Agent Name** from the agent's `README.md` and click **`Let's go`**.
2. **Step 1 — Instructions (`system-prompt.md`)**:
   - Open the agent's `system-prompt.md` file, copy the text, and paste it into the **Specific Instructions** field.
   - **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** in ArtesAI to save on context window tokens and keep the model focused strictly on your agent's instructions and skills.
3. **Step 2 — Name & Identity**:
   - **Name**: Pre-filled from Quick Create (verify it matches the agent title).
   - **Short Description**: Copy the 1-sentence summary into the **Short Description** box.
   - **Welcome Message (Rich Text Box)**: Replace the default *"Welcome to the Chat!"* boilerplate text with the custom **Welcome Message** provided in each agent's `README.md`. This text appears on the start screen of your agent chat, reminding you what to paste and which skills to attach!
4. **Step 3 — Knowledge & Tools**:
   - *(Optional)* Upload any static reference files you want the agent to always know (e.g., your lab style guide, department syllabus template, or agency solicitation PDF).
5. **Step 4 — Capabilities & Model**:
   - Set the four capability toggles (**Image Creation**, **Add Files & Images**, **Web Search**, and **Generate Artifacts**) and click **Change** next to **Model** to select your preferred **Model Type** (`OpenAI`, `Anthropic`, `xAI`, `Mistral`, or `Meta`) and **Model** (such as `gpt-5.4`, `gpt-6-luna`, `claude-sonnet-5`, or `claude-opus-4-7`) using the recommended table in each agent's `README.md`.
6. **Step 5 — Starter Prompts**:
   - *(Optional)* Click **Add Starter Prompt** and enter the **Title** and **Prompt** pairs listed in each agent's `README.md`, then click **Create**.

### Part 3: Test with Skills in the Preview Pane & Click Create
1. While still in the Agent Builder (or after clicking **Create**), look at the **Preview** chat pane on the right.
2. Click the **`+` button** on the left side of the message input bar (`+ Type a message...`).
3. Hover over **`Skills >`** in the popup menu and click the skill(s) you created in Part 1 to attach them.
4. Copy the sample prompt from `example-input.md` into the chat, verify the response against `example-output.md`, and click **Create** at the bottom to save your agent!

## Understanding "Capabilities & Model" (Step 4)

In step **4. Capabilities & Model**, ArtesAI lets you toggle four features and pick a base model. Here is a quick guide to when to turn each toggle **On** or **Off**:

| Capability / Setting | What It Does in ArtesAI | When to Turn It **ON** vs. **OFF** |
| :--- | :--- | :--- |
| **Image Creation** | Allows the agent to generate images from text prompts. | Keep **OFF** for academic writing, coding, and data agents (prevents accidental image generation). Turn **ON** only if brainstorming visual/graphical concepts. |
| **Add Files & Images** | Lets users attach PDFs, CSVs, scripts, or screenshots directly inside a chat session. | Turn **ON** for almost all research, teaching, and coding agents so you can drop papers, syllabi, or `.py`/`.csv` files into the chat. |
| **Web Search** | Lets the agent search the live internet during a conversation. | Keep **OFF** when you want strict grounding in *only* the text/data you provide (e.g., `Abstract Synthesizer`). Turn **ON** when checking live funder websites or current policy dates. |
| **Generate Artifacts** | Opens long tables, polished drafts, and code scripts in a dedicated side-by-side preview/copy window. | Turn **ON** for all agents in this repo—it makes Markdown matrices, syllabi, and Python/R scripts much easier to read and copy. |
| **Model (`Change` button)** | Opens the **Model Options** dialog to choose a **Model Type**, specific **Model**, **Max Response Tokens**, and tuning controls (**Creativity** or **Verbosity / Reasoning Effort**). | Defaults to `OpenAI (gpt-5.4)`. Check the dropdown to see what models are available |
---

## Tips for Getting the Most Out of ArtesAI Agents

- **Start Simple, Then Layer Skills**: Test the agent with just its `system-prompt.md` first, then add skills one at a time so you can see how each skill shapes the output.
- **Attach Reference Files**: ArtesAI allows you to upload reference documents (such as your lab style guide, agency solicitation PDFs, or department syllabus templates) directly to your Personal Agent's knowledge base.
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


