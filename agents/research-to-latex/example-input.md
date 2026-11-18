# Example Input: Research-to-LaTeX Agent

Copy and paste the prompt below into your ArtesAI **Research-to-LaTeX Agent** chat (with `markdown-to-latex-converter` attached, or using the base agent):

````text
Convert the following Markdown report into a short, standalone LaTeX technical report using the article class and pdfLaTeX-compatible source. Provide a proposed structure, the complete LaTeX source, and a researcher checklist.

Preserve all reported values, units, the equation, and the code. Do not calculate new statistics or invent references. Mark missing information with % TODO comments or visible placeholders, and do not add a figure file or bibliography entry that I have not supplied.

# Comparing Two Document Conversion Workflows

## Objective
Compare the time required to prepare editable LaTeX drafts from Markdown notes using Workflow A and Workflow B.

## Methods
Each workflow was applied to the same 6 sample Markdown reports. Each report contained one table and one equation. Each workflow was run once per report. Preparation time included manual correction of the generated LaTeX. Hardware and software versions were not recorded.

## Results
The following values were recorded:

| Workflow | Reports processed | Mean preparation time (min) | Reports requiring manual correction |
| --- | --- | --- | --- |
| A | 6 | 18.5 | 4 |
| B | 6 | 12.0 | 2 |

## Reported Equation
Mean preparation time was defined as:

\[
\bar{t} = \frac{1}{n}\sum_{i=1}^{n} t_i
\]

Here, t_i is preparation time for report i, measured in minutes, and n is the number of reports.

## Code Excerpt
This Python excerpt labels the two workflows; it does not perform analysis:

```python
workflow_labels = ["A", "B"]
print("Workflow labels:", workflow_labels)
```

## Discussion
Workflow B had a lower reported mean preparation time in this pilot. No significance tests, confidence intervals, or effect sizes were computed. These observations do not establish a general performance advantage.

Background statement needing a citation: Structured authoring workflows can support reproducible document preparation. (No source supplied yet.)

## Limitations
Only 6 reports were included. Each workflow was run once per report. Hardware and software versions were not recorded. Manual corrections were included in preparation time but were not categorized by error type.

## Missing Materials
Author name and affiliation were not supplied. A workflow diagram was mentioned in the planning notes, but no figure file was supplied. No bibliography was supplied.
````
