# Grant Compass

> **One-Sentence Summary**: Helps FSU faculty and research staff discover and verify funding opportunities (including FSU limited-submission checks), evaluate project-to-sponsor fit, and build proposal checklists, timelines, and sponsor-aligned outlines.

[**⬅ Back to Main Catalog**](../../README.md)

---

## Overview

Finding the right grant, verifying complex solicitation rules, checking whether FSU restricts the number of institutional applications, and organizing a proposal timeline takes hours of cross-checking across sponsor websites and university policies.

**Grant Compass** combines low-friction funding discovery (starting from as little as two sentences describing what you study and what you want funded) with rigorous solicitation verification, qualitative project-fit evaluation, FSU limited-submission checks, backward-planned proposal checklists/timelines, and review-criteria-mapped outlines. It strictly separates **Sponsor Required**, **FSU Required**, and **Recommended Practice** items while directing institutional approvals to the appropriate FSU offices (`Research Development`, `SRA`, `FSURF`).

- **Recommended Model in ArtesAI**: `OpenAI (gpt-5.6-luna)` (Default, Reasoning Effort: `Medium`/`High`) or `Anthropic (claude-sonnet-5)` (Creativity: `Low`)
- **Estimated Setup Time**: ~5–10 minutes (works immediately with its 5 skills; optional Knowledge pack available for extended FSU routing & source-registry rules)

---

## How to Build This Agent & Its Skills in ArtesAI

In ArtesAI, **create the companion Skills first** under your account **Settings → My Skills** (Part 1). That way, when you build the **Personal Agent** (Part 2), you can immediately attach and test the skills inside the right-hand **Preview** pane before clicking **Create** (Part 3).

### Part 1: Create the Companion Skills First (`Settings → My Skills`)

1. Click your **Profile / Account box** at the bottom-left of the maroon FSU sidebar and click **Settings**.
2. Click **My Skills** on the left, then click **`+ New Skill`** in the top-right corner.
3. Open each standard skill file below and copy its parts into the **Create Skill** modal (**Name** = `name:` from the top `---` block, **Description** = `description:` from the top `---` block, leave **Always On** unchecked/`Ad Hoc`, and paste only the Markdown body below the second `---` into the dark editor box):
   - **[`funding-opportunity-finder`](./skills/funding-opportunity-finder.md)** (`/find-funding`): Turns a short, non-confidential research description and funding need into a verified shortlist of 3–7 current grant opportunities with fit classifications and blockers.
   - **[`funding-opportunity-verifier`](./skills/funding-opportunity-verifier.md)** (`/verify-opportunity` / `/check-limited`): Extracts deadlines (with time zones), eligibility, award limits, required components, and review criteria from an official solicitation, and runs an **FSU Limited-Submission Check** (separating institutional vs. PI limits).
   - **[`research-opportunity-matcher`](./skills/research-opportunity-matcher.md)** (`/match-opportunity`): Compares a non-confidential project concept against a solicitation using qualitative fit categories (`Strong apparent fit`, `Possible fit`, `Weak apparent fit`, `Provisional`), separating framing opportunities from substantive gaps and ending with a `Pursue` / `Investigate Further` / `Monitor` / `Do Not Pursue` decision.
   - **[`fsu-proposal-planner`](./skills/fsu-proposal-planner.md)** (`/plan-proposal`): Builds a 3-tier proposal checklist (`Sponsor Required`, `FSU Required`, `Recommended Practice`) and a backward-planned milestone timeline with roles, dependencies, and FSU internal-date guardrails.
   - **[`sponsor-aligned-proposal-outliner`](./skills/sponsor-aligned-proposal-outliner.md)** (`/outline-proposal`): Creates an editable, section-by-section proposal outline preserving mandatory sponsor headings and page limits, paired with `[PLACEHOLDER]` prompts for missing evidence and a **Review-Criteria Crosswalk** table.

---

### Part 2: Create the Personal Agent

#### 0. Launch "Quick Create"
1. In the left maroon FSU sidebar, click **Explore Agents** (or switch to the **Agents** tab).
2. Under **My Agents** (*Agents created by me*), click the **`+ Create`** button next to the **My Agents** heading (or click the dashed **`+ Create`** card).
3. In the **Quick Create** popup box, enter **`Grant Compass`** as the **Agent Name** and click **`Let's go`**.

#### 1. Instructions (System Prompt)
1. Open [`system-prompt.md`](./system-prompt.md), copy the text, and paste it into the **Specific Instructions** field.
2. **Remove the Platform Instructions**: Delete/clear the default pre-filled **Platform Instructions** to save on context tokens.

#### 2. Name & Identity
In the **Name & Identity** panel, fill in the three fields below (you'll see them update live in the right-hand **Preview** pane):

- **Name**:
  ```text
  Grant Compass
  ```
- **Short Description**:
  ```text
  Helps FSU faculty and research staff find and verify funding, evaluate project fit, check limited submissions, and plan sponsor-aligned proposals.
  ```
- **Welcome Message** *(replace the default "Welcome to the Chat!" text in the rich-text editor box)*:
  ```text
  Welcome to Grant Compass!

  Start with a short, non-confidential description of your research and what you want funded—or paste an official grant URL or solicitation document. (You do not need to upload raw research data, a full proposal, or a CV.)

  How to Attach Companion Skills (Click "+" in the chat bar -> "Skills >"):
  • funding-opportunity-finder (/find-funding) — Find a verified shortlist of current grants for your research
  • funding-opportunity-verifier (/verify-opportunity or /check-limited) — Analyze a solicitation & check FSU limited-submission rules
  • research-opportunity-matcher (/match-opportunity) — Evaluate project-to-grant fit and identify gaps
  • fsu-proposal-planner (/plan-proposal) — Build a proposal checklist and backward-planned timeline
  • sponsor-aligned-proposal-outliner (/outline-proposal) — Create a section-by-section outline mapped to review criteria
  ```

#### 3. Knowledge & Tools *(Upload from `./knowledge/`)*
To give **Grant Compass** the full FSU Office of Research routing directory, qualitative match rubric, standard output templates, and official sponsor registry, upload the four ready-to-use Markdown files from [`./knowledge/`](./knowledge/README.md) into **Step 3 — Knowledge & Tools** (preserve their filenames):
- [`knowledge/01_fsu_routing.md`](./knowledge/01_fsu_routing.md) — FSU Office of Research routing matrix (SRA, FSURF, Research Development, Limited Submissions, RAMP, IRB, ACUC, RISE) and internal-deadline rules
- [`knowledge/02_match_rubric.md`](./knowledge/02_match_rubric.md) — 6-dimension qualitative fit rubric (`Strong apparent fit`, `Possible fit`, `Weak apparent fit`, `Provisional`) and `Pursue` / `Investigate Further` / `Monitor` / `Do Not Pursue` decision criteria
- [`knowledge/03_output_templates.md`](./knowledge/03_output_templates.md) — Standard response layouts and table structures for all five skills
- [`knowledge/04_source_registry.md`](./knowledge/04_source_registry.md) — Directory of official FSU research pages and federal/agency grant portals (`Grants.gov`, `NIH`, `NSF`, `NEH`, `USDA`, `DOE`, `NASA`, `HRSA`)

*(Note: All five skills also include built-in fallback rules so the agent still functions if you test it before uploading the knowledge pack. See [`knowledge/README.md`](./knowledge/README.md) for details.)*

#### 4. Capabilities & Model
In the **Capabilities & Model** tab, configure the toggles and model as follows:

| Setting | Recommended Value | Why? |
| :--- | :--- | :--- |
| **Image Creation** | **OFF** | Grant discovery, solicitation verification, and proposal planning use text and documents. |
| **Add Files & Images** | **ON** | Lets faculty upload official solicitation PDFs, program guidelines, and non-confidential concept notes. |
| **Web Search** | **ON** | Required for live funding discovery (`/find-funding`) and checking current sponsor deadlines, amendments, and FSU Limited Submissions listings. |
| **Generate Artifacts** | **ON** | Renders opportunity briefs, fit matrices, checklists, timelines, and proposal outlines in a clean side-by-side panel. |
| **Model (`Change` button)** | • **OpenAI**: `gpt-5.6-luna` *(Default, `128,000` max tokens, set **Reasoning Effort**: `Medium`/`High`)*<br>• **Anthropic**: `claude-sonnet-5` *(set **Creativity**: `Low`)* | Low creativity and strong reasoning keep deadline extraction, eligibility checks, and review-criteria crosswalks strictly grounded in the solicitation. |

#### 5. Starter Prompts *(Optional)*
In **5. Starter Prompts**, click **Add Starter Prompt** and enter the **Title** and **Prompt** fields below, then click **Create**:

| Title | Prompt |
| :--- | :--- |
| `Find Funding (/find-funding)` | `Run /find-funding. Ask me only for the minimum non-confidential information you need (what I study and what I want funded), then search for current grants and explain the strongest matches.` |
| `Verify Solicitation & Limits (/verify-opportunity)` | `Run /verify-opportunity on the official solicitation I provide. Put submission blockers first, extract deadlines with time zones, eligibility, institutional/PI application limits, required components, and review criteria.` |
| `Evaluate Project Fit (/match-opportunity)` | `Run /match-opportunity to compare my non-confidential project summary with this grant. Distinguish framing opportunities from substantive project gaps and give a Pursue / Investigate Further / Monitor / Do Not Pursue recommendation.` |
| `Plan & Outline Proposal (/plan-proposal)` | `Run /plan-proposal and /outline-proposal on this verified opportunity to build a 3-tier checklist, a backward-planned timeline with roles, and a section outline mapped to review criteria.` |

---

### Part 3: Test with Skills in the Preview Pane & Click Create
1. In the **Preview** chat pane, click the **`+` button** in the message bar → hover over **`Skills >`** → attach `funding-opportunity-verifier`, `research-opportunity-matcher`, `fsu-proposal-planner`, and `sponsor-aligned-proposal-outliner` (or attach `funding-opportunity-finder` to test live discovery).
2. Open [`example-input.md`](./example-input.md), copy and paste the self-contained *HeatReady Florida* prompt (or the quick *Pufferfish Toxicology* discovery prompt), and compare the result with [`example-output.md`](./example-output.md).
3. Click **Create** at the bottom of the screen to save your **Grant Compass** agent!

---

## Files in This Folder

| File / Folder | Purpose |
| :--- | :--- |
| [`system-prompt.md`](./system-prompt.md) | Copy-pasteable role, workflow, and anti-hallucination / data-minimization guardrails |
| [`skills/funding-opportunity-finder.md`](./skills/funding-opportunity-finder.md) | Skill (`/find-funding`) for low-friction intake and verified funding discovery |
| [`skills/funding-opportunity-verifier.md`](./skills/funding-opportunity-verifier.md) | Skill (`/verify-opportunity` / `/check-limited`) for solicitation analysis and FSU limited-submission checking |
| [`skills/research-opportunity-matcher.md`](./skills/research-opportunity-matcher.md) | Skill (`/match-opportunity`) for qualitative project-to-grant fit evaluation |
| [`skills/fsu-proposal-planner.md`](./skills/fsu-proposal-planner.md) | Skill (`/plan-proposal`) for 3-tier proposal checklists and backward-planned timelines |
| [`skills/sponsor-aligned-proposal-outliner.md`](./skills/sponsor-aligned-proposal-outliner.md) | Skill (`/outline-proposal`) for sponsor-aligned outlines and review-criteria crosswalks |
| [`example-input.md`](./example-input.md) | Self-contained *HeatReady Florida* solicitation test prompt + quick discovery test prompt |
| [`example-output.md`](./example-output.md) | Worked Opportunity Brief, Limited-Submission Check, Fit Assessment, Checklist/Timeline, and Outline |
| [`knowledge/`](./knowledge/README.md) | Four upload-ready ArtesAI knowledge files (`01_fsu_routing.md`–`04_source_registry.md`) for Step 3 (`Knowledge & Tools`) |

---

## Modify & Play: Ideas to Try

1. **Test the Low-Friction Discovery Intake (`/find-funding`)**:
   - *Try this*: Attach `funding-opportunity-finder` and type just `"I study pufferfish."` Watch how the agent asks only 2 brief questions (what aspect of pufferfish you study and what activities/expenses you need funded) instead of demanding a CV or full proposal.
2. **Compare Lead vs. Subrecipient Planning (`/plan-proposal`)**:
   - *Try this*: Change FSU's role in [`example-input.md`](./example-input.md) from lead applicant to subrecipient. Check that the planner asks for the pass-through university's document deadline rather than assuming the prime sponsor deadline applies to FSU.
3. **Test a Limited-Submission Blocker (`/verify-opportunity`)**:
   - *Try this*: Paste a foundation solicitation with a *"one application per university"* cap and note that no FSU listing was found. Watch how the Verifier flags the institutional limit first and directs you to **FSU Research Development** (`limitedsubmissions@fsu.edu`).
4. **Customize Departmental Routing via Knowledge Files**:
   - *Try this*: Edit [`knowledge/01_fsu_routing.md`](./knowledge/01_fsu_routing.md) or upload your college's internal pre-award review checklist in **Step 3 (Knowledge & Tools)** and ask `/plan-proposal` to include your college's internal review milestone alongside the sponsor requirements.
