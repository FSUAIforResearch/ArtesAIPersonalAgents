# Grant Compass Knowledge

> **One-Sentence Summary**: Optional reference packets that give Grant Compass reusable FSU routing rules, a qualitative matching rubric, response templates, and source-verification rules.

[**⬅ Back to Main Catalog**](../README.md) · [**Grant Compass Setup Guide**](../grant-compass-agent/README.md)

---

## Overview

Knowledge supplies the reference material an agent consults while working. **Grant Compass** uses these optional packets to standardize FSU office routing, compare projects consistently, organize results, and distinguish authoritative evidence from discovery leads. The [system prompt](../grant-compass-agent/system-prompt.md) defines its role; the [five companion skills](../grant-compass-agent/README.md) define its workflows; these files provide reusable context those workflows can consult when uploaded in **Step 3 (Knowledge & Tools)**.

---

## What Knowledge the Agent Uses and Why

| Knowledge file | What it contains | Why Grant Compass uses it | Skills that use it |
| :--- | :--- | :--- | :--- |
| [`01_fsu_routing.md`](./01_fsu_routing.md) | FSU office routing, limited-submission referrals, internal-date prerequisites, and institutional boundaries. | A promising opportunity still needs the correct institutional route. This helps the agent direct questions to appropriate people without claiming approval. | All five skills. |
| [`02_match_rubric.md`](./02_match_rubric.md) | Program, eligibility, mechanism, team, review, and feasibility dimensions; qualitative fit rules. | Keeps comparisons grounded in the project and solicitation rather than keyword overlap or invented funding probabilities. | Finder and Matcher; other skills when a fit assessment is requested. |
| [`03_output_templates.md`](./03_output_templates.md) | Search results, opportunity briefs, match assessments, limit checks, checklists, timelines, routing responses, and outlines. | Makes important requirements, blockers, sources, and next actions easy to find and compare across responses. | All five skills, using the format relevant to the task. |
| [`04_source_registry.md`](./04_source_registry.md) | Source categories, approval statuses, evidence rules, and retrieval fallback behavior. | Prevents a search result, outdated file, or API summary from being presented as a current controlling requirement. | All five skills. |

---

## How to Add This Knowledge in ArtesAI

1. Follow the [Grant Compass setup guide](../grant-compass-agent/README.md) to create the five skills and Personal Agent.
2. In the agent builder's **Knowledge & Tools** step, upload the four numbered Markdown files in this folder (`01_fsu_routing.md`, `02_match_rubric.md`, `03_output_templates.md`, and `04_source_registry.md`). Preserve their filenames because the skills refer to them by name.
3. Add a current official solicitation and incorporated instructions for the opportunity being analyzed. Add current FSU policy and closure information if asking for an internal-date calculation.
4. Test with the [fictional HeatReady Florida input](../grant-compass-agent/example-input.md) and compare with the [worked output](../grant-compass-agent/example-output.md).

Upload the knowledge files as reference documents. Put skill instructions in **My Skills** and the [system prompt](../grant-compass-agent/system-prompt.md) in **Specific Instructions**, following the existing example template. This README is for the person building the agent and does not need to be uploaded.

---

## Stable Knowledge vs. Information That Must Be Checked Live

| Keep in reusable knowledge | Obtain from current authoritative evidence |
| :--- | :--- |
| Routing principles and referral boundaries. | Current office responsibilities, policy text, and institutional facts. |
| Qualitative matching dimensions. | The specific program's current scope, eligibility, and application limits. |
| Output layouts and source-reporting fields. | Deadlines, exact times, time zones, amendments, and open/closed status. |
| Internal-date calculation prerequisites. | Current working-day policy, university closures, applicant role, and any pass-through deadline. |
| Budget questions and approval boundaries. | Applicable F&A, fringe, tuition, allowable costs, and cost-sharing rules. |

---

## Example: How the Knowledge Shapes an Answer

**Input:** *“My project studies rural heat resilience among older adults. The training sponsor permits one application per institution, requires a signed community partner letter, and allows \$450,000 in total costs over 36 months. Our partners have expressed interest but have not committed. Can we apply, and what should we do next?”*

| Knowledge consulted | Expected effect on the response |
| :--- | :--- |
| [`01_fsu_routing.md`](./01_fsu_routing.md) | Flag the institutional limit and refer the internal selection question to Research Development; do not grant permission to apply. |
| [`02_match_rubric.md`](./02_match_rubric.md) | Explain topic and mechanism alignment, but classify fit provisionally while material commitments and selection remain unresolved. |
| [`03_output_templates.md`](./03_output_templates.md) | Put blockers first, separate exercise sponsor requirements from recommendations, and provide roles and dependencies. |
| [`04_source_registry.md`](./04_source_registry.md) | Identify the supplied material as fictional exercise evidence; do not invent an official URL, live status, or verification date. |

---

## Modify & Play: Ideas to Try

1. **Add your department's context:** Supply a current approved departmental checklist and ask the agent to label local requirements separately from sponsor requirements.
2. **Test a missing source:** Remove the current policy or closure calendar and check that no precise internal deadline is invented.
3. **Test a missing partner:** Change a signed commitment to an expression of interest and check that the required letter becomes an unresolved blocker.
4. **Try another discipline:** Replace *HeatReady Florida* with a non-confidential arts, humanities, education, or laboratory concept while keeping the same evidence and matching rules.
