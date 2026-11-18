---
name: markdown-to-latex-converter
description: Converts supplied Markdown research reports into editable LaTeX while preserving content, tables, equations, code, and limitations. Use when asked to convert Markdown notes or reports to LaTeX.
---

# Markdown-to-LaTeX Converter

## When to Apply This Skill
Activate this workflow whenever the user asks to convert a Markdown report or Markdown research notes into a LaTeX document.

## Step-by-Step Instructions
1. **Inspect the Markdown Input**: Identify all headings, lists, tables, equations, code blocks, links, citations, and referenced figures. Use the requested document class or infer an appropriate structure (e.g., `article` for a technical report).
2. **Preserve Research Meaning & Exact Values**: Retain all supplied measurements, units, qualifications, negative findings, uncertainty, and limitations verbatim in meaning. Never compute unrequested statistics or invent citations.
3. **Convert Structural Elements to Idiomatic LaTeX**:
   - **Headings & Lists**: Map `#` / `##` / `###` to `\section`, `\subsection`, `\subsubsection`, and Markdown lists to `itemize` or `enumerate`.
   - **Tables**: Convert Markdown pipe tables to `table` + `tabular` (using `booktabs`: `\toprule`, `\midrule`, `\bottomrule`), preserving every number and unit exactly and adding a `\caption` and `\label`.
   - **Equations & Code**: Preserve mathematical notation using standard LaTeX math environments (`amsmath`) and place code blocks in `lstlisting` (`listings`) or `verbatim`. Escape special characters (`%`, `_`, `&`, `#`) in prose without altering math or code.
   - **Citations & Missing Figures**: Format supplied citations properly; mark missing references with `\cite{TODO}` and a `% TODO:` comment, and use `% TODO:` placeholders for unprovided figure files so compilation does not break.
4. **Verify Syntax & Deliver Output**: Confirm all braces, environments, and math delimiters are balanced. Output a brief **Proposed Structure**, the complete **LaTeX Draft** inside a `latex` code block, and a **Researcher Checklist** of remaining TODOs.
