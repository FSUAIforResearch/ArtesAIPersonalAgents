# Example Output

*What a good response to `example-input.md` looks like. Wording will vary, but the rating, the top problems, and the structure should match.*

---

## Rating: Bad
Four High problems: the planned Print to PDF export strips all accessibility tags, the readings depend on color alone, the grade chart has no description, and the schedule table has no header row.

Summary: I reviewed pasted text from a Word syllabus (Canvas course material, which FSU says must meet WCAG 2.1 AA). It's in use for a current course, so the old-document exception doesn't apply. Fix first: (1) export with Save As Copy > PDF instead of Print to PDF, (2) stop using color alone to mark required readings, (3) add alt text (and a text version) for the grade chart.

| # | Issue | Where | WCAG | Severity | How to fix |
|---|---|---|---|---|---|
| 1 | Print to PDF strips all tags, so screen readers lose headings, the table, and reading order | Planned export | 1.3.1, 1.3.2 | High | In Word: File > Save As Copy > PDF and keep the accessibility/document structure tags option on. Or upload the .docx directly |
| 2 | Required vs. optional readings shown only by color (red/green); red/green is also the most common color-blindness pair | "highlighted in red… in green," schedule | 1.4.1 | High | Add words: "Ch. 1 (required)", "Ch. 2 (optional)" |
| 3 | Grade chart has no description, and the instructions point to its position ("the chart on the right") | Grading | 1.1.1, 1.3.3 | High | Alt text: "Pie chart of grade weights: …" with the actual percentages, plus a short list in the text. Say "the grade chart below" instead of "on the right" |
| 4 | Schedule table has no header row | Schedule | 1.3.1 | High | Add a top row (Week, Topic, Required reading, Optional/Due) and turn on Table Design > Header Row |
| 5 | Headings are bold text, not heading styles | All section titles | 1.3.1, 2.4.6 | Medium | Apply Heading 1 to the course title and Heading 2 to each section |
| 6 | Image with no alt text (filename only) | "IMG_0042.png," Course Materials | 1.1.1 | Medium | Describe it (e.g., "Cover of *Applied Statistics*, 7th edition") or mark it decorative |
| 7 | Vague link text and raw URLs | "click here," lecture link | 2.4.4 | Medium | "Sign up for office hours (Microsoft Form)"; "Watch the Week 1 welcome video (Kaltura)" |
| 8 | Lecture videos use automatic captions only | Lecture Videos | 1.2.2 | Medium | FSU: "Automated captions are not compliant alone." Edit the captions in Kaltura for accuracy. Raise this to Critical if they're never reviewed |

Needs manual testing: document title and language in File > Properties, the Word Accessibility Checker (Review > Check Accessibility), color contrast of the red/green text, caption accuracy on the actual videos, and the final PDF in Acrobat Pro's accessibility check.

Done well: it includes an accessibility statement, the sections are logically ordered, and the course materials are linked rather than pasted in as images.

Help: DigitalAccessibility@fsu.edu · canvas@fsu.edu (Office of Digital Learning)
