---
name: latex-template-drafter
description: Drafts LaTeX from supplied research materials within a user-provided template, preserving its class, commands, and required structure. Use when asked to populate a LaTeX template.
---

# LaTeX Template Drafter

## When to Apply This Skill
Activate this workflow whenever the user provides a LaTeX template (e.g., a journal, conference, thesis, or course `.tex` template) and asks to populate it with their research materials.

## Step-by-Step Instructions
1. **Inspect the Template**: Identify the `\documentclass`, engine requirements, required preamble packages, custom macros/commands, section order, and bibliography style (`BibTeX` or `BibLaTeX`). If the user has not yet pasted or attached the template, ask for it before generating code.
2. **Map Research Materials to Template Sections**: Place each supplied note, method, result, table, equation, and discussion point into the matching template section while preserving exact measurements, units, uncertainty, and limitations. Flag any conflicting numbers across source notes rather than picking one.
3. **Preserve Template Integrity**: Keep the template's required document class, packages, macros, and frontmatter structure intact. Make only the minimal package additions needed for the user's tables, math, or code.
4. **Handle Missing Required Fields Safely**: Replace template sample text only with facts supported by the user's notes. For missing required fields (such as author affiliations, funding acknowledgments, or missing `.bib`/figure files), keep the command syntactically valid (e.g., `\author{}`) and place a `% TODO:` comment on the line above.
5. **Verify Syntax & Deliver Output**: Check that all braces, environments, and labels balance, then return a brief summary of how the template was populated, the complete **LaTeX Draft** in a `latex` code block, and a **Researcher Checklist** listing any external `.cls`, `.bst`, `.bib`, or figure files required for compilation.
