---
name: nsf-project-summary-coach
description: Audits a user's draft against NSF PAPPG 1-Page Project Summary rules (Overview, Intellectual Merit, Broader Impacts) and provides section-by-section coaching without rewriting their text. Use when the user types /nsf-summary or asks for NSF abstract feedback.
---

# NSF 1-Page Project Summary Coach (`/nsf-summary`)

## When to Apply This Skill
Trigger this skill when the user types `/nsf-summary` or asks for coaching and compliance feedback on a 1-page **National Science Foundation (NSF) Project Summary**.

## Step-by-Step Coaching Instructions
Do **not** write or rewrite the NSF Project Summary for the user. Coach the researcher on their own text using these steps:

1. **NSF PAPPG Compliance & Heading Check**:
   - Check whether the user's draft is within the **1-page (~450–500 words / ~4,600 characters)** limit and explicitly contains all **three mandatory PAPPG section headings** (`Overview`, `Intellectual Merit`, and `Broader Impacts`).
   - Warn the user that NSF returns proposals without review if any of the three headings are missing or combined.
2. **Sentence Mapping & Section-by-Section Diagnostic**:
   Evaluate how the user's existing sentences map to each required NSF section and advise what to move, sharpen, or add:
   - **`Overview` Coaching**:
     - Does the opening establish the scientific bottleneck and knowledge gap within 2–3 sentences?
     - Are the overarching research goal/hypothesis and the specific research objectives/aims clearly stated with measurable verbs (*quantify, benchmark, validate*) instead of vague verbs (*explore, study*)?
   - **`Intellectual Merit` Coaching**:
     - Identify which sentences in the user's draft explain *how* the work advances fundamental knowledge and methods within or across fields.
     - Point out where the author needs to clarify their novel mechanism, baseline comparisons, or validation metrics.
   - **`Broader Impacts` Coaching**:
     - Flag if the user's draft relies on "baseline research expectations" (e.g., *"we will train graduate students and put code on GitHub"*).
     - Advise how the author can connect their technical research to specific societal outcomes, educational modules, practitioner tools, or FSU/Florida community partners.
3. **Author Revision Blueprint**:
   - Provide a bulleted, section-by-section **Revision Checklist & Guiding Questions** that tells the author exactly which sentences to move, which verbs to upgrade, and which missing numbers/metrics to plug into their own draft.
   - Remind the user they can run `/impacts` (`broader-impacts-coach`) to brainstorm a structured Broader Impacts evaluation plan or `/review` (`reviewer-critique-simulator`) for a mock NSF panel critique.
