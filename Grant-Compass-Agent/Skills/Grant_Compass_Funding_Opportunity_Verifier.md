---
name: funding-opportunity-verifier
description: Verify one funding solicitation and check FSU limited-submission rules. Use for /verify-opportunity, /check-limited, or requests to analyze deadlines, eligibility, institutional/PI application limits, budgets, required documents, and review criteria.
---

# Funding Opportunity Verifier & Limited-Submission Checker (`/verify-opportunity` / `/check-limited`)

## When to Apply This Skill

Apply when the user types `/verify-opportunity` or `/check-limited`, or asks to analyze a specific grant solicitation, URL, opportunity number, or institutional/investigator application limit. Follow the workflow below and end with three prioritized next actions.

## Objective

Turn an official grant solicitation, program announcement, or URL into a source-grounded **Opportunity Brief** and **Limited-Submission Check** for Florida State University faculty and research staff. Put submission blockers first, preserve exact distinctions between required and optional items, and separate **Sponsor Required**, **FSU Required**, and **Recommended Practice**.

## Required Knowledge and Tools

Use available sources in this order:
1. Current official sponsor solicitation and controlling amendments/corrections.
2. Official sponsor FAQs and incorporated application guides.
3. Current FSU Limited Submissions website and FSU Research Development / SRA / FSURF guidance.
4. Uploaded Grant Compass knowledge packets (`01_fsu_routing.md`, `02_match_rubric.md`, `03_output_templates.md`, `04_source_registry.md`), when present.

Never treat a search snippet, third-party aggregator, or prior-year solicitation as the current controlling announcement.

## Step-by-Step Verification Workflow

### Step 1: Establish Source Control & Current Status
Identify the sponsor, program title, opportunity number, publication/version date, and whether amendments or incorporated guides apply. Classify status as `Open`, `Forecast`, `Recurring (next deadline verified)`, `Closed`, `Archived`, or `Unable to verify`. If an official webpage is blocked or incomplete, state what could not be accessed and ask the user to upload the solicitation PDF if needed (**Blocked-Site Fallback**).

### Step 2: Flag Submission-Blocking Issues First
Before the general summary, highlight any immediate blockers:
- Passed or imminent LOI, preapplication, registration, or full proposal deadline.
- Institutional application or nomination limit (Limited Submission).
- Explicit institutional or PI eligibility conflict.
- Mandatory cost sharing or required external partner/commitment letter.

### Step 3: Extract Critical Dates & FSU Internal Deadline Rule
Extract all sponsor deadlines (LOI, preapplication, full proposal) with **exact time and original time zone**, plus source section/page.
- **FSU Internal Deadline Rule**: Calculate a tentative FSU internal routing deadline *only* when the verified sponsor deadline, current controlling FSU proposal-submission policy (working-day rule), university closure calendar, and FSU's role (lead vs. subrecipient) are all established. Never subtract raw calendar days or invent an internal date; otherwise state:
  > *A precise FSU internal deadline could not be calculated from the available authoritative sources; confirm timing with your departmental grants analyst and the responsible FSU office.*

### Step 4: Verify Eligibility & Run the FSU Limited-Submission Check
Extract eligible applicant types, PI appointment/career-stage rules, and required partnerships. Then explicitly separate and check **Application Limits**:
1. **Institutional Limit**: Does the sponsor restrict how many proposals, concept papers, LOIs, or nominations one university/campus/organization may submit?
2. **Investigator Limit**: Does the sponsor restrict how many applications one individual may participate in as PI, Co-PI, or key personnel? (Report separately from institutional limits.)
3. **FSU Limited-Submission Classification**: Assign one of the following statuses:
   - `Yes — FSU internal process identified` (include FSU internal deadline and required materials if verified).
   - `Sponsor limit identified — no current FSU listing found` (*Required note*: Direct the researcher to **FSU Research Development** immediately; absence from the public FSU list does not authorize independent submission).
   - `Possibly limited — institutional interpretation required` (ambiguous organizational unit or multi-track cap; refer to FSU Research Development).
   - `Investigator limit only` (no institutional cap, but individual participation is restricted).
   - `No explicit institutional limit identified` (in the official sources reviewed).
   - `Unable to verify`.

### Step 5: Verify Funding, Cost Sharing, & Project Period
Extract award floor, ceiling, total vs. direct-cost basis, F&A/indirect-cost rules, maximum duration, budget restrictions, and whether cost sharing is `Required`, `Prohibited`, or `Optional`.

### Step 6: Extract Required Components, Formatting, & Review Criteria
List narrative sections, forms, attachments, letters, biosketches, data/mentoring plans, page/word/font/margin rules, and submission system/AOR requirements. Preserve exact distinctions among:
- **Required** / **Conditional** / **Optional** / **Encouraged** / **Prohibited** / **Not stated in the available authoritative sources**
Capture published **Review Criteria** and their weights/points, distinguishing scored criteria from general program priorities.

### Step 7: Identify FSU Routing & Compliance Flags
Note apparent FSU routing (`Sponsored Research Administration [SRA]` for federal/state/local public funding; `FSU Research Foundation [FSURF]` for private foundations, industry, or foreign sponsors; `Research Development` for limited submissions; `RAMP` for internal routing) and flag regulated activities (IRB/human subjects, IACUC/vertebrate animals, export control, international activities) as referral items, not final institutional determinations.

## Required Output Structure

1. **Submission-Blocking Issues** (listed first)
2. **Opportunity Brief Table** (`Field | Verified Finding (Required/Optional/Prohibited) | Source Section/Page or URL`) covering Sponsor/Program, Opportunity/Version, Status, Sponsor Deadline (with time zone), LOI/Preapplication, Eligibility, Application Limits, Funding/Duration, Cost Sharing, Required Partners, Narrative & Formatting, Attachments, and Submission System.
3. **Limited-Submission Check** (Institutional limit, Investigator limit, FSU Limited-Submission status, and Research Development referral when applicable)
4. **Published Review Criteria** (with weights/points if stated)
5. **Unknown or Unresolved Information** & **Tentative FSU Internal Deadline Note**
6. **Official Sources & Verification Date**
7. **Recommended Next Three Actions**
