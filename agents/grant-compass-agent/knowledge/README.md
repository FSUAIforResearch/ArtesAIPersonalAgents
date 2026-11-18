# Grant Compass Knowledge Pack

> **One-Sentence Summary**: Four upload-ready Markdown reference files (`01`–`04`) that you can attach in ArtesAI's **Step 3: Knowledge & Tools** to give Grant Compass FSU office routing URLs, qualitative match criteria, response templates, and official sponsor directories.

[**⬅ Back to Grant Compass Setup**](../README.md) · [**⬅ Back to Main Catalog**](../../../README.md)

---

## Overview

In ArtesAI, **Step 3: Knowledge & Tools** lets you upload reference documents that your Personal Agent can consult across every conversation.

The four Markdown files in this folder (`01_fsu_routing.md` through `04_source_registry.md`) are formatted as **direct, upload-ready ArtesAI knowledge files**—with no YAML frontmatter or repository meta-commentary—so you can drop them straight into your agent's Knowledge base.

---

## What Each Knowledge File Contains

| Upload File | What It Gives the Agent in ArtesAI | When the Agent Uses It |
| :--- | :--- | :--- |
| [`01_fsu_routing.md`](./01_fsu_routing.md) | **FSU Office of Research Routing Matrix** (with direct URLs for SRA, FSURF, Research Development, Limited Submissions, Internal Funding, SRA Facts Sheet, RAMP, IRB/OHSP, ACUC, and RISE), plus the 6 FSU Limited-Submission statuses and internal-deadline prerequisites. | Used across all 5 skills to route questions to the right FSU office and enforce internal-deadline guardrails. |
| [`02_match_rubric.md`](./02_match_rubric.md) | **6-Dimension Qualitative Match Rubric**, the 4 fit classifications (`Strong apparent fit`, `Possible fit`, `Weak apparent fit`, `Provisional`), Framing Opportunities vs. Substantive Gaps rules, and the 4 action decisions (`Pursue`, `Investigate Further`, `Monitor`, `Do Not Pursue`). | Used by `funding-opportunity-finder` (`/find-funding`) and `research-opportunity-matcher` (`/match-opportunity`). |
| [`03_output_templates.md`](./03_output_templates.md) | **Standard Response Templates** for all 5 workflows (Funding Search Shortlist, Opportunity Brief & Limited-Submission Check, Research-to-Opportunity Match, 3-Tier Proposal Checklist & Timeline, and Sponsor-Aligned Proposal Outline). | Used by all 5 skills to keep tables, headings, and blocker-first formatting consistent. |
| [`04_source_registry.md`](./04_source_registry.md) | **Directory of Official FSU & External Sponsor Sources** (12 FSU Office of Research pages + 10 major federal/agency portals including Grants.gov, NIH, NSF, NSF PAPPG, IES, NEH, NEA, USDA NIFA, DOE, NASA NSPIRES, and HRSA) plus blocked-site fallback rules. | Used during live web discovery (`/find-funding`) and solicitation verification (`/verify-opportunity`). |

---

## How to Upload These Files into ArtesAI (`Step 3: Knowledge & Tools`)

1. Open your **Grant Compass** agent in the ArtesAI Agent Builder and go to **Step 3 — Knowledge & Tools**.
2. Upload the four numbered Markdown files from this folder (do **not** upload `README.md`):
   - `01_fsu_routing.md`
   - `02_match_rubric.md`
   - `03_output_templates.md`
   - `04_source_registry.md`
3. Keep their exact filenames (`01_fsu_routing.md`–`04_source_registry.md`) so the agent's system prompt and skills can reference them by name.
4. *(Optional)* In **Step 3 — Knowledge & Tools**, you can also add any of the official URLs listed in [`04_source_registry.md`](./04_source_registry.md) (such as `https://www.research.fsu.edu/limitedsubmission/` or `https://www.research.fsu.edu/research-offices/sra/facts-sheet/`) as live Website Knowledge Sources.
