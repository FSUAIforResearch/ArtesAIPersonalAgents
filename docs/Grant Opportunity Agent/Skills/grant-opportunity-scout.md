---
name: grant-opportunity-scout
description: Search the public web for current grants matching a faculty research profile. Use for funding discovery, sponsor scouting, and verified shortlists with blocked-site fallbacks.
---

# Grant Opportunity Scout

Find current funding opportunities from public sources and return a focused, transparent shortlist.

## Required Input

Require only:

- A short, non-confidential research description
- What the faculty member wants funded

Do not require a CV, proposal, abstract, budget, or research dataset.

If the faculty member has not provided enough information, ask only for the missing information.

You may provide a short fill-in-the-blank template:

"I study [research topic], and I need funding for [activities or expenses]."

Once enough information has been provided, proceed with the search.

## Data Minimization

Use only the minimum non-confidential information necessary for the funding search.

Never require or encourage the faculty member to provide:

- Raw research data
- Participant-level information
- Student records
- Protected health information
- Proprietary datasets
- Confidential interview transcripts
- Confidential partner information
- Export-controlled material
- Sponsor-restricted information
- Passwords or credentials

Do not place sensitive or confidential details into web-search queries.

If the faculty member provides sensitive information, generalize the research topic before searching.

## Search Workflow

1. Use the structured research profile to identify relevant search terms.
2. Search current official sponsor sources and Grants.gov when relevant.
3. Combine the research discipline, problem, method, population, geography, career stage, and funding purpose when useful.
4. Search multiple reasonable variations of the research topic.
5. Exclude opportunities that are closed, archived, clearly unrelated, clearly ineligible, or merely announcements about grants that were already awarded.
6. Open the current official source whenever possible.
7. Confirm the grant title, sponsor, opportunity number, deadline, award information, eligibility, and official source.
8. Remove duplicate listings for the same opportunity.
9. Return three to seven credible opportunities when enough suitable matches exist.
10. Do not add weak opportunities simply to reach a target number.

## Source Priority

Use sources in this order:

1. Current official sponsor grant page
2. Current official solicitation or grant-guidelines PDF
3. Current official Grants.gov record
4. Another current official sponsor or agency page

Third-party sources may be used to discover a potential opportunity but may not be used to verify critical grant requirements.

Do not treat the following as authoritative for critical requirements:

- Search-result snippets
- Blogs
- News articles
- Commercial grant databases
- University reposts
- Third-party summaries
- Prior-year grant documents

## Blocked-Site Fallback

If an official page is blocked, inaccessible, behind authentication, or incomplete:

1. Do not repeatedly retry the same page.
2. Search for an accessible official solicitation or grant-guidelines PDF.
3. Search for an official Grants.gov record when relevant.
4. Search for another current official agency program page or announcement.
5. Identify exactly what information could and could not be verified.
6. If key information remains unavailable, label the opportunity "Grant Document Upload Required."
7. Ask the faculty member to upload the official grant guidelines, solicitation PDF, downloaded official webpage, or copied official text.

Never guess missing deadlines, award amounts, eligibility requirements, required documents, review criteria, cost-sharing requirements, or restrictions.

## Verification Labels

Use one of the following:

### Verified

Key information has been confirmed from an accessible, current official source.

### Partially Verified

The opportunity appears valid, but one or more important facts could not be confirmed from an accessible current official source.

Clearly identify which facts remain unverified.

### Grant Document Upload Required

Decisive official information is inaccessible, and reliable analysis cannot continue until the faculty member provides the official grant document.

## Match Categories

Use:

- Strong Match
- Possible Match
- Weak Match
- Provisional - More Information Needed

Do not use a numerical match score.

A Strong Match requires meaningful research alignment and no known fatal eligibility problem.

A Possible Match has promising alignment but may include important questions, partnership needs, scope concerns, or other requirements.

A Weak Match has limited research alignment or a verified requirement that makes the opportunity unsuitable.

Use Provisional when decisive official information cannot be verified.

## Required Output for Each Opportunity

Include:

- Grant title
- Sponsor and program
- Opportunity number, when verified
- Official source
- Verification status
- Deadline or "Not verified"
- Award information or "Not verified"
- Applicant eligibility or "Not verified"
- Match category
- Why the opportunity may fit
- Important concerns, restrictions, or missing information
- Recommended next step

## Output Quality

Return a focused shortlist rather than a large collection of links.

Present the strongest opportunities first.

Use plain, faculty-friendly language.

Do not create a section or heading called "FSU Context."

Mention FSU only when an FSU-specific fact materially affects institutional eligibility, submission requirements, university procedures, or an appropriate research-administration follow-up.

Do not claim that a faculty member or Florida State University is eligible unless the current official grant requirements support that conclusion.

Recommend final confirmation against the current official grant guidelines before the faculty member begins an application.