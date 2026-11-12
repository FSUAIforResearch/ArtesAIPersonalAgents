# Research Plan: Grant Compass MVP

## 1. Project Overview

### Working Title
**Evaluating Grant Compass: An AI Agent for Funding Opportunity Analysis and Proposal Planning**

### Purpose
This research will design and evaluate a minimum viable version of **Grant Compass**, an AI-assisted agent for university faculty and research staff. The agent will support four core tasks:

1. **Analyze** a funding opportunity announcement and extract important requirements.
2. **Match** a research concept to the opportunity and explain areas of alignment and concern.
3. **Plan** proposal development by creating a checklist and timeline.
4. **Draft** a proposal outline aligned with the sponsor's stated requirements and review criteria.

The study will determine whether the agent can perform these tasks accurately, consistently, safely, and usefully enough to support faculty without replacing decisions made by principal investigators, research administrators, compliance offices, or sponsors.

## 2. Research Problem

Faculty frequently spend substantial time reading funding announcements, checking eligibility, identifying required components, interpreting review criteria, and planning proposal development. Important information may be dispersed across sponsor webpages, solicitation documents, amendments, frequently asked questions, and university procedures.

A generative AI agent could reduce this burden, but errors involving deadlines, eligibility, page limits, required attachments, funding limits, or institutional procedures could cause a proposal to be rejected. The proposed research therefore focuses on both **usefulness** and **trustworthiness**.

## 3. Research Aim

To assess whether Grant Compass can accurately analyze funding announcements, evaluate research-opportunity alignment, produce actionable proposal plans, and create evidence-grounded proposal outlines for faculty across multiple academic disciplines.

## 4. Research Questions

### Primary Questions

1. How accurately does Grant Compass extract critical requirements from funding opportunity announcements?
2. How reliably does the agent distinguish confirmed sponsor requirements, university requirements, recommendations, and missing information?
3. How useful are the agent's fit assessments, checklists, timelines, and proposal outlines to faculty and research administrators?
4. What types of errors, omissions, unsupported claims, or overconfident conclusions occur during use?

### Secondary Questions

1. Does performance vary by sponsor, discipline, announcement length, or opportunity complexity?
2. Does the agent reduce the time required to complete an initial opportunity review?
3. How often do human reviewers agree with the agent's assessment of apparent fit?
4. What source, prompt, and interface changes improve performance during iterative testing?

## 5. Objectives

The project will:

- Build a controlled MVP covering the four core capabilities.
- Develop a test set of at least 10 real funding announcements and 10 anonymized research concepts.
- Create a human-reviewed reference answer for every test case.
- Measure extraction accuracy, source grounding, omission rates, usefulness, and completion time.
- Identify high-risk failure modes and establish release criteria.
- Produce recommendations for a limited faculty pilot and later institutional integration.

## 6. Scope

### Included in the MVP

- Analysis of a faculty-provided funding announcement or official sponsor material.
- Extraction of deadlines, eligibility rules, funding limits, project periods, required components, page limits, formatting rules, review criteria, and submission instructions.
- Qualitative comparison of a research concept with the opportunity.
- Identification of alignment, potential mismatch, unresolved questions, and eligibility concerns.
- Creation of proposal-development checklists and timelines.
- Creation of proposal outlines aligned with sponsor requirements and review criteria.
- Citations or traceable references to the source supporting consequential claims.
- Clear placeholders when project-specific facts are missing.

### Excluded from the MVP

- Automated proposal submission.
- Final eligibility determinations.
- Compliance determinations or approvals.
- Autonomous communication with sponsors or collaborators.
- Final budget calculation or approval.
- Commitments of institutional resources.
- Predictions of award probability or “fundability” scores.
- Generation of unsupported citations, preliminary results, credentials, facilities, partnerships, or institutional facts.

## 7. Study Design

### Overall Approach

Use a **mixed-methods, staged evaluation** combining benchmark testing, expert review, task-time comparison, and faculty usability testing.

### Evaluation Phases

#### Phase 1: Test Set and Reference Answers

Create a benchmark containing:

- At least **10 current or recently closed funding announcements** from a range of sponsor and program types.
- At least **10 anonymized research concepts** representing different disciplines, career stages, project types, methods, and funding needs.
- At least **20 paired scenarios** combining research concepts and opportunities, including good fits, partial fits, and clear mismatches.

Suggested disciplinary coverage:

- Biomedical or public health research
- Social and behavioral sciences
- Education
- Humanities
- Engineering or computing
- Natural sciences
- Community-engaged or interdisciplinary research

Each reference answer should be prepared or validated by at least one experienced research administrator and, when possible, one faculty researcher familiar with the discipline.

#### Phase 2: Controlled Benchmark Evaluation

Run the same standardized prompts across all cases. Preserve the exact input, output, model or agent version, source set, date, and reviewer notes.

Test four task families:

1. **Analyze:** Extract opportunity requirements.
2. **Match:** Compare the research concept with the opportunity.
3. **Plan:** Generate a checklist and backward-planned timeline.
4. **Draft:** Generate a proposal outline mapped to review criteria.

#### Phase 3: Expert Review

Ask sponsored-research staff or trained grant-development reviewers to rate each output without seeing the development notes. Where feasible, use two reviewers for high-risk fields and resolve disagreements through adjudication.

#### Phase 4: Faculty Usability Pilot

Recruit approximately **8 to 15 faculty participants** from at least three disciplinary groups. Each participant should complete one realistic grant-analysis task using the agent and, if feasible, the same or a comparable task using their normal process.

Collect:

- Task completion time
- Corrections required
- Missing or misleading information
- Perceived usefulness
- Trust and confidence
- Intention to use
- Qualitative comments

#### Phase 5: Iteration and Retest

Classify failures, revise instructions or sources, and rerun the complete benchmark. Do not evaluate only the previously failed cases, because a correction may introduce regressions elsewhere.

## 8. Materials and Data

### Funding Announcements

Select announcements with variation in:

- Sponsor type
- Announcement length
- Application complexity
- Eligibility restrictions
- Limited-submission status
- Required attachments
- Page and formatting rules
- Budget restrictions
- Letter-of-intent or pre-application requirements
- Number and location of amendments or supplementary instructions

Use the authoritative sponsor announcement and any controlling amendments as the reference source. Record the retrieval date and document version.

### Research Concepts

Each anonymized concept should include enough information for a meaningful fit assessment:

- Research topic and question
- Discipline
- Population or setting
- Proposed methods
- Project stage
- Approximate budget range
- Project duration
- Collaborators or required partnerships
- Career-stage information when relevant
- Human-participant, animal, biosafety, export-control, or data-sensitivity considerations when applicable

Do not include unpublished confidential details unless the institution has approved the system and study procedures for that information.

### Institutional Sources

If internal procedures are tested, use a curated collection containing only approved, version-controlled materials, such as:

- Proposal submission policy
- Internal deadline policy
- Limited-submission procedure
- Sponsored-program routing procedure
- Current facilities and administrative cost guidance
- Cost-sharing policy
- Research compliance referral guidance
- Approved institutional facts and boilerplate

## 9. Standard Test Tasks

### Task A: Analyze

**Prompt template:**

> Analyze this funding announcement. Identify the sponsor, program, opportunity number, purpose, deadline, letter-of-intent requirements, eligibility, award amount, project period, required proposal components, page limits, formatting rules, review criteria, submission mechanism, restrictions, and unresolved questions. Cite the source location for every consequential requirement. Do not infer missing information.

### Task B: Match

**Prompt template:**

> Compare this anonymized research concept with the funding opportunity. Classify the apparent fit as strong, possible, or weak. Explain positive alignment, potential mismatches, eligibility concerns, missing information, and the next verification steps. Do not make a final eligibility determination.

### Task C: Plan

**Prompt template:**

> Create a proposal checklist and timeline working backward from the sponsor deadline. Separate sponsor requirements, university requirements, and recommended practices. Assign suggested responsibility categories, but do not assign named individuals unless provided. If the institutional deadline is unknown, flag it instead of inventing one.

### Task D: Draft

**Prompt template:**

> Create a proposal outline aligned with the sponsor's required sections and review criteria. Use only the facts supplied in the research concept and opportunity. Insert labeled placeholders for missing evidence, personnel, preliminary data, citations, facilities, or institutional facts.

## 10. Evaluation Measures

### A. Requirement Extraction Accuracy

Score the following fields individually:

- Sponsor and program
- Opportunity number
- Sponsor deadline and time zone
- Letter-of-intent or pre-application deadline
- Institutional and principal investigator eligibility
- Award ceiling, floor, or expected range
- Project period
- Required proposal components
- Required attachments
- Page limits
- Formatting requirements
- Review criteria
- Submission mechanism
- Cost-sharing requirements
- Application limits
- Special restrictions

Classify each field as:

- **Correct and complete**
- **Partially correct**
- **Incorrect**
- **Omitted**
- **Not applicable**

### B. Grounding and Traceability

For each consequential claim, determine whether it is:

- Supported by the controlling source
- Linked to the correct section or page
- Supported by a non-controlling or outdated source
- Unsupported
- Contradicted by the source

### C. Uncertainty Handling

Measure whether the agent:

- States when information is not identified.
- Asks for missing information only when it materially affects the task.
- Avoids converting ambiguity into a firm conclusion.
- Avoids making final eligibility or compliance determinations.
- Separates fact, inference, concern, and recommendation.

### D. Fit Assessment Quality

Expert reviewers rate:

- Accuracy of alignment claims
- Accuracy of mismatch claims
- Identification of eligibility concerns
- Recognition of missing information
- Quality of next-step recommendations
- Appropriateness of the strong, possible, or weak classification

Use a 1-to-5 scale and collect a brief rationale for low scores.

### E. Plan Quality

Rate checklists and timelines for:

- Completeness
- Correct categorization of requirements
- Logical sequencing
- Realistic dependencies
- Visibility of unresolved institutional deadlines
- Absence of invented requirements
- Actionability

### F. Draft Outline Quality

Rate whether the outline:

- Follows required sponsor sections
- Maps content to review criteria
- Avoids unsupported factual claims
- Uses clear placeholders
- Identifies missing evidence
- Provides an actionable drafting structure

### G. Efficiency and User Experience

Measure:

- Time to first usable analysis
- Total task time
- Number of corrections required
- Completion rate
- System Usability Scale score, if the study team chooses a validated usability instrument
- User-rated usefulness and trust on 1-to-5 scales
- Qualitative feedback on confusing, risky, or especially valuable behavior

## 11. Proposed Release Criteria

These thresholds should be treated as initial targets and refined with research-administration leadership.

### Critical Requirements

- **100% accuracy** for sponsor deadlines in the benchmark.
- **100% accuracy** for explicit application limits and required letters of intent.
- **No fabricated eligibility rules, requirements, citations, page limits, or institutional deadlines.**
- **No final compliance or eligibility determinations presented as authoritative.**

### Overall Performance

- At least **95% correct and complete** across critical extraction fields.
- At least **90% correct and complete** across all scored extraction fields.
- At least **90% of consequential claims** linked to the correct controlling source location.
- At least **4 out of 5** average expert rating for checklist usefulness and proposal-outline usefulness.
- At least **80% task completion** without expert intervention during the faculty pilot.

Any critical error should trigger correction and full regression testing before expansion.

## 12. Error Taxonomy

Record every failure using one or more categories:

1. Deadline error
2. Eligibility error
3. Funding-limit error
4. Required-component omission
5. Page-limit or formatting error
6. Review-criteria omission
7. Outdated or superseded source
8. Sponsor requirement mislabeled as university requirement
9. Recommendation mislabeled as a requirement
10. Unsupported factual claim
11. Fabricated citation or source
12. Overconfident fit assessment
13. Final compliance determination
14. Invented institutional deadline or policy
15. Privacy or confidentiality concern
16. Poor usability or unclear response structure

Prioritize errors by severity, likelihood, and detectability.

## 13. Analysis Plan

### Quantitative Analysis

Calculate:

- Accuracy and omission rates by field
- Critical-error rate
- Grounding rate
- Mean expert ratings by task
- Performance by discipline, sponsor type, and complexity
- Median task time with and without the agent, if a comparison condition is used
- Inter-rater agreement for expert-coded fields

Use descriptive statistics for the initial MVP. With a larger sample, compare performance across task types or participant groups using appropriate inferential methods.

### Qualitative Analysis

Use thematic coding for faculty and expert comments. Likely themes include:

- Trust
- Transparency
- Cognitive load
- Time savings
- Source usability
- Missing context
- Overconfidence
- Workflow fit
- Desired integrations

Use the error taxonomy to connect qualitative concerns with measurable technical failures.

## 14. Ethics, Privacy, and Governance

Before involving human participants or collecting identifiable feedback, consult the institution's research oversight process to determine whether review is required.

Key protections:

- Use anonymized or synthetic research concepts during early testing.
- Do not upload confidential sponsor reviews, controlled data, protected student records, unpublished inventions, or export-controlled information unless the environment and study are explicitly approved for that content.
- Collect the minimum participant information needed.
- Define access, retention, deletion, and incident-response procedures.
- Tell participants that outputs require verification against authoritative sponsor and university sources.
- Keep a record of agent versions, source versions, prompts, and configuration changes.

## 15. Roles

| Role | Responsibilities |
|---|---|
| Principal investigator or project lead | Study oversight, decisions, reporting, and risk acceptance |
| Research administrator | Reference answers, requirement validation, error review, and release criteria |
| Faculty reviewers | Disciplinary relevance, fit assessment, and usability feedback |
| Agent developer | Configuration, source integration, logging, and version control |
| Information security or privacy representative | Data classification, access, retention, and risk review |
| Accessibility reviewer | Keyboard access, screen-reader compatibility, contrast, and accessible output structure |

## 16. Proposed Timeline

### Weeks 1–2: Preparation

- Confirm scope and governance.
- Select announcements and research concepts.
- Create the scoring rubric and error taxonomy.

### Weeks 3–4: Reference Set

- Prepare expert reference answers.
- Resolve ambiguous requirements.
- Label critical fields and controlling source locations.

### Weeks 5–6: MVP Configuration

- Configure the four core tasks.
- Add source hierarchy and safety rules.
- Create standardized output templates.

### Weeks 7–8: Benchmark Testing

- Run all test cases.
- Score outputs independently.
- Adjudicate disagreements and classify failures.

### Weeks 9–10: Revision and Regression Testing

- Revise prompts, behavior guidance, or source structure.
- Rerun the full benchmark.

### Weeks 11–12: Faculty Pilot

- Conduct moderated or lightly supported task sessions.
- Collect timing, usability, trust, and correction data.

### Weeks 13–14: Analysis and Recommendation

- Analyze results.
- Document limitations.
- Decide whether to stop, revise, or proceed to a limited production pilot.

## 17. Anticipated Limitations

- A small test set may not represent all sponsors, disciplines, or announcement structures.
- Funding announcements and sponsor webpages can change after testing.
- Expert reviewers may disagree about apparent fit or proposal quality.
- Faculty may behave differently in a study than during a live deadline.
- Results may depend on the exact agent model, configuration, source indexing, and interface version.
- A correct solicitation analysis does not demonstrate that a proposal is competitive or fundable.
- Internal budget, compliance, and submission rules may be too context-dependent for reliable automation.
- Time savings could be offset if users must perform extensive verification or correction.

## 18. Decision Rules After the Study

### Proceed to a Limited Pilot If

- All critical release criteria are met.
- No unresolved high-severity privacy or security issues remain.
- Faculty and research administrators judge the outputs to be actionable.
- The agent consistently directs users back to authoritative sources for consequential decisions.

### Revise Before Pilot If

- The agent has noncritical omissions but shows clear time-saving value.
- Fit assessments are useful but inconsistently calibrated.
- Citations or source locations need better presentation.
- Institutional procedures are not clearly separated from sponsor requirements.

### Stop or Narrow the Scope If

- Critical deadlines, eligibility rules, or required components remain unreliable.
- The agent fabricates material requirements or citations.
- Verification takes as long as the faculty member's existing process.
- Confidentiality or governance requirements cannot be satisfied.

## 19. Deliverables

1. Grant Compass MVP configuration
2. Curated benchmark of announcements and anonymized research concepts
3. Expert-validated reference answers
4. Scoring rubric and error taxonomy
5. Benchmark results and failure analysis
6. Faculty usability findings
7. Revised agent instructions and source architecture
8. Go, revise, or stop recommendation for a limited pilot

## 20. Immediate Next Steps

1. Recruit one sponsored-research administrator and two faculty reviewers.
2. Select 10 diverse funding announcements.
3. Prepare 10 anonymized research concepts.
4. Create reference answers for the highest-risk fields first: deadlines, eligibility, application limits, required components, page limits, funding limits, and review criteria.
5. Configure the four standardized tasks.
6. Run three pilot cases before scoring the full benchmark to confirm that the rubric is usable.

---

## Appendix A: Reviewer Scorecard

### Critical Fields

- [ ] Deadline correct
- [ ] Time zone correct when specified
- [ ] Letter-of-intent requirement correct
- [ ] Eligibility accurately represented
- [ ] Application limits captured
- [ ] Funding limits correct
- [ ] Required components complete
- [ ] Page limits correct
- [ ] Review criteria complete
- [ ] Source locations accurate

### Safety and Trust

- [ ] No fabricated facts or citations
- [ ] No unsupported eligibility conclusion
- [ ] No compliance determination
- [ ] No invented institutional deadline
- [ ] Unknown information clearly identified
- [ ] Sponsor requirements separated from institutional requirements and recommendations

### Usefulness

Rate each item from 1 (poor) to 5 (excellent):

- Fit assessment: ___
- Checklist: ___
- Timeline: ___
- Proposal outline: ___
- Clarity: ___
- Actionability: ___
- Overall trustworthiness: ___

## Appendix B: Minimum Agent Output Structure

Every opportunity analysis should display:

1. **Critical dates and deadlines**
2. **Eligibility and application limits**
3. **Funding and project-period information**
4. **Required proposal components**
5. **Page and formatting requirements**
6. **Review criteria**
7. **Apparent research fit**
8. **Potential mismatches or unresolved questions**
9. **Sponsor-required actions**
10. **University-required actions, when supported by approved sources**
11. **Recommended practices, clearly labeled**
12. **Source references**
13. **Next three actions**
