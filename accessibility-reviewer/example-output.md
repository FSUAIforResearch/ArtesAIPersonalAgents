# Example Output: FSU Accessibility Reviewer

Below is an example of what your ArtesAI **FSU Accessibility Reviewer** agent will generate when given the prompt in [`example-input.md`](./example-input.md). Wording will vary, but the rating, the top problems, and the structure should match.

Tested on 2026/11/16 using ArtesAI with model gpt-5.6-luna
---

# Accessibility Review: STA 3032 Syllabus

## Rating: Very Bad

The planned **Print to PDF** export is likely to remove Word's accessibility structure, and the syllabus also has several barriers affecting headings, table navigation, color-only meaning, links, video captions, and chart access. Rebuild the Word source with accessible structure, then export with Word's tagged/accessible PDF option rather than printing to PDF.

## Summary

I reviewed the pasted content for a current Spring 2027 Canvas syllabus, assuming it will be posted as course content rather than archived material. The highest-priority fixes are to use real heading styles and a tagged export, add a header row to the schedule table, provide text alternatives for the image and grade chart, and replace color-only instructions with text labels.

## Findings

| # | Issue | Where | WCAG | Severity | How to fix |
|---|---|---|---|---|---|
| 1 | The planned **Print to PDF** workflow can create an untagged PDF or lose the document's structure, making the syllabus difficult or impossible to navigate with a screen reader. | Planned PDF export | 1.3.1 Info and Relationships; 1.3.2 Meaningful Sequence | **Critical** | Fix the Word source first. Use built-in heading styles, a real table, and meaningful reading order. Export with **File > Save As/Save a Copy > PDF**, selecting the option intended for electronic distribution/accessibility. Do not use **Print to PDF**. Then run Acrobat Pro's accessibility checker and manually inspect the tags and reading order. |
| 2 | Section headings are bold text rather than real headings, so assistive technology cannot reliably identify sections or navigate the syllabus. | “Instructor Information,” “Course Materials,” “Lecture Videos,” “Schedule,” “Grading,” and “Accessibility Statement” | 1.3.1; 2.4.6 | **High** | In Word, apply **Heading 1** to the syllabus title and **Heading 2** to each major section. Do not create headings by only changing font size or bolding text. |
| 3 | The schedule table has no header row set. Screen reader users may not know what each column represents. | Schedule table | 1.3.1 Info and Relationships | **High** | Add descriptive column headers, such as **Week**, **Topic**, **Required reading**, and **Optional reading/Activity**. Select the first row and use **Table Design > Header Row**. Keep the table rectangular and simple. |
| 4 | Required versus optional readings are conveyed by red and green alone. This information may be unavailable to people who cannot perceive the colors. | Course Materials and Schedule; “red” and “green” reading labels | 1.4.1 Use of Color | **High** | Put the meaning in text, not only color: label items **Required reading** and **Optional reading** in the schedule. You may retain color as a supplement, but it must not be the only indicator. Also verify contrast with the WebAIM Contrast Checker. |
| 5 | The chart is referenced using a visual-location instruction (“on the right”), and the chart has no text description. The grade weights may therefore be inaccessible or unclear. | Grading: “See the chart on the right…” and “[Chart: pie chart of grade weights, no description]” | 1.1.1 Non-text Content; 1.3.3 Sensory Characteristics | **High** | Replace the instruction with a meaningful label, such as “See the **Grade weights** chart below.” Add alt text that states the actual weights and purpose, for example: “Grade weights: Exams 40%, homework 25%, quizzes 15%, and final project 20%.” Confirm the percentages against the real chart. Preferably include the weights in a real text list or table as well. |
| 6 | The image has no usable alternative text in the pasted content. It may be informative or decorative, but that cannot be determined from the filename alone. | “IMG_0042.png” under Course Materials | 1.1.1 Non-text Content | **High** if informative; **Low** if decorative | In Word, right-click the image > **View Alt Text**. Describe what it shows and why it matters. If it is purely decorative, mark it decorative. Do not use the filename as alt text. |
| 7 | The office-hours link uses vague link text (“click here”), and the raw URL is exposed rather than given a descriptive destination. | Instructor Information | 2.4.4 Link Purpose (In Context) | **Medium** | Replace it with descriptive linked text, such as **Office-hours sign-up sheet**. The visible text should identify the destination; it does not need to display the full URL. |
| 8 | The lecture video is described as having automatic captions, but automated captions alone are not sufficient because errors can affect names, statistics, and technical terms. | Lecture Videos; weekly Kaltura lectures and welcome video | 1.2.2 Captions (Prerecorded) | **High** | Review and correct the captions manually before posting. Check speaker identification, punctuation, proper nouns, technical terms, and meaningful non-speech sounds. Also check whether important visual information needs audio description or spoken description. |
| 9 | The document's language and document properties cannot be confirmed from the pasted text. A missing language setting can cause incorrect pronunciation by screen readers, and a missing title makes navigation less clear. | Word/PDF metadata | 3.1.1 Language of Page; 2.4.2 Page Titled | **Medium** | In Word, set the proofing/document language to English and set **File > Info > Properties > Advanced Properties > Summary > Title** to something descriptive, such as **STA 3032 Applied Statistics Syllabus Spring 2027**. Confirm the PDF title in Acrobat Pro under **File > Properties**. |

## Needs manual testing

- Open the exported PDF in **Acrobat Pro** and run **All Tools > Prepare for accessibility > Check for accessibility**.
- Inspect the PDF tag tree and reading order; confirm the title, headings, table headers, image alt text, and chart alternative are correctly tagged.
- Test keyboard navigation and logical focus/reading order.
- Test with a screen reader, such as NVDA on Windows or VoiceOver on Mac.
- Check rendered text and non-text contrast, especially the red/green reading indicators and any chart colors, with the **WebAIM Contrast Checker**. The pasted text does not reveal the actual colors or sizes.
- Confirm that the image and pie chart communicate all information without relying on color or visual position.
- Review the Kaltura captions against the audio and confirm that any important visual information is described in the audio or an audio-description track.
- Verify that links work and that the Kaltura video player is keyboard usable.

## What's done well

- The syllabus uses descriptive section topics and identifies the course, term, instructor, office hours, schedule, grading, and accommodations information.
- A text version of the schedule is present rather than leaving all course information in an image.
- The course includes an accessibility statement and points students to the Office of Accessibility Services.

## Exceptions note

This appears to be a current Spring 2027 course syllabus, so the preexisting-document exception does not appear relevant. FSU Digital Accessibility makes the final determination about exceptions and accommodations.

## Help

For assistance, contact **DigitalAccessibility@fsu.edu**. For Canvas course content, contact **canvas@fsu.edu**.