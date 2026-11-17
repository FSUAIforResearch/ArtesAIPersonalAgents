# FSU Accessibility Reviewer

> **One-Sentence Summary**: Reviews uploaded documents, flyers, web pages, caption files, and social media posts for accessibility under WCAG 2.1 AA, ADA Title II, and FSU Digital Accessibility guidelines—returning a clear rating (`Good` to `Very Bad`) and step-by-step fixes.

[**⬅ Back to Main Catalog**](../README.md)

---

## Overview

Preparing course syllabi, department flyers, PDFs, slides, and web pages to meet WCAG 2.1 Level AA and the ADA Title II rule can feel overwhelming if you aren't an accessibility specialist.

The **FSU Accessibility Reviewer** checks your uploaded Word docs, PDFs, PowerPoints, Excel sheets, Canva flyers, caption files, or HTML/social posts against FSU's Digital Accessibility guides (`digitalaccessibility.fsu.edu`). It rates the file (**Good · Somewhat Good · Neutral · Bad · Very Bad**), flags whether an ADA Title II exception might apply, and provides exact menu-path fixes in the app you are using, plus a checklist of what still requires manual testing.

- **Recommended Model in ArtesAI**: `Anthropic (claude-sonnet-5)` or `OpenAI (gpt-5.6-luna)` (Default)
- **Estimated Setup Time**: ~5 minutes

---

## How to Build This Agent & Its Skills in ArtesAI

In ArtesAI, **create the companion Skills first** under your account **Settings → My Skills** (Part 1). That way, when you build the **Personal Agent** (Part 2), you can immediately attach and test the skills inside the right-hand **Preview** pane before clicking **Create** (Part 3).

### Part 1: Create the Companion Skills First (`Settings → My Skills`)

1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and click **Settings**.
2. Click **My Skills** on the left, then click **`+ New Skill`** in the top-right corner.
3. Open each standard skill file below and copy its parts into the **Create Skill** modal (**Name** = `name:` from the top `---` block, **Description** = `description:` from the top `---` block, leave **Always On** unchecked/`Ad Hoc`, and paste only the Markdown body below the second `---` into the dark editor box):
   - **[`accessibility-standards`](./skills/accessibility-standards.md)**: FSU accessibility rules (ADA Title II + WCAG 2.1 AA, April 26, 2027 compliance date, Sections 504/508, Fla. Stat. 282.603), exceptions, severity levels, and the 5-level rating rubric. Attach on every review.
   - **[`document-review`](./skills/document-review.md)**: Checklists and app-specific menu-path fixes for Microsoft Word (`.docx`), PDF, PowerPoint (`.pptx`), Excel (`.xlsx`), and Canva flyers/infographics.
   - **[`media-web-social`](./skills/media-web-social.md)**: Checklists for web and Canvas pages, prerecorded/live video and audio captions/transcripts, social media posts, and FSU brand color contrast combinations.

---

### Part 2: Create the Personal Agent

#### 0. Launch "Quick Create"
1. In the left maroon FSU sidebar, click **Explore Agents** (or switch to the **Agents** tab).
2. Under **My Agents** (*Agents created by me*), click the **`+ Create`** button next to the **My Agents** heading (or click the dashed **`+ Create`** card).
3. In the **Quick Create** popup box, enter **`FSU Accessibility Reviewer`** as the **Agent Name** and click **`Let's go`**.

#### 1. Instructions (System Prompt)
1. Open [`system-prompt.md`](./system-prompt.md), copy the text, and paste it into the **Specific Instructions** field.
2. **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** to save on context tokens.

#### 2. Name & Identity
In the **Name & Identity** panel, fill in the three fields below (you'll see them update live in the right-hand **Preview** pane):

- **Name**:
  ```text
  FSU Accessibility Reviewer
  ```
- **Short Description**:
  ```text
  Rates the accessibility of your documents, flyers, web pages, and videos (Good to Very Bad) and explains how to fix each problem.
  ```
- **Welcome Message** *(replace the default "Welcome to the Chat!" text in the rich-text editor box)*:
  ```text
  Welcome to the FSU Accessibility Reviewer!

  Upload a Word doc, PDF, PowerPoint, Excel file, Canva flyer, or caption file, or paste in web page HTML or a social post. I'll give it a rating from Good to Very Bad and list what to fix, starting with the biggest problems.

  It helps to tell me what the content is for (course material, public web page, event flyer, form), since that affects whether any ADA Title II exceptions apply.

  How to Attach Companion Skills (Click "+" in the chat bar -> "Skills >"):
  • accessibility-standards — Attach on every review (rules, exceptions, WCAG criteria, and rating rubric)
  • document-review — Checklists and menu-path fixes for Word, PDF, PowerPoint, Excel, and Canva
  • media-web-social — Checklists for web/Canvas pages, video/audio captions, social posts, and FSU brand colors
  ```

#### 3. Knowledge & Tools *(Optional)*
Upload your department's style guide or brand template here if you want the agent to check against department-specific formatting rules as well.

#### 4. Capabilities & Model
In the **Capabilities & Model** tab, configure the toggles and model as follows:

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | **OFF** | Not needed for accessibility audits and fix tables. |
| **Add Files & Images** | **ON** | Lets users upload Word docs, PDFs, slide decks, spreadsheets, and flyer images directly into the chat. |
| **Web Search** | **ON** | Compliance deadlines and FSU guidance evolve (e.g., the DOJ moved the Title II compliance date to April 26, 2027). The system prompt restricts search strictly to policy checks. |
| **Generate Artifacts** | **ON** | Renders the accessibility report and findings table in a clean side-by-side panel. |
| **Model (`Change` button)** | • **Anthropic**: `claude-sonnet-5` *(set **Creativity**: `Low`)* or `claude-opus-4-7` *(for very long/complex files)*<br>• **OpenAI**: `gpt-5.6-luna` *(Default, set **Reasoning Effort**: `Medium`)* | Strong at inspecting long documents and following structured rubrics without inventing findings. |

#### 5. Starter Prompts *(Optional)*
In **5. Starter Prompts**, click **Add Starter Prompt** and enter the **Title** and **Prompt** fields below, then click **Create**:

| Title | Prompt |
| :--- | :--- |
| `Review My Document` | `Review the attached document for accessibility. It's for: [course material / public web page / event flyer / form].` |
| `Check My Flyer` | `Here's an event flyer I plan to post on Instagram and our website. Rate its accessibility and write the alt text and post caption I should use.` |
| `Does an Exception Apply?` | `This PDF was posted on our site in 2023. Does an ADA Title II exception apply, and what would I need to fix if not?` |
| `Check FSU Brand Colors` | `Our slides use FSU Garnet and Gold. Which text/background combinations pass contrast, and what should I change?` |

---

### Part 3: Test with Skills in the Preview Pane & Click Create
1. In the **Preview** chat pane, click the **`+` button** in the message bar → hover over **`Skills >`** → attach `accessibility-standards`, `document-review`, and `media-web-social`.
2. Open [`example-input.md`](./example-input.md), copy and paste the sample syllabus prompt into the chat, and compare the result with [`example-output.md`](./example-output.md) (you should see a **Bad** rating with 4 High findings, starting with Print to PDF).
3. Click **Create** at the bottom of the screen to save your **FSU Accessibility Reviewer** agent!

---

## Files in This Folder

| File | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Core workflow, report format, and honest-limits guardrails |
| [`skills/accessibility-standards.md`](./skills/accessibility-standards.md) | Skill with ADA Title II / WCAG 2.1 AA rules, exceptions, severity definitions, and rating rubric |
| [`skills/document-review.md`](./skills/document-review.md) | Skill with checklists and app menu-path fixes for Word, PDF, PowerPoint, Excel, and Canva |
| [`skills/media-web-social.md`](./skills/media-web-social.md) | Skill with checklists for web/Canvas, video/audio, social media, and FSU brand color contrast |
| [`example-input.md`](./example-input.md) | Sample syllabus prompt with common accessibility issues |
| [`example-output.md`](./example-output.md) | Sample accessibility report showing rating, prioritized findings table, and manual test list |

---

## Modify & Play: Ideas to Try

1. **Stricter or Gentler Grading**:
   - *Try this*: Edit the rubric table in [`skills/accessibility-standards.md`](./skills/accessibility-standards.md) (e.g., make `2+ High = Bad` for high-traffic public-facing pages).
2. **Add Your Department's Template Rules**:
   - *Try this*: Add a section to [`skills/document-review.md`](./skills/document-review.md) with your college or department's own template requirements (fonts, logo placement, required statements).
3. **Canvas-Only Course Content Version**:
   - *Try this*: Trim the agent to focus specifically on Canvas course materials and add FSU Office of Digital Learning (ODL) checklist items and Canvas Ally steps.
4. **Auto-Fix Mode**:
   - *Try this*: Add a rule to `system-prompt.md` so that right after the findings table, the agent rewrites the document's alt text, descriptive link text, and heading hierarchy ready to copy and paste back in.
5. **Batch Audits**:
   - *Try this*: Ask the agent to give a one-line rating per file when several files are uploaded at once, followed by the full findings table for the lowest-rated file.

---

## Sources & FSU Accessibility References
- **FSU Digital Accessibility**: [https://digitalaccessibility.fsu.edu/](https://digitalaccessibility.fsu.edu/) *(FAQ, Documents and Files, Webpages and Content, Design and Color, Video & Audio, Social Media, and Course Content guides)*
- **FSU ADA Title II Compliance FAQ**: [https://digitalaccessibility.fsu.edu/ada-title-ii-compliance-frequently-asked-questions](https://digitalaccessibility.fsu.edu/ada-title-ii-compliance-frequently-asked-questions)
- **FSU College of Medicine Title II Fact Sheet (Exceptions)**: [https://fsumed.teamdynamix.com/TDClient/2884/Portal/KB/ArticleDet?ID=170576](https://fsumed.teamdynamix.com/TDClient/2884/Portal/KB/ArticleDet?ID=170576)
- **DOJ Compliance-Date Extension (Federal Register 2026-07663)**: [https://www.federalregister.gov/documents/2026/04/20/2026-07663/extension-of-compliance-dates-for-nondiscrimination-on-the-basis-of-disability-accessibility-of-web](https://www.federalregister.gov/documents/2026/04/20/2026-07663/extension-of-compliance-dates-for-nondiscrimination-on-the-basis-of-disability-accessibility-of-web)
- **Florida Statute 282.603**: [https://flsenate.gov/Laws/Statutes/2022/0282.603](https://flsenate.gov/Laws/Statutes/2022/0282.603)
