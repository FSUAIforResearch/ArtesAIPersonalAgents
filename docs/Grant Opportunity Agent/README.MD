# FSU Grant Opportunity Scout

## Overview

The FSU Grant Opportunity Scout helps faculty:

1. Find current funding opportunities that may fit their research.
2. Compare a research project with a specific grant.
3. Analyze official grant guidelines or a solicitation.

Faculty can begin with a short, non-confidential research description. They do not need to upload raw research data, a complete proposal, or a CV to conduct an initial funding search.

---

## Package Contents

This agent package includes:

- `README.md`: Step-by-step setup and testing instructions
- `system-prompt.md`: Main instructions to paste into the agent's Specific Instructions field
- `skills/research-profile-builder.md`
- `skills/grant-opportunity-scout.md`
- `skills/grant-fit-evaluator.md`
- `skills/funding-announcement-analyzer.md`
- `skills/grant-project-matcher.md`
- `example-input.md`: Sample prompt for testing
- `example-output.md`: Example of the expected response structure

---

# Part 1: Create the Five Skills First

Create the skills before creating the personal agent so they are available to use in the finished agent.

## Open My Skills

1. Sign in to ArtesAI.
2. Click your Profile or Account box at the bottom-left of the maroon FSU sidebar.
3. Select **Settings**.
4. In the Account sidebar, select **My Skills**.
5. Click **+ New Skill** in the top-right corner.

## Create Each Skill

Repeat the following steps for all five files in the `skills/` folder:

1. Open the skill `.md` file.
2. Locate the YAML frontmatter at the top of the file, between the two `---` lines.
3. Copy the value after `name:` into the ArtesAI **Name** field.
4. Copy the value after `description:` into the ArtesAI **Description** field.
5. Leave **Always On** unchecked so the skill remains Ad Hoc.
6. Copy everything below the second `---` line into the dark **Skill Instructions** editor.
7. Click **Create**.

## Skills to Create

Create these five skills:

1. `research-profile-builder`
2. `grant-opportunity-scout`
3. `grant-fit-evaluator`
4. `funding-announcement-analyzer`
5. `grant-project-matcher`

## Why the Skills Should Remain Ad Hoc

ArtesAI limits the number of Always On skills available across an account. These skills are specific to this agent, so keeping them Ad Hoc preserves the account's Always On slots and allows the agent to use only the relevant skill for each request.

---

# Part 2: Create the Personal Agent

## Open Quick Create

1. In the left maroon FSU sidebar, select **Explore Agents** or open the **Agents** tab.
2. Scroll to **My Agents** or **Agents created by me**.
3. Click **+ Create** next to My Agents or select the dashed **+ Create** card.
4. In the Quick Create popup, enter the following name:

**FSU Grant Opportunity Scout**

5. Click **Let's go**.

---

# Part 3: Complete the Five-Step Agent Builder

## Step 1: Instructions

### Specific Instructions

1. Open `system-prompt.md`.
2. Copy the full text.
3. Paste it into the **Specific Instructions** field.

### Platform Instructions

If ArtesAI allows the field to be edited, clear the default Platform Instructions so the agent stays focused on the grant workflow and does not spend context-window space on unnecessary generic instructions.

Do not paste the system prompt into both fields.

## Step 2: Name and Identity

### Name

Confirm that the name is:

**FSU Grant Opportunity Scout**

### Short Description

Paste:

Helps FSU faculty find relevant funding opportunities, evaluate project fit, and understand grant guidelines using public web sources and non-confidential materials.

### Welcome Message

Replace the default welcome text with the following:

# Welcome to the FSU Grant Opportunity Scout

Find funding opportunities that may fit your research, check whether a project aligns with a specific grant, or turn lengthy grant guidelines into a clear action checklist.

You can start with a short, non-confidential description of your research. You do not need to upload research data, a full proposal, or a CV.

## Choose a starting point

### Find Funding

Describe what you research and what you want the funding to support. No upload is required.

### Check My Project's Fit

Share a short, non-confidential project summary and provide the grant link or upload the grant guidelines or solicitation.

### Analyze a Grant

Provide a grant link or upload the grant guidelines or solicitation. The agent will identify eligibility rules, deadlines, funding limits, required materials, review criteria, restrictions, and unresolved questions.

## Information you may provide

- A two-to-five-sentence research description
- What the funding would support
- Field or discipline
- Career stage, if relevant
- Approximate funding target
- Preferred sponsors
- Desired deadline window
- A project abstract or generalized summary
- A grant link or uploaded official grant document

## Do not upload just to improve a search

- Raw research data
- Participant-level information
- Student records
- Protected health information
- Proprietary datasets
- Confidential partner information
- Export-controlled or sponsor-restricted material
- Passwords or credentials

If an official sponsor page blocks access, the agent will look for an accessible official PDF, Grants.gov record, or another official source. If important details still cannot be verified, it will ask you to upload the official grant document rather than guessing.

This agent supports preliminary funding discovery and analysis. It does not guarantee eligibility, replace the current official grant guidelines, or replace review by the appropriate FSU research administration office.

## Step 3: Knowledge and Tools

### Static Knowledge Files

No permanent knowledge file is required for the initial version.

Do not permanently upload a single grant solicitation unless the agent is intended to specialize in that specific program. Grant guidelines, deadlines, and requirements change, so the agent should normally use current web sources or documents uploaded during the conversation.

Optional permanent files could include:

- Public department research-area descriptions
- A non-confidential sponsor glossary
- Public FSU research-administration guidance
- A department-approved grant-review checklist

Do not permanently upload raw data, confidential proposals, participant records, protected information, or sponsor-restricted content.

### Attach or Enable the Skills

After completing the Agent Builder:

In the preview chat, locate the plus button to the left to add or select skills.

Add these five skills:

research-profile-builder
grant-opportunity-scout
grant-fit-evaluator
funding-announcement-analyzer
grant-project-matcher

Confirm that all five skills are available in the Test Window before testing the agent.

Keep all five skills Ad Hoc rather than Always On.

## Step 4: Capabilities and Model

Use these settings for the initial version:

| Setting | Selection | Reason |
|---|---|---|
| Image Creation | Off | The grant workflow does not require generated images. |
| Add Files & Images | On | Faculty may need to upload grant guidelines, abstracts, or redacted project summaries. |
| Web Search | On | The agent must locate current public funding opportunities and official sources. |
| Generate Artifacts | Off initially | Keep the first version focused. Turn it on later if downloadable briefs or checklists are needed. |

### Model Selection

Choose the strongest current reasoning model available in ArtesAI that supports web searching and document analysis.

Before launch, test the selected model for:

- Accurate extraction from long PDF solicitations
- Compliance with official-source requirements
- Correct handling of blocked websites
- Resistance to inventing deadlines, award amounts, or eligibility rules
- Consistent use of verification labels

Do not select a model solely because it responds quickly. Source discipline and document accuracy matter more for this agent.

## Step 5: Starter Prompts

Add the following starter prompts.

### Starter Prompt 1

**Title:** Find funding for my research

**Prompt:**

I want to find funding opportunities. Ask me only for the minimum non-confidential information you need, then search for relevant current grants and explain the strongest matches.

### Starter Prompt 2

**Title:** Check whether my project fits a grant

**Prompt:**

I want to compare a project with a specific grant. Ask me for a short non-confidential project summary and the grant link or official grant document.

### Starter Prompt 3

**Title:** Analyze a grant

**Prompt:**

I want to understand a grant's official guidelines. Ask me to provide the link or upload the solicitation, then identify eligibility, deadlines, funding limits, required materials, review criteria, restrictions, and questions to confirm.

### Starter Prompt 4

**Title:** What should I provide?

**Prompt:**

Tell me the minimum information needed for each workflow and what sensitive or proprietary material I should not upload.

After adding the prompts, click **Create**, **Save**, or **Update**, depending on the button shown in ArtesAI.

---

# Part 4: How the Agent Should Route Requests

The five skills are modular. The agent should not run all five for every request.

## Find Funding

Use:

1. `research-profile-builder`
2. `grant-opportunity-scout`
3. `grant-fit-evaluator` only for the strongest results when enough official information is available

## Check My Project's Fit

Use:

1. `funding-announcement-analyzer`
2. `research-profile-builder` only if the project description needs structure
3. `grant-fit-evaluator`
4. `grant-project-matcher`

## Analyze a Grant

Use:

1. `funding-announcement-analyzer`

---

# Part 5: What Faculty Need to Provide

## To Find Funding

Required:

1. A short, non-confidential research description
2. What the funding should support

Optional:

- Field or discipline
- Career stage
- Desired funding range
- Preferred sponsor type
- Deadline window
- Collaborator or partnership preferences
- A CV, biosketch, abstract, or generalized project summary

Example response template for faculty:

“I study [research topic], and I need funding for [activities or expenses].”

## To Check Project Fit

Required:

1. A short, non-confidential project summary
2. A grant link or uploaded official grant document

Faculty may use redacted or generalized materials. A complete proposal and raw research data are not required.

## To Analyze a Grant

Required:

1. A grant link, uploaded official grant document, or pasted official text

A research description is not required unless the faculty member also wants a project-fit analysis.

---

# Part 6: Verification and Blocked-Site Behavior

The agent should use the following verification labels:

- **Verified:** Key facts were confirmed from a current, accessible official source.
- **Partially verified:** The opportunity appears valid, but one or more important facts could not be confirmed from an accessible official source.
- **Grant document upload required:** Reliable analysis cannot continue until the faculty member provides the official grant guidelines or solicitation.

When an official page is blocked or incomplete, the agent should:

1. Avoid repeatedly retrying the same blocked page.
2. Look for an official solicitation PDF.
3. Look for an official Grants.gov record when relevant.
4. Look for another official agency program page or announcement.
5. Clearly identify what remains unverified.
6. Ask the faculty member to upload the official document when necessary.

The agent must not guess deadlines, award amounts, eligibility, page limits, review criteria, or application requirements.

---

# Part 7: Test the Agent

Start a new conversation for each test. Do not rely only on the conversation used while building the agent.

## Test 1: Minimal Research Description

Enter:

“I study pufferfish.”

Expected behavior:

- The agent asks what aspect of pufferfish the faculty member studies.
- The agent asks what the funding should support.
- It may provide a short fill-in-the-blank response template.
- It does not add an unnecessary FSU Context section.

## Test 2: Complete Initial Request

Enter:

“I study pufferfish toxicology, especially how environmental conditions affect toxin production. I need funding for sequencing, laboratory supplies, animal care, and graduate research assistance.”

Expected behavior:

- The agent does not ask for a CV, proposal, or dataset.
- It proceeds to a web search.
- It returns a focused shortlist rather than a long link dump.
- It distinguishes verified and unverified information.

## Test 3: Blocked Website

Provide a sponsor link that the agent cannot access.

Expected behavior:

- It looks for an official PDF, Grants.gov record, or another official agency page.
- It does not repeatedly retry the same page.
- It asks for an uploaded official document if key information remains unavailable.

## Test 4: Uploaded Grant Guidelines

Upload a current public solicitation PDF and ask the agent to analyze it.

Expected behavior:

- It extracts eligibility, deadlines, funding limits, required documents, review criteria, restrictions, and submission requirements.
- It identifies page or section locations when available.
- It distinguishes required, optional, encouraged, prohibited, and unstated items.

## Test 5: Project-to-Grant Fit

Provide a project summary and current official grant document.

Expected behavior:

- It maps the project to sponsor priorities.
- It identifies strong alignment, framing opportunities, substantive gaps, and eligibility risks.
- It ends with Pursue, Investigate further, Monitor, or Do not pursue.
- It does not use a numerical fit score.

## Test 6: Sensitive Data Offered

Enter:

“I can upload my participant-level dataset if that would help.”

Expected behavior:

- The agent says the dataset is unnecessary for funding discovery.
- It requests only a generalized, non-confidential research description.

## Test 7: Prior-Year Solicitation

Provide an older solicitation and ask about current deadlines.

Expected behavior:

- The agent clearly identifies the document as prior-year material.
- It does not present old dates, award limits, or requirements as current.
- It searches for a current official source or marks the current details unverified.

## Test 8: Clearly Ineligible Opportunity

Provide a grant restricted to an applicant type that does not include the faculty member or institution.

Expected behavior:

- The agent identifies the verified eligibility conflict.
- It recommends Do not pursue or Investigate further if the rule is ambiguous.
- It does not soften a confirmed fatal eligibility issue into a strong match.

---

# Part 8: Quality Checklist Before Sharing

Do not share the agent with faculty until it consistently:

- Accepts a short research description without requiring uploads
- Avoids requesting proprietary data
- Searches current public sources
- Prefers official sponsor information
- Identifies closed and archived opportunities
- Avoids duplicate opportunities
- Uses verification labels correctly
- Does not invent missing facts
- Uses blocked-site fallbacks
- Produces concise, faculty-friendly results
- Avoids the generic FSU Context section
- Mentions FSU only when institution-specific information materially matters
- Preserves helpful examples and fill-in-the-blank placeholders
- Recommends final confirmation against the official solicitation and through appropriate FSU research administration channels

---

# Part 9: Pilot Plan

Pilot the agent with three to five faculty members from different disciplines.

A useful pilot group may include:

- One STEM faculty member
- One social-science faculty member
- One humanities faculty member
- One early-career faculty member
- One experienced grant applicant

Ask each participant to complete one real funding-related task and answer:

1. Were the opportunities relevant?
2. Did the agent reduce search or review time?
3. Were the verification labels understandable?
4. Did the agent ask for too much information?
5. Did any response create false confidence?
6. What information was missing?
7. Would the faculty member use the agent again?

The primary success measure is not the number of grants returned. It is whether the agent helps a faculty member identify at least one opportunity worth investigating while reducing search and review effort.

---

# Part 10: Modify and Play Ideas

After the general version works reliably, consider these customizations.

## Department-Specific Versions

Create versions tailored to:

- Engineering
- Medicine or health research, while continuing to follow ArtesAI data restrictions
- Social sciences
- Arts and humanities
- Education
- Marine and environmental research

Adjust sponsor vocabulary and examples without weakening official-source or privacy safeguards.

## Early-Career Funding Mode

Add a workflow that prioritizes opportunities with verified early-career, new-investigator, or first-award criteria. Do not label an opportunity early-career unless the current official guidelines confirm it.

## Equipment Funding Mode

Prioritize instrumentation, shared research infrastructure, laboratory equipment, computing resources, and facility-upgrade programs.

## Foundation Funding Mode

Add public foundation opportunities while retaining the rule that foundation summaries and aggregators are not authoritative for critical requirements.

## Internal Funding Mode

If approved internal sources become accessible, create a separate skill for current FSU internal funding. Keep internal and external opportunities clearly labeled.

## Grant Compliance Checker

Create a future skill that compares a draft application package with the verified solicitation requirements and produces a missing-item checklist.

## Downloadable Briefs

If Generate Artifacts is enabled later, allow the agent to create a downloadable opportunity brief or application checklist. The brief should include the official source, verification date, and unresolved questions.

## Sponsor-Specific Versions

Create specialized workflows for sponsors such as NSF, NIH, NEH, NASA, NOAA, DOE, USDA, or the U.S. Department of Education. Keep the general scout available for interdisciplinary searches.

---

# Troubleshooting

## The Agent Does Not Search the Web

- Confirm **Web Search** is on.
- Start a new conversation after changing settings.
- Confirm the request asks the agent to find current opportunities.

## The Agent Does Not Use the Skills

- Confirm all five skills exist under the same ArtesAI account.
- Confirm the skills are attached or available to the agent.
- Keep the skills Ad Hoc.
- Confirm `system-prompt.md` contains the skill-routing section.
- Start a new conversation after updating the agent.

## The Agent Keeps Adding “FSU Context”

- Confirm the latest system prompt is saved.
- Confirm the system prompt contains the explicit prohibition against an FSU Context heading.
- Clear default Platform Instructions if the interface permits it.
- Start a new conversation because an existing conversation may retain earlier behavior.

## The Agent Gives Too Many Results

Confirm the system prompt requires a focused shortlist of approximately three to seven credible opportunities and prohibits padding the results with weak matches.

## The Agent Guesses Missing Details

- Confirm the source-verification and blocked-site rules are present.
- Test with another strong reasoning model.
- Require `Not verified` when official evidence is unavailable.

## The Agent Requests Too Much Information

Confirm the minimum-input and follow-up-question rules are included. For a basic search, it should require only a short research description and what the funding should support.

---

# Final Scope Statement

The FSU Grant Opportunity Scout supports preliminary funding discovery, grant-guideline analysis, and project-fit screening. It does not guarantee eligibility or funding, replace the current official grant solicitation, certify institutional approval, or replace review by the appropriate FSU research administration office.