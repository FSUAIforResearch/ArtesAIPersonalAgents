# Lab Onboarding Assistant

> **One-Sentence Summary:** Helps undergraduate and graduate researchers get oriented in a new lab by answering documentation-grounded questions about projects, contacts, tools, onboarding steps, and data-handling rules.

[**⬅ Back to Main Catalog**](../README.md)

---

## Overview

New researchers often have to piece together information from project guides, checklists, and scattered lab policies. The **Lab Onboarding Assistant** makes these documents searchable through natural-language questions and can generate an onboarding plan while citing its sources and distinguishing official rules from suggestions.

This example uses the **Cypress Computational Research Lab**, a **fully fictional lab with synthetic demo documents**. No real personnel, credentials, or restricted lab data are included. It is suitable for a faculty showcase across disciplines.

- **Recommended Model in ArtesAI:** OpenAI default model (or another available conversational model)
- **Estimated Setup Time:** ~5–10 minutes
- **Skills:** Optional `onboarding-plan-builder` for structured plans; the basic Q&A agent works without it.

---

## How to Build This Agent in ArtesAI

### Part 1: Optional Companion Skill (`Settings → My Skills`)

1. Click your profile in the FSU sidebar → **Settings** → **My Skills** → **+ New Skill**.
2. Open [`skills/onboarding-plan-builder.md`](./skills/onboarding-plan-builder.md).
3. Use the YAML `name:` and `description:` values for the corresponding fields. Leave **Always On** unchecked (`Ad Hoc`). Copy only the Markdown below the second `---` into **Skill Instructions** and click **Create**.

This skill is optional; you can demonstrate all the basic questions with only the system prompt and knowledge pack.

### Part 2: Create the Personal Agent

1. Open **Explore Agents → My Agents → + Create**. Enter **Lab Onboarding Assistant**.
2. Under **Instructions**, paste [`system-prompt.md`](./system-prompt.md) into **Specific Instructions**.
3. Under **Name & Identity**, use:
   - **Name:** `Lab Onboarding Assistant`
   - **Short Description:** `Answers new researchers' questions about lab onboarding, projects, contacts, and policies using uploaded lab documents.`
   - **Welcome Message:**

     > Welcome to the Lab Onboarding Assistant! Ask what to do in your first week, who to contact, which tools you need, or what your lab's research projects involve. Responses are based on the uploaded lab documents. This demo uses a fictional research lab.

4. In **Knowledge & Tools**, upload **the four files in [`knowledge/`](./knowledge/)**. Do **not** upload `example-input.md` or `example-output.md` as agent knowledge.
5. In **Capabilities & Model**, select an available conversational model and use:

   | Capability | Setting | Reason |
   | :--- | :--- | :--- |
   | Image Creation | Off | Not necessary |
   | Add Files & Images | On | Supports supplemental documents |
   | Web Search | Off | Keeps answers grounded in lab-provided documents |
   | Generate Artifacts | On | Helpful for printable onboarding plans |

6. Suggested **Starter Prompts**:

   | Title | Prompt |
   | :--- | :--- |
   | My First Week | I'm a new undergraduate researcher. What should I do during my first week? |
   | Explain My Project | Explain Project Atlas to someone with no machine learning background. |
   | Data Access | Who approves access to datasets, and what rules should I follow? |

### Part 3: Test and Save

1. Ask the questions in [`example-input.md`](./example-input.md) in the Preview pane. If desired, attach the optional skill via **+ → Skills** before asking for a plan.
2. Compare the replies with [`example-output.md`](./example-output.md): expect document citations and refusal to invent missing details.
3. Click **Create** to save the agent.

---

## Files in This Folder

| Path | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Always-on rules for grounded lab help |
| [`skills/onboarding-plan-builder.md`](./skills/onboarding-plan-builder.md) | Optional structured planning skill |
| [`knowledge/01_lab_overview.md`](./knowledge/01_lab_overview.md) | Fictional lab focus, team, contacts, and meetings |
| [`knowledge/02_first_week_checklist.md`](./knowledge/02_first_week_checklist.md) | Official-for-demo Day 1–5 onboarding checklist |
| [`knowledge/03_data_and_security_policy.md`](./knowledge/03_data_and_security_policy.md) | Fictional access and data-handling rules |
| [`knowledge/04_atlas_project_guide.md`](./knowledge/04_atlas_project_guide.md) | Synthetic CNN project guide and evaluation workflow |
| [`example-input.md`](./example-input.md) | Reproducible sample questions, including adversarial tests |
| [`example-output.md`](./example-output.md) | Illustrative grounded answers and expected behavior |

---

## Demo: What to Show Faculty

1. **Quick lookup:** "Who should I contact to get started?" → names the documented lab manager and source.
2. **Explain a project:** "Explain Project Atlas to a beginner." → makes research accessible outside the field.
3. **Build a plan:** "Create a two-week Atlas onboarding plan." → separates documented tasks from suggestions.
4. **Safety:** "What's the lab Wi-Fi password?" → says the answer is not documented instead of fabricating it.

## Modify & Play

- Replace the fictional [`knowledge/`](./knowledge/) files with your own **approved** lab handbook, safety procedures, onboarding checklist, and project notes.
- Change the agent prompt to target a wet lab, fieldwork group, humanities research team, or computational lab.
- Add a lab-specific vocabulary guide or recurring FAQ as additional knowledge.
- For real deployment, review documents for secrets, sensitive data, personal information, and sharing permissions **before** upload.

## Limitations

This is a document-grounded assistant, not an access-provisioning system. It cannot grant permissions, verify schedule changes, or guarantee that a document is the latest revision. Always confirm access and security-sensitive actions with a human lab contact.
