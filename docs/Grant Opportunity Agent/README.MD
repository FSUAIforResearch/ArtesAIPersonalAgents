 FSU Grant Opportunity Scout

## What This Agent Does

The FSU Grant Opportunity Scout helps faculty:

- Find current funding opportunities relevant to their research.
- Compare a research project with a specific grant.
- Analyze grant guidelines for eligibility, deadlines, funding limits, required materials, review criteria, and restrictions.

Faculty can begin with a short, non-confidential description of their research and what they want the funding to support. Raw research data is not required.

## Files Included

- `README.md` - Setup instructions
- `system-prompt.md` - Agent instructions
- `example-input.md` - Sample inputs for testing
- `example-output.md` - Example expected output
- `skills/`
  - `research-profile-builder.md`
  - `grant-opportunity-scout.md`
  - `grant-fit-evaluator.md`
  - `funding-announcement-analyzer.md`
  - `grant-project-matcher.md`
  
  # Setup

## 1. Create the Skills

Before creating the agent:

1. Open ArtesAI.
2. Go to **Profile / Account → Settings → My Skills**.
3. Click **+ New Skill**.
4. Create each of the five skills in the `skills/` folder.

For each skill:

- **Name:** Copy the `name:` value from the YAML frontmatter.
- **Description:** Copy the `description:` value.
- **Always On:** Leave unchecked so the skill remains Ad Hoc.
- **Skill Instructions:** Copy everything below the second `---` line.

Create:

1. `research-profile-builder`
2. `grant-opportunity-scout`
3. `grant-fit-evaluator`
4. `funding-announcement-analyzer`
5. `grant-project-matcher`

## 2. Create the Personal Agent

1. Go to **Explore Agents** or the **Agents** tab.
2. Find **My Agents**.
3. Click **+ Create**.
4. In Quick Create, enter:

**FSU Grant Opportunity Scout**

5. Click **Let's go**.

## 3. Follow the 5-Step Agent Builder

### Step 1 - Instructions

Open `system-prompt.md`.

Copy the entire file and paste it into **Specific Instructions**.

If permitted, clear the default **Platform Instructions**.

### Step 2 - Name & Identity

**Name:**

FSU Grant Opportunity Scout

**Short Description:**

Helps FSU faculty find relevant funding opportunities, evaluate project fit, and understand grant guidelines using public web sources and non-confidential materials.

**Welcome Message:**

# Welcome to the FSU Grant Opportunity Scout

Find funding opportunities that may fit your research, check whether a project aligns with a specific grant, or turn lengthy grant guidelines into a clear action checklist.

You can start with a short, non-confidential description of your research. You do not need to upload research data, a full proposal, or a CV.

### Find Funding

Describe what you research and what you want the funding to support. No upload is required.

### Check My Project's Fit

Share a short, non-confidential project summary and provide the grant link or upload the grant guidelines or solicitation.

### Analyze a Grant

Provide a grant link or upload the grant guidelines or solicitation.

### Step 3 - Knowledge & Tools

No permanent knowledge files are required for the initial version.

Faculty can upload grant guidelines or non-confidential project materials during a conversation when needed.

### Step 4 - Capabilities & Model

Set:

- **Image Creation:** Off
- **Add Files & Images:** On
- **Web Search:** On
- **Generate Artifacts:** Off initially

Select a strong reasoning model that supports web search and document analysis.

### Step 5 - Starter Prompts

**Find funding for my research**

I want to find funding opportunities. Ask me only for the minimum non-confidential information you need, then search for relevant current grants and explain the strongest matches.

**Check whether my project fits a grant**

I want to compare a project with a specific grant. Ask me for a short non-confidential project summary and the grant link or official grant document.

**Analyze a grant**

I want to understand a grant's official guidelines. Ask me to provide the link or upload the solicitation, then identify eligibility, deadlines, funding limits, required materials, review criteria, restrictions, and questions to confirm.

## 4. Add the Skills in the Test Window

After completing the five-step Agent Builder:

1. Open the agent's **Test Window**.
2. In the Test Window chat, select the option to add or choose skills.
3. Add:
   - `research-profile-builder`
   - `grant-opportunity-scout`
   - `grant-fit-evaluator`
   - `funding-announcement-analyzer`
   - `grant-project-matcher`
4. Confirm that all five skills are available.
5. Keep the skills Ad Hoc.

## 5. Test the Agent

Use the sample scenarios in `example-input.md`.

Use `example-output.md` as a reference for what a successful response should look like.