# Grant Compass Knowledge

> **One-Sentence Summary**: Gives Grant Compass the FSU context, matching rubric, response templates, and source rules it needs to turn funding information into useful, verifiable next steps.

[Back to Main Catalog](../README.md) · [Grant Compass Setup](../Grant-Compass-Agent/README.md)

---

## Overview

Knowledge supplies the reference material an agent consults while working. Grant Compass uses it to understand FSU routing, compare projects consistently, organize results, and distinguish authoritative evidence from discovery leads. The system prompt defines its role; the six companion skills define its workflows; these files provide the reusable context those workflows need.

This folder provides a compact example pack adapted from the existing [detailed Grant Compass knowledge packets](../Grant-Compass-Agent/Knowledge%20files/). It follows the other examples' setup, file-purpose, sample-use, and customization format. It adds no new verified policy, deadline, rate, or source approval.

## What Knowledge the Agent Uses and Why

| Knowledge file | What it contains | Why Grant Compass uses it | Skills that use it |
| :--- | :--- | :--- | :--- |
| [`01_fsu_routing.md`](./01_fsu_routing.md) | FSU office routing, limited-submission referrals, internal-date prerequisites, and institutional boundaries. | A promising opportunity still needs the correct institutional route. This helps the agent direct questions to appropriate people without claiming approval. | All six skills. |
| [`02_match_rubric.md`](./02_match_rubric.md) | Program, eligibility, mechanism, team, review, and feasibility dimensions; qualitative fit rules. | Keeps comparisons grounded in the project and solicitation rather than keyword overlap or invented funding probabilities. | Finder and Matcher; other skills when a fit assessment is requested. |
| [`03_output_templates.md`](./03_output_templates.md) | Search results, opportunity briefs, match assessments, limit checks, checklists, timelines, routing responses, and outlines. | Makes important requirements, blockers, sources, and next actions easy to find and compare across responses. | All six skills, using the format relevant to the task. |
| [`04_source_registry.md`](./04_source_registry.md) | Source categories, links to the detailed registry, approval statuses, evidence rules, and retrieval fallback behavior. | Prevents a search result, outdated file, or API summary from being presented as a current controlling requirement. | All six skills. |

## How to Add This Knowledge in ArtesAI

1. Follow the [Grant Compass setup guide](../Grant-Compass-Agent/README.md) to create the six skills and Personal Agent.
2. In the agent builder's **Knowledge & Tools** step, upload the four numbered Markdown files in this folder. Preserve their filenames because the skills refer to them by name.
3. For live work, also upload the current detailed [`04_source_registry.md`](../Grant-Compass-Agent/Knowledge%20files/04_source_registry.md), **replacing** this pack's compact file of the same name. That detailed file carries the source-by-source URLs, statuses, and retrieval limits. The compact registry defaults live retrieval to unavailable when that configuration is absent.
4. Use either this compact pack or the detailed packet set as the baseline. Avoid uploading two versions of the same filename together. The detailed set remains the maintained source for source approvals and the extended workflows.
5. Add a current official solicitation and incorporated instructions for the opportunity being analyzed. Add current FSU policy and closure information if asking for an internal-date calculation.
6. Test with the [fictional HeatReady Florida input](../Grant-Compass-Agent/example-input.md) and compare with the [worked output](../Grant-Compass-Agent/example-output.md).

Upload the knowledge files as reference documents. Put skill instructions in **My Skills** and the [system prompt](../Grant-Compass-Agent/system-prompt.md) in **Specific Instructions**, following the existing example template. This README is for the person building the agent and does not need to be uploaded.

## Stable Knowledge and Information That Must Be Checked

| Keep in reusable knowledge | Obtain from current authoritative evidence |
| :--- | :--- |
| Routing principles and referral boundaries. | Current office responsibilities, policy text, and institutional facts. |
| Qualitative matching dimensions. | The specific program's current scope, eligibility, and application limits. |
| Output layouts and source-reporting fields. | Deadlines, exact times, time zones, amendments, and open/closed status. |
| Internal-date calculation prerequisites. | Current working-day policy, university closures, applicant role, and any pass-through deadline. |
| Budget questions and approval boundaries. | Applicable F&A, fringe, tuition, allowable costs, and cost-sharing rules. |

The packet creation date is not a policy-verification date. Most entries in the existing detailed source registry are marked **Testing**. Do not treat them as approved until the documented ArtesAI acceptance checks have been completed and their status updated by the source owner.

## Optional Knowledge and Why to Add It

| Reference | Use it for | Currency or scope limit |
| :--- | :--- | :--- |
| [FSU context pack](../Grant-Compass-Agent/fsu_grant_compass_context.md) | Additional institutional background and referral context. | Confirm changing details against current official FSU sources. |
| [Develop and Submit Proposal knowledge](../Grant-Compass-Agent/FSU_Develop_Submit_Proposal_Agent_Knowledge.md) | More detailed proposal components, budgeting topics, and submission preparation. | Treat rates, thresholds, and procedural details as needing current confirmation. |
| [2021 proposal policy PDF](../Grant-Compass-Agent/202105-proposal-submission-policy-fsu-policy-7a-19-7.pdf) | Historical policy reference and comparison. | Establish whether it is still controlling before applying its timing rule. |
| Current official solicitation, amendments, FAQ, and incorporated application guide | Program-specific requirements and review criteria. | Confirm the correct competition and controlling version. |
| Current departmental checklist or writing template supplied by the user | Local review milestones and document organization. | Confirm applicability; sponsor-mandated sections and limits still control. |
| Nonconfidential project concept supplied by the researcher | Research aims, methods, budget estimate, partners, and readiness. | Distinguish proposed activities from established results and confirmed commitments. |

The [research plan](../Grant-Compass-Agent/grant_compass_research_plan.md) and [recorded test responses](../Grant-Compass-Agent/Test%20Prompts/test_prompts_README.md) support evaluation of the agent. They are not evidence that a funding opportunity is currently open or that a policy interpretation is correct.

## Example: How the Knowledge Changes an Answer

**Input:** “My project studies rural heat resilience among older adults. The training sponsor permits one application per institution, requires a signed community partner letter, and allows $450,000 in total costs over 36 months. Our partners have expressed interest but have not committed. Can we apply, and what should we do next?”

| Knowledge consulted | Expected effect on the response |
| :--- | :--- |
| FSU routing | Flag the institutional limit and refer the internal selection question to Research Development; do not grant permission to apply. |
| Match rubric | Explain topic and mechanism alignment, but classify fit provisionally while material commitments and selection remain unresolved. |
| Output templates | Put blockers first, separate exercise sponsor requirements from recommendations, and provide roles and dependencies. |
| Source registry | Identify the supplied material as fictional exercise evidence; do not invent an official URL, live status, or verification date. |

A good response also keeps indirect costs within the stated total-cost ceiling, identifies the partner letter as outstanding, and leaves the FSU internal deadline unresolved without current policy and closure information.

## Knowledge Check Before Using the Agent

- [ ] The four numbered knowledge files are available to the agent.
- [ ] The active source registry has source-specific statuses and limits for any live retrieval.
- [ ] Current sponsor evidence is distinguished from background files and exercise facts.
- [ ] Institutional and investigator application limits are checked separately.
- [ ] Sponsor requirements, FSU requirements, and recommendations remain distinct.
- [ ] Missing facts lead to explicit unknowns rather than invented deadlines, approvals, partners, or results.
- [ ] Restricted research information, participant records, credentials, and proprietary details are excluded.

## Modify & Play: Ideas to Try

1. **Add your department's context:** Supply a current approved checklist and ask the agent to label local requirements separately from sponsor requirements.
2. **Test a missing source:** Remove the current policy or closure calendar and check that no precise internal deadline is invented.
3. **Test a missing partner:** Change a signed commitment to an expression of interest and check that the required letter becomes an unresolved blocker.
4. **Try another discipline:** Replace HeatReady Florida with a nonconfidential arts, humanities, education, or laboratory concept while keeping the same evidence and matching rules.

When the detailed knowledge changes, review the corresponding compact packet here. Keep live approval records in the detailed registry rather than maintaining a second independent approval list.
