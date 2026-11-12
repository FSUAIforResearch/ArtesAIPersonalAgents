---
name: fsu-limited-submission-checker
description: Check sponsor application limits and FSU limited-submission processes. Use for /check-limited or institutional, nomination, or investigator-limit questions; distinguish limits, verify current FSU guidance, and refer unresolved selection issues.
---

# FSU Limited Submission Checker

## When to Apply This Skill

Apply when the user types `/check-limited`, asks about application limits, or another workflow identifies a possible limit. Follow the workflow below and end with three prioritized next actions.

## Objective

Determine whether a specific funding opportunity limits the number of applications, proposals, nominations, concept papers, or letters of intent that Florida State University may submit, and identify the correct next step for the researcher.

Use this Skill when:

- A user asks whether an opportunity is a limited submission.
- A solicitation includes an institutional application or nomination limit.
- The Funding Opportunity Finder or Funding Opportunity Verifier identifies a possible application limit.
- A user asks whether FSU has an internal competition or internal deadline.
- A user wants to know whether the user may proceed independently with a limited opportunity.

Do not use this Skill to determine scientific fit, write a proposal, approve an applicant, select an institutional nominee, or guarantee permission to submit.

## Required knowledge and tools

Use available sources in this order:

1. Current official sponsor solicitation.
2. Controlling amendments, corrections, and FAQs.
3. Current FSU Limited Submissions website.
4. Current FSU Research Development guidance.
5. Uploaded Grant Compass knowledge packets:
   - `01_fsu_routing.md`
   - `03_output_templates.md`
   - `04_source_registry.md`
6. User-provided official URL or solicitation document.

Use an API record, search result, newsletter, or third-party listing only to locate the official sponsor source. Do not treat a discovery summary as controlling.

## Required inputs

Attempt to identify:

- Sponsor.
- Program title.
- Opportunity number.
- Official solicitation URL or uploaded solicitation.
- Sponsor deadline.
- Letter-of-intent or preapplication deadline.
- Any sponsor language limiting institutional or investigator submissions.

If the user provides only a title, search approved official sources from `04_source_registry.md` and confirm the exact opportunity before reaching a conclusion.

## Definitions

### Institutionally limited opportunity

Treat an opportunity as institutionally limited when the sponsor restricts the number of submissions, applications, proposals, nominations, concept papers, preapplications, or letters of intent that one institution or organizational unit may submit.

Examples include:

- One application per institution.
- Two nominations per university.
- One proposal per campus.
- A maximum number per school, college, department, or eligible component.
- One lead application, with additional participation allowed only as a subrecipient.
- A combined institutional limit across tracks, categories, or program areas.

### Investigator limit

An investigator-level limit restricts the number of applications in which one person may participate. Investigator limits are important but do not automatically create an institutional limited submission.

Report investigator limits separately.

### Ambiguous limit

Treat a limit as ambiguous when the sponsor uses terms such as organization, component, campus, branch, affiliate, department, school, or system without clearly defining how the limit applies to FSU.

Do not interpret ambiguous organizational language independently. Route the question to FSU Research Development.

## Workflow

### Step 1: Verify the sponsor source

Locate the current official solicitation and any controlling amendments or FAQs.

Confirm:

- Sponsor.
- Program title.
- Opportunity number.
- Solicitation version or publication date.
- Current status.
- Sponsor deadline.

If the supplied source is archived or from a prior cycle, search for the current official source when available. Do not apply a prior-cycle application limit to a current competition without verification.

### Step 2: Search for limit language

Review the official sources for terms including:

- limited submission
- number of applications
- application limit
- institutional limit
- organizational limit
- one per institution
- per campus
- per department
- per school or college
- nominations
- concept papers
- preapplications
- letters of intent
- lead applicant
- duplicate submissions
- multiple applications
- restrictions on applicants

Read the complete surrounding section. Do not rely on a keyword fragment without context.

### Step 3: Extract the exact sponsor limit

Record:

- Exact numerical limit.
- Unit to which the limit applies.
- Whether the limit applies to applications, nominations, letters of intent, concept papers, or another submission stage.
- Whether the limit spans multiple tracks or categories.
- Whether subrecipient participation is included or excluded.
- Whether resubmissions, renewals, or separate campuses are treated differently.
- Sponsor deadline, time, and time zone.
- Source title, section, page, and URL.

Paraphrase the rule accurately. Use a brief quotation only when necessary to preserve important wording.

### Step 4: Distinguish institutional and investigator limits

Classify each identified restriction as:

- Institutional application limit.
- Organizational-component limit requiring FSU interpretation.
- Investigator-level limit.
- Nomination limit.
- Preapplication or letter-of-intent limit.
- No explicit limit identified.
- Unable to verify.

An investigator limit does not replace the institutional-limit analysis.

### Step 5: Check the FSU Limited Submissions source

Search the current FSU Limited Submissions website for:

- Sponsor.
- Program title.
- Opportunity number.
- Common abbreviation.
- Current competition year or cycle.

Attempt to identify:

- Whether FSU lists the opportunity.
- FSU internal deadline.
- Internal application or nomination instructions.
- Required internal materials.
- Internal review or selection process.
- Contact or responsible office.
- Status of the internal competition.

Do not assume that a similarly titled prior-year listing applies to the current cycle.

### Step 6: Assign the FSU limited-submission result

Use exactly one result:

#### Yes - FSU internal process identified

Use when the sponsor imposes an institutional or nomination limit and the current FSU source identifies an internal process for the same competition cycle.

#### Sponsor limit identified - no current FSU listing found

Use when the sponsor imposes a limit but no matching current FSU listing is found.

Required next step:

> Contact FSU Research Development immediately. Absence from the public FSU listing does not mean the researcher may proceed independently.

#### Possibly limited - institutional interpretation required

Use when sponsor language is ambiguous, applies to an organizational component, spans multiple tracks, or cannot be confidently mapped to FSU.

Required next step:

> Ask FSU Research Development to interpret the sponsor's application limit before proceeding.

#### Investigator limit only

Use when the sponsor restricts an individual's participation but does not identify an institutional submission limit.

Still report the investigator restriction prominently.

#### No explicit institutional limit identified

Use only when the current official sponsor sources were reviewed and no institutional application or nomination limit was found.

Required caution:

> No explicit institutional limit was identified in the official sources reviewed. This is not a guarantee that no FSU internal coordination is required.

#### Unable to verify

Use when the controlling sponsor source or current FSU source cannot be retrieved or interpreted reliably.

### Step 7: Check timing and blockers

Identify:

- FSU internal deadline.
- Sponsor letter-of-intent or preapplication deadline.
- Sponsor application deadline.
- Whether an internal deadline appears to have passed.
- Whether the sponsor deadline appears to have passed.
- Whether the listing is for the current cycle.

Do not invent an internal deadline. If no current internal date is identified, state:

> **Not identified in the available authoritative sources.**

### Step 8: Route the researcher

Consult `01_fsu_routing.md`.

For a limited submission or ambiguous institutional limit, direct the researcher to FSU Research Development.

Do not:

- Tell the researcher to submit independently.
- Select or rank internal candidates.
- Approve an exception.
- Promise an internal nomination.
- Claim that an internal application was received or selected.
- Assign a named contact unless the name appears in a current authoritative source.

## Required output

Use this structure.

# Limited-Submission Check: [Program Title]

## Result

State one required result:

- Yes - FSU internal process identified.
- Sponsor limit identified - no current FSU listing found.
- Possibly limited - institutional interpretation required.
- Investigator limit only.
- No explicit institutional limit identified.
- Unable to verify.

## Submission-Blocking Issues

List first:

- Passed or near-term FSU internal deadline.
- Passed letter-of-intent or preapplication deadline.
- Passed sponsor deadline.
- Institutional application or nomination limit.
- Ambiguous organizational limit.
- Current-cycle listing not found.

## Sponsor Limit

- Sponsor: [value]
- Program: [value]
- Opportunity number: [value]
- Exact limit: [value]
- Limit applies to: [institution / campus / department / individual / nomination / preapplication / other]
- Tracks or categories affected: [value]
- Sponsor deadline: [date, time, time zone]
- Sponsor source: [document, section/page, official URL]

## FSU Internal Process

- Current FSU listing found: [yes/no/unable to verify]
- FSU internal deadline: [value or not identified]
- Required internal materials: [value or not identified]
- Internal process: [value or not identified]
- Responsible office: FSU Research Development, unless a current authoritative source specifies otherwise
- FSU source: [official URL and verification date]

## Investigator Restrictions

List investigator-level participation restrictions separately from the institutional limit.

## Unknown or Unresolved

List only material unknowns, such as:

- Meaning of institution, campus, or organizational component.
- Whether multiple tracks share one limit.
- Whether subrecipient participation counts toward the limit.
- Whether the FSU listing is for the current cycle.

## Recommended Next Three Actions

Provide three prioritized actions. When the opportunity is limited and no current FSU listing is found, the first action must be contacting FSU Research Development.

## Sources

Identify:

- Current official sponsor solicitation.
- Controlling amendments or FAQs.
- Current FSU Limited Submissions page.
- Current FSU Research Development guidance when used.
- Verification date.

## Evidence rules

Cite or identify the source location for:

- Institutional application limit.
- Investigator limit.
- Nomination limit.
- Letter-of-intent or preapplication limit.
- Sponsor deadline.
- FSU internal deadline.
- Internal application instructions.

Never fabricate a source, page number, deadline, contact, limit, listing, or internal result.

When a consequential fact is absent, state:

> **Not identified in the available authoritative sources.**

## Failure and fallback behavior

If the sponsor source cannot be retrieved:

1. State that the sponsor limit could not be verified.
2. Ask the user for the official solicitation or URL only when needed.
3. Do not rely on a third-party summary as final evidence.
4. Return **Unable to verify**.

If the FSU source cannot be retrieved:

1. State that the current FSU internal process could not be verified.
2. Preserve the verified sponsor limit.
3. Direct the researcher to FSU Research Development.
4. Do not interpret absence or retrieval failure as permission to submit.

If the sponsor and FSU sources conflict:

1. Describe the conflict.
2. Treat the sponsor's current official limit as controlling for sponsor requirements.
3. Treat the current FSU source as controlling for FSU's internal process.
4. Refer unresolved institutional interpretation to FSU Research Development.

## Boundaries

Do not:

- Guarantee that an opportunity is unrestricted.
- Guarantee that a researcher may submit.
- Approve or waive an internal competition.
- Select an institutional nominee.
- Create an internal deadline not found in a current source.
- Treat absence from the FSU website as absence of a sponsor limit.
- Treat an investigator limit as an institutional limit without evidence.
- Make final eligibility, budget, compliance, submission, or award decisions.

## Final quality check

Before responding, confirm that:

- The current sponsor cycle was identified.
- The exact limit and unit were captured.
- Institutional and investigator limits were separated.
- The current FSU source was checked.
- Absence from the FSU listing was not treated as permission to proceed.
- Deadlines and current-cycle status were checked.
- Unknown information was labeled rather than inferred.
- The response ends with three specific next actions.
