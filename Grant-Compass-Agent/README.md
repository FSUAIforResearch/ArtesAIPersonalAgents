# Grant Compass

> **One-Sentence Summary**: Helps FSU faculty and research staff find and verify funding opportunities, assess research fit, check limited submissions, and build proposal plans and sponsor-aligned outlines.

[**Back to Main Catalog**](../README.md)

---

## Overview

Grant Compass turns a research concept and current sponsor documents into an evidence-based funding shortlist, opportunity brief, qualitative fit assessment, proposal checklist, timeline, or editable outline. It preserves the distinction between sponsor requirements, FSU requirements, and recommendations, while directing institutional decisions to the responsible FSU office.

This example adapts the existing Grant Compass instructions, six skills, knowledge packets, and HeatReady Florida test scenario. Start with the self-contained fictional solicitation in the sample before testing live discovery.

- **Recommended Model in ArtesAI**: A model available in your account that supports web search, document analysis, and structured long-form responses; use moderate reasoning and low creativity where those controls are available.
- **Estimated Setup Time**: ~15–20 minutes for six skills and four knowledge files, plus live-source acceptance testing.

## How to Build This Agent & Its Skills in ArtesAI

Create the companion skills first, then build and test the Personal Agent in the Preview pane. The existing `Skills/` directory is retained; links below use its exact capitalization.

### Part 1: Create the Companion Skills First (`Settings → My Skills`)

1. Open your **Profile / Account name → Settings → My Skills → + New Skill**.
2. For each file below, copy the YAML `name:` and `description:` values into **Name** and **Description**. Each description is under 300 characters.
3. Leave **Always On** unchecked (**Ad Hoc**).
4. Copy only the Markdown body below the second `---` into **Skill Instructions**, then click **Create**.

| Skill file / Name | Request shorthand | When to attach |
| :--- | :--- | :--- |
| [`funding-opportunity-finder`](./Skills/Grant_Compass_Funding_Opportunity_Finder.md) | `/find-funding` | Search for a short, verified list of opportunities matching a research concept. |
| [`funding-opportunity-verifier`](./Skills/Grant_Compass_Funding_Opportunity_Verifier.md) | `/verify-opportunity` | Extract current requirements, deadlines, limits, and unknowns from one opportunity. |
| [`research-opportunity-matcher`](./Skills/Grant_Compass_Research_Opportunity_Matcher.md) | `/match-opportunity` | Compare project facts with verified sponsor requirements using qualitative fit categories. |
| [`fsu-limited-submission-checker`](./Skills/Grant_Compass_FSU_Limited_Submission_Checker.md) | `/check-limited` | Separate institutional and investigator limits and check the FSU internal process. |
| [`fsu-proposal-planner`](./Skills/Grant_Compass_FSU_Proposal_Planner.md) | `/plan-proposal` | Build a checklist and timeline with roles, dependencies, and verified internal-date inputs. |
| [`sponsor-aligned-proposal-outliner`](./Skills/Grant_Compass_Sponsor_Aligned_Proposal_Outliner.md) | `/outline-proposal` | Mirror required sections and map them to published review criteria. |

These shorthands are text triggers described in the skills, not automatically registered platform commands. Attach the relevant skill through **+ → Skills >**; ordinary requests also trigger its workflow.

### Part 2: Create the Personal Agent

#### 0. Launch Quick Create

Open **Explore Agents → My Agents → + Create**, enter **Grant Compass**, and click **Let's go**.

#### 1. Instructions (System Prompt)

Copy all of [`system-prompt.md`](./system-prompt.md) into **Specific Instructions**. Following this repository's template, clear the editable default **Platform Instructions** boilerplate in the builder. The short system prompt contains the rules needed on every turn; detailed workflows stay in the skills and knowledge files.

Use this short prompt for the example build. The existing [`grant_compass_agent_instructions_updated.md`](./grant_compass_agent_instructions_updated.md) remains the extended design reference; pasting both would duplicate instructions.

#### 2. Name & Identity

- **Name**:
  ```text
  Grant Compass
  ```
- **Short Description**:
  ```text
  Helps FSU faculty and research staff find and verify funding, assess fit, check limited submissions, and plan sponsor-aligned proposals.
  ```
- **Welcome Message**:
  ```markdown
  Welcome to **Grant Compass**!

  Paste a short, nonconfidential research concept, an official funding URL, or a solicitation document. Include your approximate budget, project duration, and submission window when relevant.

  Attach companion skills using **+ → Skills >**:
  - `funding-opportunity-finder` — find funding (`/find-funding`).
  - `funding-opportunity-verifier` — verify a solicitation (`/verify-opportunity`).
  - `research-opportunity-matcher` — assess apparent fit (`/match-opportunity`).
  - `fsu-limited-submission-checker` — check application limits (`/check-limited`).
  - `fsu-proposal-planner` — create a checklist and timeline (`/plan-proposal`).
  - `sponsor-aligned-proposal-outliner` — create an outline (`/outline-proposal`).

  Start with one skill or attach several for a staged workflow. Please do not share participant records, credentials, restricted research information, or unpublished patentable details. Grant Compass supports preparation; institutional approvals and submission remain with authorized people.
  ```

#### 3. Knowledge & Tools

For a template-style explanation of **what knowledge Grant Compass uses and why**, see the [Knowledge example and compact upload pack](../Knowledge/README.md). Use that compact pack or the detailed set below as your baseline; for live retrieval, retain the detailed source registry so source-specific permissions and limits are available. Avoid uploading two versions of the same filename together.

Upload these four core knowledge packets, preserving their filenames so the skills can refer to them:

| File | Purpose |
| :--- | :--- |
| [`01_fsu_routing.md`](./Knowledge%20files/01_fsu_routing.md) | Office routing, referral language, and institutional boundaries. |
| [`02_match_rubric.md`](./Knowledge%20files/02_match_rubric.md) | Qualitative fit dimensions and classification rules. |
| [`03_output_templates.md`](./Knowledge%20files/03_output_templates.md) | Briefs, search results, match assessments, checklists, timelines, and outlines. |
| [`04_source_registry.md`](./Knowledge%20files/04_source_registry.md) | Source scope, status, retrieval limits, and acceptance tests. |

**Before live use:** Most source-registry entries are currently **Testing**, not **Approved**. Run the registry's website acceptance checklist in ArtesAI and have the source owner record the outcome before promoting an entry. The Finder permits only **Approved** or **Conditional** sources; do not silently treat Testing entries as approved. An agent can analyze supplied documents and run the fictional example while source testing is pending, but it must disclose that live status has not been verified.

Upload current official solicitations or application guides as needed. The supplied [2021 policy PDF](./202105-proposal-submission-policy-fsu-policy-7a-19-7.pdf), [context pack](./fsu_grant_compass_context.md), and [proposal knowledge draft](./FSU_Develop_Submit_Proposal_Agent_Knowledge.md) are optional background references. Confirm their currency against official sources before relying on policy details. Knowledge-file review dates do not by themselves prove a policy or deadline is current.

No API is required for the baseline example. If an approved discovery API is configured later, use its records as leads and verify consequential requirements against the official solicitation. Keep credentials out of prompts and uploaded files. This build does not provide authenticated RAMP access.

#### 4. Capabilities & Model

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | `Off` | Grant analysis and proposal planning use text and documents. |
| **Add Files & Images** | `On` | Supports solicitation PDFs, guides, and nonconfidential concept notes. |
| **Web Search** | `On` for live work | Current status, amendments, policies, and limited-submission listings need verification using permitted sources. |
| **Generate Artifacts** | `On` | Makes checklists, tables, and editable outlines easier to review. |
| **Model (`Change` button)** | Available model supporting the enabled tools | Use low creativity and moderate reasoning where available; allow enough response space for structured analysis. |

The fictional sample works without web access. When live retrieval is unavailable, the agent should analyze only the supplied evidence, mark unknowns, and avoid precise FSU internal dates.

#### 5. Starter Prompts

Use **Add Starter Prompt** to enter these title/prompt pairs:

| Title | Prompt |
| :--- | :--- |
| Find funding | Find current funding for the research concept I provide. Use permitted official sources, verify each recommended candidate, and separate unverified leads. Ask only for missing facts that materially affect the search. |
| Verify a solicitation | Analyze the official solicitation I provide. Put blockers first; identify deadlines with time zones, eligibility, application limits, required components, review criteria, sources, and unresolved facts. |
| Assess project fit | Compare my research concept with this verified opportunity. Explain alignment, mismatches, eligibility concerns, and blockers using qualitative fit categories. |
| Check limited submission | Check the sponsor's exact institutional and investigator limits and the current FSU internal process. Do not treat an absent listing as permission to apply. |
| Plan and outline | From this verified opportunity, build a proposal checklist, a timeline with roles and dependencies, and an outline mapped to review criteria. Separate requirements from recommendations and leave unsupported dates unresolved. |

### Part 3: Test with Skills in the Preview Pane & Click Create

1. In **Preview**, use **+ → Skills >** to attach the Verifier, Matcher, Limited Submission Checker, Planner, and Outliner for the combined sample. For a smaller first test, attach only the Verifier and request only the opportunity brief.
2. Paste the complete prompt from [`example-input.md`](./example-input.md). Keep its fictional-source and no-live-verification instructions intact.
3. Compare against [`example-output.md`](./example-output.md). Wording can vary; the important checks are the institutional limit, unconfirmed partner, qualitative fit, exact supplied sponsor deadline, unchanged sponsor section titles, and absence of an invented FSU internal deadline.
4. Click **Create** to save the agent.
5. After source acceptance testing, attach the Finder and test a live search using a nonconfidential research concept. Check the official links, source dates, and current status yourself. The [original test transcripts](./Test%20Prompts/test_prompts_README.md) offer additional scenarios, not evidence that opportunities remain open.

## Files in This Folder

| File / Folder | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Short copy-pasteable role, workflow, and guardrails. |
| [`Skills/`](./Skills/) | Six companion skills with template-compatible YAML metadata and text triggers. |
| [`example-input.md`](./example-input.md) | Self-contained HeatReady Florida concept and fictional solicitation. |
| [`example-output.md`](./example-output.md) | Worked brief, fit assessment, limit check, plan, and outline. |
| [`Knowledge files/`](./Knowledge%20files/) | Four supporting knowledge packets. |
| [`grant_compass_agent_instructions_updated.md`](./grant_compass_agent_instructions_updated.md) | Extended agent design reference. |
| [`fsu_grant_compass_context.md`](./fsu_grant_compass_context.md) | Background FSU context; verify changing information before use. |
| [`FSU_Develop_Submit_Proposal_Agent_Knowledge.md`](./FSU_Develop_Submit_Proposal_Agent_Knowledge.md) | Background proposal-development reference. |
| [`202105-proposal-submission-policy-fsu-policy-7a-19-7.pdf`](./202105-proposal-submission-policy-fsu-policy-7a-19-7.pdf) | Historical policy reference; establish current controlling policy before calculating dates. |
| [`grant_compass_research_plan.md`](./grant_compass_research_plan.md) | MVP evaluation plan. |
| [`Test Prompts/`](./Test%20Prompts/test_prompts_README.md) | Existing discovery scenarios and recorded responses. |

## Context-Saving Checklist (For Agent Creators)

1. Keep setup directions in this README and the welcome message.
2. Paste only the skill body into **Skill Instructions**; put YAML metadata in its separate fields.
3. Use the short system prompt, under approximately 250 words, and attach only the skills needed for the task.
4. Upload the four core knowledge packets once. Add optional background files only when needed and verify changing facts live.

## Modify & Play: Ideas to Try

1. **Focus discovery on your discipline:** Add a nonconfidential lab profile and sponsor preferences; retain source verification and explicit exclusions.
2. **Compare lead and subrecipient planning:** Change FSU's role in the sample. Check that the planner asks for the pass-through entity's document deadline rather than assuming the prime deadline applies to FSU.
3. **Test missing information:** Remove the sponsor time zone or partner commitment. The agent should label the gap and continue supported analysis.
4. **Test a limited-submission trap:** Say no FSU listing was found. The sponsor's one-per-institution limit should still trigger referral to Research Development.
5. **Customize the outline:** Supply your department's writing template, but keep the sponsor's mandatory structure and limits controlling.
