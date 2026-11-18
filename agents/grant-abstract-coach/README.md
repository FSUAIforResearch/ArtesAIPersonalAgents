# Grant & Abstract Coach Agent

> **One-Sentence Summary**: Coaches and advises FSU researchers on their draft grant abstracts—auditing against **NSF 1-Page Project Summary** (`Overview`, `Intellectual Merit`, `Broader Impacts`) and **NIH SF424** (`Project Summary/Abstract`, `Project Narrative`, `Specific Aims`) requirements, simulating reviewer panel critiques, and guiding Broader Impacts planning **without ghostwriting the researcher's text**.

[**⬅ Back to Main Catalog**](../../README.md)

---

## Overview

Funding agencies like NSF and NIH expect grant summaries to be authored in the investigator's own voice while meeting strict structural and compliance rules—such as NSF's mandatory three-heading Project Summary (`Overview`, `Intellectual Merit`, `Broader Impacts`) or NIH's 30-line `Project Summary/Abstract`, 2–3 sentence `Project Narrative`, and 1-page `Specific Aims`.

The **Grant & Abstract Coach** is a **non-ghostwriting developmental coach**. Rather than rewriting your abstract for you, it audits your draft sentence by sentence, flags weak or unmeasurable verbs (*"explore"*, *"study"*), identifies missing quantitative benchmarks or interdependent aims, and gives you a concrete revision blueprint so you stay 100% in control of your prose.

- **Recommended Model in ArtesAI**: `OpenAI (gpt-5.6-luna)` (Default, Reasoning Effort: `High`) or `Anthropic (claude-sonnet-5)` / `claude-opus-4-7` (Creativity: `Low`/`Medium`)
- **Estimated Setup Time**: ~5 minutes

---

## How to Build This Agent & Its Skills in ArtesAI

In ArtesAI, **create the companion Skills first** under your account **Settings → My Skills** (Part 1). That way, while you are building the **Personal Agent** (Part 2), you can immediately attach and test the skills inside the right-hand **Preview** chat pane before clicking **Create** (Part 3).

### Part 1: Create the Companion Skills First (`Settings → My Skills`)

1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and click **Settings**.
2. Click **My Skills** on the left, then click **`+ New Skill`** in the top-right corner.
3. Open each standard skill file below and copy its parts into the **Create Skill** modal (**Name** = `name:` from the top `---` block, **Description** = `description:` from the top `---` block, leave **Always On** unchecked/`Ad Hoc`, and paste only the Markdown body below the second `---` into the dark editor box):
   - **[`nsf-project-summary-coach`](./skills/nsf-project-summary.md)** (`/nsf-summary`): Audits a user's draft against **NSF PAPPG 1-Page Project Summary** rules (`Overview`, `Intellectual Merit`, `Broader Impacts`), mapping which sentences belong under each mandatory heading and coaching the author on what to sharpen.
   - **[`nih-project-summary-coach`](./skills/nih-project-summary.md)** (`/nih-summary`): Coaches researchers on their draft **NIH SF424 summary documents**—auditing the 30-line `Project Summary/Abstract`, checking lay readability in the 2–3 sentence `Project Narrative`, and checking `Specific Aims` for aim independence.
   - **[`broader-impacts-coach`](./skills/broader-impacts-builder.md)** (`/impacts`): Critiques weak Broader Impacts sentences and coaches researchers through 3 tailored Florida/FSU activity frameworks, an evaluation planning matrix, and a structural outline so the PI can write a compelling section.
   - **[`reviewer-critique-simulator`](./skills/reviewer-critique-simulator.md)** (`/review`): Simulates a 3-reviewer grant panel / study section (The Tired Generalist, The Methodological Skeptic, and The Feasibility Pragmatist) to uncover weaknesses and coach the author on preemptive fixes before submission.

---

### Part 2: Create the Personal Agent

#### 0. Launch "Quick Create"
1. In the left maroon FSU sidebar, click **Explore Agents** (or switch to the **Agents** tab).
2. Under **My Agents** (*Agents created by me*), click the **`+ Create`** button next to the **My Agents** heading (or click the dashed **`+ Create`** card).
3. In the **Quick Create** popup box, enter **`Grant & Abstract Coach`** as the **Agent Name** and click **`Let's go`**.

#### 1. Instructions (System Prompt)
1. Open [`system-prompt.md`](./system-prompt.md), copy the text, and paste it into the **Specific Instructions** field.
2. **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** to save on context tokens.

#### 2. Name & Identity
In the **Name & Identity** panel, copy and paste the fields below (you'll see them update live in the right-hand **Preview** pane):

- **Name**:
  ```text
  Grant & Abstract Coach
  ```
- **Short Description**:
  ```text
  Coaches and advises researchers on their draft NSF and NIH grant summaries, Broader Impacts plans, and reviewer panel critiques without ghostwriting text.
  ```
- **Welcome Message** *(replace the default "Welcome to the Chat!" text in the rich-text editor box)*:
  ```text
  Welcome to the Grant & Abstract Coach!

  Paste your draft abstract, Project Summary, Project Narrative, or Specific Aims below (and mention your target funder, such as NSF or NIH). I will audit your structure, flag vague verbs and missing metrics, and give you a concrete revision plan—while keeping 100% of the writing in your own voice.

  How to Attach Companion Skills (Click "+" in the chat bar -> "Skills >"):
  • nsf-project-summary-coach (/nsf-summary) — Audit your draft against NSF PAPPG 1-Page Project Summary rules (Overview, Intellectual Merit, Broader Impacts)
  • nih-project-summary-coach (/nih-summary) — Audit your draft against NIH SF424 rules (30-line Project Summary/Abstract, 2-3 sentence Project Narrative, & Specific Aims)
  • broader-impacts-coach (/impacts) — Get coached on concrete Florida/FSU Broader Impacts activities and an evaluation planning matrix
  • reviewer-critique-simulator (/review) — Run a 3-person Mock Review Panel / Study Section critique
  ```

#### 3. Knowledge & Tools *(Optional)*
You can upload your target agency's solicitation PDF (e.g., an NSF program solicitation or NIH NOFO) here so the agent aligns its coaching and critiques with that program's specific review criteria.

#### 4. Capabilities & Model
In the **Capabilities & Model** tab, configure the toggles and model as follows:

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | **OFF** | Not needed for developmental coaching and structural audits. |
| **Add Files & Images** | **ON** | Allows you to attach draft proposal PDFs or agency solicitation documents directly inside a chat. |
| **Web Search** | **ON** *(Optional)* | Helpful when asking the agent to check current solicitation requirements or regional Florida statistics for Broader Impacts planning. |
| **Generate Artifacts** | **ON** | Displays your diagnostic audit tables, mock study-section critiques, and Broader Impacts planning matrices in a clean side-by-side window. |
| **Model (`Change` button)** | • **OpenAI**: `gpt-5.6-luna` *(Default, set **Reasoning Effort**: `High`)*<br>• **Anthropic**: `claude-sonnet-5` or `claude-opus-4-7` *(set **Creativity**: `Low`)* | High reasoning effort and low creativity keep critiques analytical, specific to your draft text, and aligned with NSF/NIH rules. |

#### 5. Starter Prompts *(Optional)*
In **5. Starter Prompts**, click **Add Starter Prompt** and enter the **Title** and **Prompt** fields below, then click **Create**:

| Title | Prompt |
| :--- | :--- |
| `Coach My NSF Project Summary (/nsf-summary)` | `Run /nsf-summary, /review, and /impacts to coach me on the draft NSF Project Summary I paste next without rewriting my text.` |
| `Coach My NIH Summary & Narrative (/nih-summary)` | `Run /nih-summary on my draft NIH Project Summary, Project Narrative, and Specific Aims to check SF424 compliance, lay readability, and aim independence.` |
| `Mock Panel / Study Section Critique (/review)` | `Run /review on my draft Specific Aims or Project Summary as a skeptical 3-reviewer panel and advise me on how to preempt their critiques.` |
| `Coach My Broader Impacts Plan (/impacts)` | `Run /impacts on my draft to critique my current Broader Impacts idea and help me plan concrete Florida/FSU activities and evaluation metrics.` |

---

### Part 3: Test with Skills in the Preview Pane & Click Create
1. In the **Preview** chat pane on the right side of the Agent Builder (or after clicking **Create**), click the **`+` button** on the left side of the message input bar (`+ Type a message...`) → hover over **`Skills >`** → attach `nsf-project-summary-coach`, `nih-project-summary-coach`, `broader-impacts-coach`, and `reviewer-critique-simulator`.
2. Open [`example-input.md`](./example-input.md), copy either the **NSF** or **NIH** draft prompt into the chat, and compare the coaching output with [`example-output.md`](./example-output.md).
3. Click **Create** at the bottom of the screen to save your **Grant & Abstract Coach** agent!

---

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Core non-ghostwriting coaching persona and 5-part diagnostic checklist |
| [`skills/nsf-project-summary.md`](./skills/nsf-project-summary.md) | Skill (`/nsf-summary`) for auditing and coaching on NSF PAPPG 1-Page Project Summaries |
| [`skills/nih-project-summary.md`](./skills/nih-project-summary.md) | Skill (`/nih-summary`) for auditing and coaching on NIH 30-line Project Summaries, 2–3 sentence Project Narratives, and Specific Aims |
| [`skills/broader-impacts-builder.md`](./skills/broader-impacts-builder.md) | Skill (`/impacts`) for coaching researchers through measurable Broader Impacts & evaluation planning |
| [`skills/reviewer-critique-simulator.md`](./skills/reviewer-critique-simulator.md) | Skill (`/review`) for simulating a 3-person grant review panel / study section |
| [`example-input.md`](./example-input.md) | Sample NSF and NIH draft abstracts to test the agent |
| [`example-output.md`](./example-output.md) | Sample coaching diagnostics for NSF & NIH drafts, mock panel review, and Broader Impacts planning guide |

---

## Modify & Play: Ideas to Try

1. **Compare NSF vs. NIH Coaching on the Same Project**:
   - *Try this*: Paste the same draft into `/nsf-summary` and `/nih-summary` to see how the coach guides you to restructure your text for NSF's 3-heading `Overview / Intellectual Merit / Broader Impacts` format versus NIH's 30-line `Project Summary`, 2–3 sentence lay `Project Narrative`, and independent `Specific Aims`.
2. **Attach an Agency Solicitation / NOFO PDF**:
   - *Try this*: Upload a specific NSF program solicitation or NIH NOFO PDF into your ArtesAI agent's **Step 3: Knowledge & Tools** tab, and ask `/review` to critique your draft specifically against that solicitation's review criteria.
3. **Iterative Re-Review**:
   - *Try this*: Revise your draft in your own words using the **Top 3 Revisions** from `/review`, then paste your revised version back into the chat and ask the 3 simulated reviewers whether your changes resolved their concerns.
4. **Customize for Humanities & Arts Fellowships (NEH / Guggenheim)**:
   - *Try this*: Modify the terminology in `system-prompt.md` from "hypotheses and experimental validation" to "archival sources, theoretical intervention, and chapter organization."
