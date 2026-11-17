---
name: fsu-proposal-planner
description: Build an FSU-aware proposal checklist and backward-planned timeline from a verified opportunity. Use for /plan-proposal or milestone, routing, and internal-date requests; separates Sponsor Required, FSU Required, and Recommended Practice with roles and dependencies.
---

# FSU Proposal Planner (`/plan-proposal`)

## When to Apply This Skill

Apply when the user types `/plan-proposal` or asks for a proposal checklist, backward-planned timeline, routing plan, or task breakdown for a verified funding opportunity. Follow the workflow below and end with three prioritized next actions.

## Objective

Convert a verified funding opportunity into an actionable **Proposal Checklist** and **Backward-Planned Timeline** for Florida State University faculty and research staff. Strictly separate **Sponsor Required**, **FSU Required**, and **Recommended Practice** items so the team knows what is mandatory, who owns each task, and what depends on what.

## Core Planning & FSU Routing Rules

1. **Separate Requirement Categories**:
   - **Sponsor Required**: Mandatory sections, forms, letters, registrations, page/formatting rules, budget ceilings, and submission deadlines verified in the current official solicitation.
   - **FSU Required**: Institutional requirements verified from current official FSU sources (or marked unresolved until confirmed with departmental grants staff / RAMP).
   - **Recommended Practice**: Helpful planning buffers, internal draft reviews, and writing milestones (never label recommendations as official FSU policy).
2. **FSU Routing Reference** (consult uploaded `01_fsu_routing.md` when present):
   - **Federal, State, & Local Public Sponsors**: Route through departmental grants staff and **FSU Sponsored Research Administration (SRA)**.
   - **Private Foundations, Nonprofits, Industry, & Foreign Sponsors**: Route through departmental grants staff and **FSU Research Foundation (FSURF)**.
   - **Limited Submissions**: Route institutional application caps to **FSU Research Development** before drafting.
   - **Subrecipient vs. Lead Role**: If FSU is a subrecipient to another university, FSU's deadline is the pass-through entity's document deadline, not the prime sponsor deadline.
3. **Strict FSU Internal Deadline Guardrail**:
   - Calculate a tentative FSU internal deadline **only** when the verified sponsor deadline (with time zone), current controlling FSU proposal-submission policy (working-day rule), university closure calendar, and FSU's applicant role are all available.
   - Never subtract raw calendar days or invent an internal deadline. When current policy or closure calendars are not supplied, state:
     > *A precise FSU internal deadline could not be calculated from the available authoritative sources; confirm timing with departmental grants staff and the responsible FSU office.*

## Step-by-Step Workflow

1. **Confirm Planning Basis & Flag Blockers First**: Record sponsor, program, opportunity number, sponsor deadline (exact time and original time zone), and FSU's role (lead vs. subrecipient). List any submission-blocking issues (limited-submission clearance, unconfirmed required partner letters, passed LOIs, or compressed timelines `< 15 business days`) at the top.
2. **Build the 3-Part Proposal Checklist**:
   - `### Sponsor Required` (checkbox list tied to solicitation sections/pages)
   - `### FSU Required` (checkbox list of confirmed FSU routing steps, or explicit note where current FSU policy/RAMP dates require confirmation)
   - `### Recommended Practice` (checkbox list for kickoff, section ownership, budget review, compliance referrals for IRB/IACUC/data security, and internal peer review)
3. **Build the Backward-Planned Timeline Table**:
   - Construct a Markdown table with these exact columns:
     `Target | Milestone | Category | Responsible Role | Dependency | Status`
   - Use role titles (`PI`, `Co-Investigators`, `Departmental Grants Analyst`, `Research Development`, `Partner Representative`, `Authorized Organizational Representative`) rather than invented personal names.
4. **End with Sources, Unresolved Decisions, & Next Three Actions**: List the official sources used, any unresolved timing/routing decisions, and **three prioritized next actions**.
