# Lab Onboarding Assistant

> **One-Sentence Summary**: Helps undergraduate and graduate researchers get oriented in a new lab by answering documentation-grounded questions about projects, contacts, tools, onboarding steps, and data-handling rules.

[**⬅ Back to Main Catalog**](../../README.md)

---

## Overview

New researchers often have to piece together information from project guides, checklists, and scattered lab policies. The **Lab Onboarding Assistant** makes these documents searchable through natural-language questions and generates structured onboarding plans while citing its sources and distinguishing official lab requirements from suggestions.

This example uses the **Cypress Computational Research Lab**, a **fully fictional lab with synthetic demo documents** in [`knowledge/`](./knowledge/). No real personnel, credentials, or restricted lab data are included, making it ready to test immediately and easy to swap with your own lab's approved handbook and checklists.

- **Recommended Model in ArtesAI**: `OpenAI (gpt-5.6-luna)` (Default) or `Anthropic (claude-sonnet-5)`
- **Estimated Setup Time**: ~5 minutes

---

## How to Build This Agent & Its Skills in ArtesAI

In ArtesAI, **create the companion Skill first** under your account **Settings → My Skills** (Part 1). That way, when you build the **Personal Agent** (Part 2), you can immediately attach and test the skill inside the right-hand **Preview** pane before clicking **Create** (Part 3).

### Part 1: Create the Companion Skill First (`Settings → My Skills`)

1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and click **Settings**.
2. Click **My Skills** on the left, then click **`+ New Skill`** in the top-right corner.
3. Open the standard skill file below and copy its parts into the **Create Skill** modal (**Name** = `name:` from the top `---` block, **Description** = `description:` from the top `---` block, leave **Always On** unchecked/`Ad Hoc`, and paste only the Markdown body below the second `---` into the dark editor box):
   - **[`onboarding-plan-builder`](./skills/onboarding-plan-builder.md)**: Creates a beginner-friendly one- or two-week research lab onboarding plan (`Day | Task | Contact | Source` table) grounded in the uploaded checklist, clearly separating documented requirements from suggestions.

---

### Part 2: Create the Personal Agent

#### 0. Launch "Quick Create"
1. In the left maroon FSU sidebar, click **Explore Agents** (or switch to the **Agents** tab).
2. Under **My Agents** (*Agents created by me*), click the **`+ Create`** button next to the **My Agents** heading (or click the dashed **`+ Create`** card).
3. In the **Quick Create** popup box, enter **`Lab Onboarding Assistant`** as the **Agent Name** and click **`Let's go`**.

#### 1. Instructions (System Prompt)
1. Open [`system-prompt.md`](./system-prompt.md), copy the text, and paste it into the **Specific Instructions** field.
2. **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** to save on context tokens.

#### 2. Name & Identity
In the **Name & Identity** panel, fill in the three fields below (you'll see them update live in the right-hand **Preview** pane):

- **Name**:
  ```text
  Lab Onboarding Assistant
  ```
- **Short Description**:
  ```text
  Answers new researchers' questions about lab onboarding, projects, contacts, and policies using uploaded lab documents.
  ```
- **Welcome Message** *(replace the default "Welcome to the Chat!" text in the rich-text editor box)*:
  ```text
  Welcome to the Lab Onboarding Assistant!

  Ask what to do in your first week, who to contact, which tools you need, or what your lab's research projects involve. Responses are based strictly on the uploaded lab documents (this demo uses the fictional Cypress Computational Research Lab).

  How to Attach Companion Skills (Click "+" in the chat bar -> "Skills >"):
  • onboarding-plan-builder — Build a structured Day / Task / Contact / Source onboarding plan separating official checklist steps from suggestions
  ```

#### 3. Knowledge & Tools *(Upload from `./knowledge/`)*
Upload the **four synthetic lab files** from [`./knowledge/`](./knowledge/) into **Step 3 — Knowledge & Tools** (do **not** upload `example-input.md` or `example-output.md` as agent knowledge):
- [`knowledge/01_lab_overview.md`](./knowledge/01_lab_overview.md) — Fictional lab focus, team roles/contacts, and weekly meetings
- [`knowledge/02_first_week_checklist.md`](./knowledge/02_first_week_checklist.md) — Official Day 1–5 onboarding checklist
- [`knowledge/03_data_and_security_policy.md`](./knowledge/03_data_and_security_policy.md) — Access and data-handling rules
- [`knowledge/04_atlas_project_guide.md`](./knowledge/04_atlas_project_guide.md) — Synthetic CNN project starter guide and reproducibility rules

#### 4. Capabilities & Model
In the **Capabilities & Model** tab, configure the toggles and model as follows:

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | **OFF** | Not needed for documentation Q&A and onboarding checklists. |
| **Add Files & Images** | **ON** | Lets users attach supplemental project notes or error logs during chat. |
| **Web Search** | **OFF** | Keeps answers strictly grounded in the uploaded lab documents without pulling in outside rules. |
| **Generate Artifacts** | **ON** | Renders printable Day 1–Day 10 onboarding tables and checklists in a clean side-by-side panel. |
| **Model (`Change` button)** | • **OpenAI**: `gpt-5.6-luna` *(Default, set **Reasoning Effort**: `Medium`)*<br>• **Anthropic**: `claude-sonnet-5` *(set **Creativity**: `Low`)* | Low creativity keeps answers grounded in the uploaded knowledge files and prevents invented contacts, links, or policies. |

#### 5. Starter Prompts *(Optional)*
In **5. Starter Prompts**, click **Add Starter Prompt** and enter the **Title** and **Prompt** fields below, then click **Create**:

| Title | Prompt |
| :--- | :--- |
| `My First Week` | `I'm a new undergraduate researcher. What should I do during my first week, and who do I ask for access?` |
| `Explain My Project` | `Explain Project Atlas to someone with no machine learning background.` |
| `Data Access & Security` | `Who approves access to datasets, and what rules should I follow?` |
| `Build a 2-Week Onboarding Plan` | `I'm joining Project Atlas. Create a two-week onboarding plan separating the official checklist from suggested next steps.` |

---

### Part 3: Test with Skills in the Preview Pane & Click Create
1. In the **Preview** chat pane, click the **`+` button** in the message bar → hover over **`Skills >`** → attach `onboarding-plan-builder` (or test basic Q&A without it).
2. Open [`example-input.md`](./example-input.md), copy and paste the sample questions into the chat, and compare the replies with [`example-output.md`](./example-output.md).
3. Click **Create** at the bottom of the screen to save your **Lab Onboarding Assistant** agent!

---

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Always-on rules for grounded lab Q&A, source citations, and privacy guardrails |
| [`skills/onboarding-plan-builder.md`](./skills/onboarding-plan-builder.md) | Skill for building a `Day / Task / Contact / Source` onboarding table |
| [`knowledge/01_lab_overview.md`](./knowledge/01_lab_overview.md) | Fictional lab focus, team roles/contacts, and meeting schedule |
| [`knowledge/02_first_week_checklist.md`](./knowledge/02_first_week_checklist.md) | Day 1–5 new-researcher onboarding checklist |
| [`knowledge/03_data_and_security_policy.md`](./knowledge/03_data_and_security_policy.md) | Fictional data access, storage, and security policy |
| [`knowledge/04_atlas_project_guide.md`](./knowledge/04_atlas_project_guide.md) | Synthetic microscopy CNN starter guide and evaluation workflow |
| [`example-input.md`](./example-input.md) | Five sample prompts covering Week 1 tasks, project explanation, unknown info, security, and 2-week planning |
| [`example-output.md`](./example-output.md) | Sample grounded responses and 2-week onboarding table |

---

## Modify & Play: Ideas to Try

1. **Swap in Your Own Lab's Approved Handbook**:
   - *Try this*: Replace the four fictional [`knowledge/`](./knowledge/) files with your own lab's approved onboarding checklist, safety procedures, instrument SOPs, and project guides (always review documents to remove passwords, unpublished IP, or restricted data before uploading).
2. **Adapt for a Wet Lab, Fieldwork Team, or Humanities Group**:
   - *Try this*: Customize the starter prompts and knowledge documents for EHS/biosafety training and reagent inventories (wet lab), field gear and IRB consent protocols (fieldwork), or archival citation and transcription conventions (humanities).
3. **Add a Lab Jargon & Acronym Glossary**:
   - *Try this*: Upload a `05_lab_glossary.md` file defining common acronyms, file paths, and software tools used in your group so new undergraduate researchers can ask *"What does X mean in our lab?"*
4. **Test the Hallucination Guardrail**:
   - *Try this*: Ask the agent *"What is the lab Wi-Fi password, and has tomorrow's meeting moved to 3 p.m.?"* Watch how it refuses to guess and points you to the documented lab manager (**Jordan Lee**).
