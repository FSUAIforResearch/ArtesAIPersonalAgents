---
name: funding-opportunity-finder
description: Find and verify current funding opportunities from a short, non-confidential research description. Use for /find-funding or grant discovery requests; builds search terms, verifies official sponsor sources, and returns a ranked shortlist with fit and blockers.
---

# Funding Opportunity Finder (`/find-funding`)

## When to Apply This Skill

Apply when the user types `/find-funding` or asks to find grants, fellowships, equipment, training, or internal funding for their research. Follow the workflow below and end with three prioritized next actions.

## Objective

Turn a short, non-confidential research description into a focused, verified shortlist of current funding opportunities (3–7 candidates). Treat search snippets and database records as leads, and verify each candidate against an official sponsor source before presenting it as a current opportunity.

## Minimum Researcher Intake & Data Minimization

Require only two pieces of information to begin a search:
1. **A short, non-confidential description of the research topic.**
2. **What the faculty member wants the funding to support** (e.g., graduate students, lab supplies, fieldwork, pilot study, equipment).

Do **not** require a CV, biosketch, full abstract, proposal draft, budget, or dataset. If the user's initial prompt is too brief to search effectively (for example, *"I study pufferfish"*), ask at most 2–3 short questions and offer a simple fill-in-the-blank template:
> *"I study [specific research topic or question], and I need funding for [activities, personnel, or expenses]."*

Once those two items are clear, proceed directly with the search.

**Data Minimization Rule**: Never request or place raw research data, participant records, student records, protected health information, proprietary partner details, export-controlled material, or unpublished patentable inventions into web-search queries. If sensitive details are provided, generalize them into broad disciplinary search terms before searching.

## Required Knowledge and Tools

Use available sources in this order:
1. Official sponsor websites and solicitations (e.g., NSF, NIH, DOE, DOD, NEH, NEA, USDA, NOAA, Florida agencies, and major foundations) for verification.
2. Public grant databases (e.g., Grants.gov, NIH Guide) as discovery leads.
3. Current FSU Limited Submissions website (`research.fsu.edu`) for institutional application limits.
4. Uploaded Grant Compass knowledge packets (`01_fsu_routing.md`, `02_match_rubric.md`, `03_output_templates.md`, `04_source_registry.md`), when present.

## Step-by-Step Workflow

### 1. Build Search Profile & Keywords
Extract the core research topic, what the funding should support, relevant disciplines, methods, target populations/settings, and any optional constraints provided (career stage, project stage, budget target, deadline window, or preferred sponsors). Generate 6–10 concise, sponsor-friendly search phrases without distorting the underlying research.

### 2. Discover & Screen Candidates
Search for open, forecast, or recurring opportunities matching the search profile. Exclude candidates that are:
- Closed or archived (unless clearly recurring and the user asked for future cycles).
- Explicitly unavailable to U.S. public universities / FSU or incompatible with stated career stage, budget scale, or required partnerships.
- Missing an already-passed mandatory letter of intent (LOI) or preapplication.

### 3. Verify Official Sponsor Sources (With Blocked-Site Fallback)
Open the official sponsor page or solicitation for each candidate to confirm:
- Sponsor, program title, and opportunity number.
- Verification status (`Verified`, `Partially Verified`, or `Unverified Lead`).
- Sponsor deadline, exact time, and time zone (plus LOI/preapplication dates).
- Applicant and PI eligibility, and any institutional or investigator application limits.
- Award floor/ceiling and project period.
- Official solicitation URL and verification date.

**Blocked-Site Fallback**: If an official sponsor page is blocked or inaccessible, do not invent details or rely on third-party summaries as final rules. Search for an accessible official PDF or Grants.gov record; if decisive fields remain inaccessible, mark them `Not verified` and place the item under **Unverified Leads** explaining what needs manual confirmation.

### 4. Classify Apparent Fit (Qualitative Only)
Classify each candidate using one of four qualitative categories (never output a numerical match percentage, award probability, or fundability score):
- **Strong apparent fit (`Strong Match`)**: Substantive research and mechanism alignment with no known fatal eligibility or timeline blocker.
- **Possible fit (`Possible Match`)**: Meaningful alignment, but important questions, partnership needs, scope adjustments, or application limits require verification.
- **Weak apparent fit (`Weak Match`)**: Marginal alignment or a verified requirement that makes the opportunity unsuitable.
- **Provisional — More Information Needed**: Promising lead where decisive official guidelines could not yet be verified.

### 5. Check FSU Limited-Submission Implications
If an opportunity restricts how many applications an institution may submit (e.g., "1 per university"), flag it prominently and check FSU Limited Submissions when possible. Direct the researcher to **FSU Research Development** (`limitedsubmissions@fsu.edu`)—absence from FSU's public listing does not authorize independent submission.

### 6. Present the Shortlist
Return **3–7 credible opportunities** (do not pad with weak matches). Put blockers (missed LOIs, institutional limits, mandatory cost share, required partners) first. For each opportunity, include:
- **Grant Title, Sponsor, Program, & Opportunity Number**
- **Official Source URL & Verification Status** (`Verified` / `Partially Verified` + date)
- **Deadline** (date, exact time, time zone, plus LOI/preapplication status)
- **Award Information & Project Period**
- **Eligibility & FSU Limited-Submission Status**
- **Apparent Fit Category** (`Strong apparent fit`, `Possible fit`, `Weak apparent fit`, or `Provisional`)
- **Why It May Fit** (2–4 bullets tied to the user's research and funding need)
- **Important Considerations / Potential Blockers**
- **Recommended Next Step** (e.g., run `/verify-opportunity` or `/match-opportunity` on the top pick)

End the response with **three prioritized next actions**.
