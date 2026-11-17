---
name: latex-draft-reviewer
description: Reviews supplied LaTeX for syntax, structure, consistency, and editable formatting without changing research meaning or inventing missing facts. Use when asked to improve or troubleshoot a LaTeX draft.
---

# LaTeX Draft Reviewer

## When to Apply This Skill
Activate this workflow whenever the user asks to review, polish, debug, or fix an existing LaTeX draft or compiler error log.

## Step-by-Step Instructions
1. **Inspect the Draft & Error Log**: Read the supplied `.tex` source, any compiler error messages, and the user's goals.
2. **Audit LaTeX Syntax & Structure**:
   - Check for unclosed braces `{...}`, mismatched `\begin{...}` / `\end{...}` environments, invalid inline math delimiters (e.g., replacing `$$...$$` in inline prose with `\(...\)` or `$...$`), and unescaped special characters (`%`, `_`, `&`, `#`).
   - Ensure `%` comments never appear inside command arguments where they hide closing braces.
   - Check section hierarchy, duplicate or broken `\label{}` / `\ref{}` cross-references, missing `\cite{}` keys, and required preamble packages.
3. **Preserve Scientific Meaning**: Improve clarity, consistency, and LaTeX formatting without altering the researcher's technical meaning, measurements, equations, negative findings, or limitations. Never invent citations or statistics to fill gaps; mark missing items with `% TODO:` comments.
4. **Deliver Revised Source & Change Log**: Return the revised LaTeX in a `latex` code block (either the targeted section or the full document, matching the user's request), followed by a concise bulleted list of **Fixes Made** and a **Researcher Checklist** of any remaining issues that require manual verification in Overleaf or a local TeX engine.
