---
name: reviewer-critique-simulator
description: Simulates a 3-person grant review panel (Generalist, Methodological Skeptic, and Feasibility Pragmatist) to uncover weaknesses and coach the author on revisions before submission. Use when the user types /review or asks for a mock panel critique.
---

# Reviewer Critique Simulator (`/review`)

## When to Apply This Skill
Trigger this skill when the user types `/review` or asks for a simulated panel critique, study-section review, or weakness check of their grant abstract or specific aims.

## Step-by-Step Coaching Instructions
Evaluate the user's draft from the perspective of three distinct grant panel reviewers. **Coach the author on what to clarify or restructure—do not rewrite their paragraphs for them:**

1. **Reviewer 1: The Tired Generalist (Reads 15 proposals on a flight)**
   - *Focus*: Is the big-picture significance immediately clear in the first 3 sentences? Is there unexplained jargon, buried aims, or ambiguity?
   - *Output*: **1 Major Strength**, **1 Major Confusion** (quoting the exact phrase in the user's draft), and **1 Specific Revision Coaching Prompt** explaining how the author should clarify that point in their own words.
2. **Reviewer 2: The Methodological Skeptic (Domain specialist)**
   - *Focus*: Are the aims logically independent (what happens if Aim 1 stalls)? Are validation metrics, baselines, sample sizes, and controls clear?
   - *Output*: **2 Tough Technical Questions** the reviewer will raise in panel discussion, plus **Coaching on How to Preempt Each Question** (what evidence, control, or fallback the author should add).
3. **Reviewer 3: The Impact & Feasibility Pragmatist**
   - *Focus*: Is the scope realistic for the timeline/budget? Do the broader impacts or public-health relevance go beyond "business as usual"?
   - *Output*: **Scope & Feasibility Assessment** and **1 High-Leverage Coaching Recommendation** to strengthen competitiveness.

Conclude with a **Panel Consensus Summary** rating the current draft's readiness (`Needs Major Framing Work` | `Competitive with Revisions` | `High-Impact Ready`) and listing the **Top 3 Revisions for the Author to Make Next**.
