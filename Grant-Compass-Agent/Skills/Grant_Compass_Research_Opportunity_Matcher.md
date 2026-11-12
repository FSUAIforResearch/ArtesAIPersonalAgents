---
name: research-opportunity-matcher
description: Compare a research concept with a verified funding opportunity. Use for /match-opportunity or project-fit questions; assess qualitative alignment, eligibility concerns, mechanism fit, review criteria, and blockers without predicting funding success.
---

# Research Opportunity Matcher

## When to Apply This Skill

Apply when the user types `/match-opportunity` or asks whether a project fits a specific opportunity. Follow the workflow below and end with three prioritized next actions.

## Objective

Compare an FSU faculty member's research concept with one specific, verified funding opportunity and produce a transparent qualitative fit assessment.

Use this Skill when the user asks whether a project, research idea, program, training plan, equipment request, fellowship plan, or collaborative concept fits a particular funding opportunity.

Do not use this Skill to search broadly for funding. Use the Funding Opportunity Finder for discovery and the Funding Opportunity Verifier to establish the current opportunity requirements before matching.

## Required inputs

Use two inputs:

1. A verified funding opportunity record, official solicitation, or opportunity brief.
2. A research concept supplied by the user.

A useful research concept may include:

- Department or discipline.
- Working title.
- Research problem.
- Objective or aims.
- Methods or approach.
- Population, setting, or geographic focus.
- Project stage.
- Approximate funding need.
- Expected duration.
- Collaborators or required partners.
- Career-stage facts when relevant.
- Human participants, vertebrate animals, international activities, controlled information, or sensitive-data considerations.
- Preferred or excluded sponsors.

Collect only the fields needed for the current comparison. Do not require the user to complete a full intake form when one or two missing facts would be sufficient.

## Required knowledge and tools

Consult these uploaded Grant Compass knowledge packets:

- `01_fsu_routing.md`
- `02_match_rubric.md`
- `03_output_templates.md`
- `04_source_registry.md`

Use the current official sponsor solicitation and controlling amendments as the authority for program purpose, priorities, eligibility, application limits, funding, project period, required partnerships, review criteria, and restrictions.

If the opportunity has not been verified, run or request the Funding Opportunity Verifier workflow before presenting a confident assessment.

## Workflow

### Step 1: Confirm the opportunity record

Verify that the available opportunity information identifies:

- Sponsor.
- Program title.
- Opportunity number.
- Current status.
- Sponsor deadline.
- Program purpose and priorities.
- Eligibility requirements.
- Institutional and investigator application limits.
- Award range or ceiling.
- Project period.
- Required activities, populations, settings, methods, partners, or outcomes.
- Review criteria.
- Cost-sharing requirement or prohibition.
- Current official source.

If critical opportunity information is missing, continue with a provisional match only when useful. Clearly identify the limitation.

Do not use an API summary, search result, third-party listing, prior-cycle announcement, or successful proposal as the controlling source.

### Step 2: Identify material project facts

Extract the facts supplied by the researcher. Determine which missing facts would materially change the assessment.

Ask only for the minimum missing information needed. Examples include:

- Career stage when the mechanism is career-stage restricted.
- Approximate budget when the mechanism has a narrow ceiling.
- Project duration when the allowed period is short.
- Required partner availability when the sponsor mandates a partnership.
- Institution or appointment type when eligibility depends on it.
- Project stage when the mechanism supports planning rather than full implementation.

Do not request sensitive information unless the opportunity makes it necessary and the system is approved to process it.

### Step 3: Evaluate program alignment

Compare the research concept with the sponsor's stated:

- Program purpose.
- Funding priorities.
- Eligible research topics.
- Eligible activities.
- Target populations.
- Required settings or geographic focus.
- Intended outcomes.

Distinguish substantive alignment from keyword overlap.

Use evidence such as:

- The project directly addresses a named priority.
- The proposed population matches the sponsor's target population.
- The method is explicitly permitted or encouraged.
- The intended outcome corresponds with the program's objectives.

Do not treat a shared subject term as sufficient evidence of fit.

### Step 4: Evaluate apparent eligibility

Compare known project and investigator facts with explicit sponsor conditions involving:

- Institution type.
- Principal investigator or project director role.
- Appointment or employment status.
- Degree or credential.
- Career stage.
- Citizenship or residency only when explicitly required.
- Geographic restriction.
- Prior award, resubmission, renewal, or participation restrictions.
- Required registrations or memberships.
- Institutional and investigator application limits.

Use one of these conclusions:

- Apparent eligibility based on supplied facts.
- Eligibility requires verification.
- Potential eligibility conflict.
- Explicit eligibility mismatch.

Never state final eligibility unless an authoritative sponsor or institutional process has confirmed it.

### Step 5: Evaluate mechanism fit

Compare:

- Project stage with the mechanism's purpose.
- Requested budget with the award range or ceiling.
- Proposed duration with the allowed project period.
- Research, training, fellowship, equipment, center, conference, planning, or team-science mechanism.
- Required deliverables.
- Required preliminary evidence or readiness.

Examples:

- A planning-stage concept may fit a planning grant but not a late-stage implementation mechanism.
- A $750,000 project may require substantial resizing for a $250,000 ceiling.
- An individual investigator project may not fit a center mechanism requiring multiple cores.

Do not reject a concept solely because the proposal narrative is not yet developed.

### Step 6: Evaluate team and partnership fit

Identify whether the opportunity requires or favors:

- Multiple disciplines.
- Community partners.
- School districts.
- Healthcare or clinical sites.
- Industry partners.
- Specific institution types.
- Multi-institutional teams.
- Mentors.
- Advisory boards.
- Evaluators.
- Trainees.
- Subawards or consortia.

Compare these requirements with the user's supplied team information.

Do not invent collaborators, commitments, sites, mentors, subrecipients, or institutional support.

### Step 7: Evaluate review-criteria fit

Map the concept to each published review criterion when available.

For every criterion, identify:

- Current alignment.
- Evidence already available.
- Missing evidence or planning.
- Proposal development needed.

Distinguish between:

- A concept that conflicts with the criterion.
- A concept that may address the criterion but lacks developed proposal detail.

Do not predict reviewer scores or funding outcomes.

### Step 8: Identify submission blockers

Check for:

- Closed or expired status.
- Missed letter of intent or preapplication.
- Institutional application limit.
- Investigator application limit.
- Explicit eligibility conflict.
- Mandatory cost sharing.
- Required partner or site.
- Geographic restriction.
- Required preliminary results.
- Budget mismatch.
- Project-period mismatch.
- Required registration.
- Human-subject, animal, biosafety, export-control, research-security, or sensitive-data considerations.

Put submission blockers before the general fit analysis.

### Step 9: Check FSU implications

Consult `01_fsu_routing.md` and current FSU sources.

Identify:

- Apparent FSU routing office.
- Possible limited-submission status.
- Need for Research Development review.
- Potential compliance referrals.
- Budget or institutional questions requiring an authorized FSU reviewer.

Treat these as routing flags, not institutional determinations.

### Step 10: Classify apparent fit

Use `02_match_rubric.md` and select one classification.

#### Strong apparent fit

Use only when:

- The project substantially aligns with the central program purpose and priorities.
- The mechanism, stage, budget, and duration are broadly compatible.
- No explicit blocking mismatch has been identified.
- Material eligibility facts are verified or clearly pending.
- The concept appears capable of addressing the published review criteria.

#### Possible fit

Use when:

- Meaningful alignment exists, but important issues require verification or adjustment.
- The project may need reframing, resizing, an added partner, a different timeline, or additional evidence.
- Eligibility or program scope is ambiguous.
- A limited submission, cost-sharing requirement, deadline, or other blocker may apply.

#### Weak apparent fit

Use when:

- The concept conflicts with the central program purpose or eligible activities.
- A verified eligibility requirement appears not to be met.
- The project stage, budget, duration, population, geography, required partnership, or mechanism is materially incompatible.
- The apparent alignment depends mainly on shared keywords.

When fit is weak, explain the mismatch and suggest a more appropriate search direction.

## Required output

Use the Research-to-Opportunity Match template in `03_output_templates.md`.

Include:

### Submission-Blocking Issues

List missed deadlines, application limits, explicit eligibility conflicts, mandatory cost sharing, required partners, or other material blockers first.

If none are identified, state:

> No submission-blocking issue was identified in the available authoritative sources. This is not a guarantee of eligibility or submission readiness.

### Apparent Fit

State one classification:

- Strong apparent fit.
- Possible fit.
- Weak apparent fit.

Add this caution:

> This classification describes alignment with the available opportunity and project information. It is not a funding prediction or final eligibility determination.

### Alignment

Explain the strongest evidence-based points of correspondence involving program purpose, priorities, population, methods, setting, outcomes, or review criteria.

### Potential Mismatches

Explain concerns involving scope, mechanism, budget, duration, population, method, geography, partnership, team, or project stage.

### Eligibility Concerns

Separate confirmed conditions from facts that require verification.

### Review-Criteria Fit

For each criterion, explain current alignment and development needed.

### FSU Considerations

Identify limited-submission, routing, budget, or compliance referral issues without making institutional determinations.

### Missing Information

List only information that materially affects the assessment.

### Recommended Verification

Identify the exact official source, sponsor question, FSU office, or institutional process that should be used next.

### Recommended Next Three Actions

Provide three specific, prioritized actions.

### Sources

Identify the current official solicitation, amendments, FAQs, and FSU sources used.

## Required labels

Use these labels where helpful:

- **Confirmed requirement**
- **Apparent concern**
- **Recommendation**
- **Unknown or unresolved**

When a consequential fact cannot be established, state:

> **Not identified in the available authoritative sources.**

## Prohibited outputs

Do not provide:

- Match percentages.
- Probability of award.
- Fundability scores.
- Predicted reviewer scores.
- Guaranteed eligibility.
- Guaranteed institutional approval.
- Final compliance conclusions.
- Claims that the proposal will or will not be funded.

Do not invent:

- Preliminary data.
- Citations.
- Publications.
- Personnel or credentials.
- Facilities.
- Partner commitments.
- Prior funding.
- Institutional facts.
- Compliance approvals.

## Missing-information behavior

If missing information does not materially affect the assessment, continue without asking for it.

If missing information prevents a reliable classification:

1. Complete the dimensions that can be assessed.
2. Identify the minimum missing information.
3. Explain why the information matters.
4. Provide a provisional classification only when useful.
5. Label the classification provisional.

## Final quality check

Before responding, confirm that:

- The opportunity was verified or the limitation was stated.
- Every alignment and mismatch claim is tied to sponsor language or supplied project facts.
- Submission blockers appear first.
- Missing facts were not converted into confident conclusions.
- No match percentage, reviewer score, or award prediction appears.
- FSU routing and limited-submission implications were checked.
- The response ends with three specific next actions.
