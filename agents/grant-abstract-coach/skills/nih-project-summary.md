---
name: nih-project-summary-coach
description: Coaches researchers on their draft NIH SF424 summary documents (30-line Project Summary/Abstract, 2-3 sentence Project Narrative, and Specific Aims) without ghostwriting text. Use when the user types /nih-summary or asks for NIH abstract or aims feedback.
---

# NIH Project Summary, Project Narrative, & Specific Aims Coach (`/nih-summary`)

## When to Apply This Skill
Trigger this skill when the user types `/nih-summary` or asks for coaching and structural feedback on an **NIH Project Summary/Abstract**, **NIH Project Narrative**, or **NIH Specific Aims** draft.

## Step-by-Step Coaching Instructions
Do **not** write or rewrite the NIH summary documents for the user. Coach the researcher on how to revise their own text against **NIH SF424 (R&R) Application Guide** standards:

1. **Audit 1: NIH `Project Summary / Abstract` (Strict Max 30 Lines of Text)**:
   - **Length & RePORTER Readiness**: Check whether the user's draft fits within NIH's strict 30-line limit and is self-contained (with no proprietary/confidential data) for public release on **NIH RePORTER**.
   - **Target NIH Institute/Center (IC) Alignment**: Check whether the draft explicitly connects the health burden and long-term goal to the mission of the target NIH Institute/Center (e.g., NIA, NCI, NIMH, NIGMS, NHLBI).
   - **Completeness Check**: Point out where the author needs to sharpen (a) the clinical/public-health gap, (b) the central hypothesis, (c) the specific aims and research design/methods, or (d) the expected health impact.
2. **Audit 2: NIH `Project Narrative` (Strict 2–3 Sentences Maximum)**:
   - Evaluate the user's draft Public Health Relevance statement (or advise them on which core ideas from their draft to distill if they haven't written one yet).
   - **Lay-Language & Jargon Check**: Flag technical terms in their draft that a layperson or non-specialist reviewer would not immediately understand, and advise how the author can state in 2–3 plain sentences how the work enhances health, lengthens life, or reduces illness and disability.
3. **Audit 3: `Specific Aims` Independence & 4-Paragraph Flow**:
   - Check the user's aims against the classic NIH 4-paragraph architecture:
     1. *Opening Hook & Critical Knowledge Gap*
     2. *Long-Term Goal, Overall Objective, Central Hypothesis, & Rationale*
     3. *Specific Aims 1–3 (Hypotheses, Approaches, & Measurable Endpoints)*
     4. *Innovation & Expected Vertical Advancement (Payoff)*
   - **Aim Interdependence Check**: Explicitly warn the user if Aim 2 or Aim 3 appears dependent on Aim 1 succeeding ("domino effect"), and coach them on how to decouple the aims.
4. **Author Revision Checklist & Guiding Questions**:
   - End with 4–6 targeted questions and revision tasks the researcher should complete in their own words, and offer `/review` (`reviewer-critique-simulator`) for a simulated 3-reviewer NIH study section critique.
