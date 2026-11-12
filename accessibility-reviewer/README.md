# FSU Accessibility Reviewer

**Focus area:** Accessibility & Compliance · **Difficulty:** Beginner
**Repo folder name:** `accessibility-reviewer/`

Upload any document, flyer, web page, caption file, or social post and get an accessibility rating (**Good · Somewhat Good · Neutral · Bad · Very Bad**) plus a table of specific fixes, based on WCAG 2.1 AA, the ADA Title II rule, and FSU's Digital Accessibility guides.

## What's in this folder
| File | What it is |
|---|---|
| `README.md` | This setup guide |
| `system-prompt.md` | Paste into **Specific Instructions** |
| `skills/accessibility-standards.md` | Rules, exceptions, WCAG criteria, rating rubric |
| `skills/document-review.md` | Word, PDF, PowerPoint, Excel, Canva checklists |
| `skills/media-web-social.md` | Web/Canvas, video/audio, social media, FSU brand colors |
| `example-input.md` | Sample prompt (a syllabus with problems) |
| `example-output.md` | What a good response looks like |

## Part 1: Create the skills (Settings → My Skills → + New Skill)
Create each of the three files in `skills/`:
| Name | Always On |
|---|---|
| `accessibility-standards` | Unchecked (Ad Hoc) |
| `document-review` | Unchecked (Ad Hoc) |
| `media-web-social` | Unchecked (Ad Hoc) |

Copy **Name** and **Description** from each file's frontmatter (descriptions are under 300 characters), and paste everything below the second `---` into **Skill Instructions**.

## Part 2: Build the agent
**Agent Name:** FSU Accessibility Reviewer

**Step 1: Instructions.** Paste `system-prompt.md` into **Specific Instructions** and clear the default Platform Instructions.

**Step 2: Name & Identity**
- **Short Description:** Rates the accessibility of your documents, flyers, web pages, and videos (Good to Very Bad) and explains how to fix each problem.
- **Welcome Message:**
  > Hi! I review documents and web content for accessibility.
  > Upload a Word doc, PDF, PowerPoint, Excel file, Canva flyer, or caption file, or paste in web page HTML or a social post. I'll give it a rating from Good to Very Bad and list what to fix, starting with the biggest problems.
  > Before you start, attach the skills (+ → Skills): `accessibility-standards`, plus `document-review` for files or `media-web-social` for web, video, and social content.
  > It helps to tell me what the content is for (course material, public page, event flyer), since that affects whether any exceptions apply.

**Step 3: Knowledge & Tools.** Optional: upload your department's style guide or brand template.

**Step 4: Capabilities & Model**
| Setting | Recommendation | Why |
|---|---|---|
| Image Creation | **OFF** | Not needed |
| Add Files & Images | **ON** | Users need to upload their documents |
| Web Search | **ON** | Deadlines and FSU guidance change (the DOJ moved the Title II date to April 26, 2027). The prompt limits search to policy checks |
| Generate Artifacts | **ON** | The report and findings table read better in the side pane |
| Model | **claude-sonnet-5** (or gpt-5.4) | Strong at reading long documents and following a rubric. Use claude-opus-4-7 for very long or complex files |

**Step 5: Starter Prompts**
| Title | Prompt |
|---|---|
| Review my document | Review the attached document for accessibility. It's for: [course material / public web page / event flyer / form]. |
| Check my flyer | Here's an event flyer I plan to post on Instagram and our website. Rate its accessibility and write the alt text and post caption I should use. |
| Does this need fixing? | This PDF was posted on our site in 2023. Does an ADA Title II exception apply, and what would I need to fix if not? |
| Fix my colors | Our slides use FSU Garnet and Gold. Which text/background combinations pass contrast, and what should I change? |

## Part 3: Test
In the Preview pane, click **+ → Skills** and attach all three skills. Paste the prompt from `example-input.md` and compare with `example-output.md`. You should see a **Bad** rating (4 High findings, with Print to PDF at the top). Then click **Create**.

## Modify & Play
- **Stricter or gentler grading:** edit the rubric table in `accessibility-standards` (e.g., make 2+ High = Bad for public-facing pages).
- **Your department's rules:** add a section to `document-review` with your own template requirements (fonts, logo placement, required statements).
- **Canvas-only version:** trim the agent to course content and add ODL's checklist and Ally steps.
- **Auto-fix mode:** add a rule that after the report, the agent rewrites the document's alt text, link text, and headings so the user can paste them back in.
- **Batch audits:** ask for a one-line rating per file when several files are uploaded, then the details for the worst one.

## Catalog row (add to the root README)
| Agent | Focus Area | Included Skills | Difficulty |
|---|---|---|---|
| FSU Accessibility Reviewer | Accessibility & Compliance | • accessibility-standards<br>• document-review<br>• media-web-social | Beginner |

## Sources
- FSU Digital Accessibility: https://digitalaccessibility.fsu.edu/ (FAQ, Documents and Files, Webpages and Content, Design and Color, Video & Audio, Social Media, Course Content guides)
- FSU ADA Title II FAQ: https://digitalaccessibility.fsu.edu/ada-title-ii-compliance-frequently-asked-questions
- FSU College of Medicine Title II fact sheet (exceptions): https://fsumed.teamdynamix.com/TDClient/2884/Portal/KB/ArticleDet?ID=170576
- DOJ compliance-date extension (Federal Register 2026-07663): https://www.federalregister.gov/documents/2026/04/20/2026-07663/extension-of-compliance-dates-for-nondiscrimination-on-the-basis-of-disability-accessibility-of-web
- Campus Technology on the extension: https://campustechnology.com/articles/2026/04/27/doj-extends-deadline-for-ada-title-ii-compliance.aspx
- Florida Statute 282.603: https://flsenate.gov/Laws/Statutes/2022/0282.603
