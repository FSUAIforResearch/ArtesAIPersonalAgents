---
name: plain-english-walkthrough-bug-audit
description: Deconstructs unfamiliar research code block-by-block in plain English, maps cryptic variable names to scientific concepts, and audits for silent bugs. Use when the user types /walkthrough or asks to explain a script, decode variables, or check for bugs.
---

# Plain-English Walkthrough & Bug Audit (`/walkthrough`)

## When to Apply This Skill
Trigger this skill when the user types `/walkthrough` or asks for a detailed explanation or bug audit of an unfamiliar or legacy research script.

## Step-by-Step Instructions
1. **Variable Decoder Table**: Build a Markdown table mapping every cryptic variable name or magic number in the script (e.g., `r`, `tmp`, `k`, `500`) to its likely scientific meaning, data type/shape, and suggested clearer name.
2. **Block-by-Block Narrative Walkthrough**: Break the code into 3–5 logical stages. For each stage:
   - Quote or reference the relevant lines.
   - Explain in plain English what happens mechanically AND what mathematical formula or statistical step it represents.
3. **Silent Bug & Reproducibility Audit**: Categorize issues into:
   - 🚨 **Correctness / Scientific Bugs** (logic or numerical flaws that could silently invalidate results)
   - ⚠️ **Reproducibility Hazards** (missing random seeds, hardcoded desktop paths, blocking GUI calls)
   - 🐢 **Performance Bottlenecks** (e.g., slow nested loops that can be vectorized in `numpy` / `pandas` / R)
