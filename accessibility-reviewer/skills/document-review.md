---
name: document-review
description: Accessibility checklists for uploaded Word, PDF, PowerPoint, Excel, and Canva files from FSU's Documents and Files guide and WCAG 2.1 AA: what to check, what counts as a problem, the menu-path fix in each app, and what needs manual testing.
---

# Document Review Checklists

*Based on FSU Digital Accessibility's "Documents and Files" and "Design and Color" guides plus WCAG 2.1 AA. WCAG numbers and severity levels are defined in `accessibility-standards`.*

## Universal checks (every document)
| Check | Problem looks like | WCAG | Fix |
|---|---|---|---|
| Real text | Little or no extractable text; pages are images | 1.1.1, 1.4.5 | Recreate from the source file, or OCR + tag in Acrobat Pro. Critical if it's the whole document |
| Headings | Section titles are just bold/large text; no heading structure; skipped levels (H1 → H3) | 1.3.1, 2.4.6 | Use built-in heading styles (H1–H6). FSU: "Never manually bold or enlarge text" to make a heading |
| Title | Document title missing or a filename ("final_v3.docx") | 2.4.2 | Set the title in File > Properties (Word/PowerPoint: File > Info > Title; Acrobat: File > Properties > Description) |
| Language | Document language not set | 3.1.1 | Set the proofing/document language |
| Alt text | Informative images, charts, or icons with no description; alt text that's a filename, "image," or "picture" | 1.1.1 | Describe what the image *shows and why it's there*. Mark logos/decorative images as decorative |
| Charts | Chart with no alt text or no data summary | 1.1.1 | Alt text that states the trend ("Enrollment rose from 2,100 in 2022 to 2,900 in 2025"), or a data table next to it |
| Links | "Click here," "read more," or long raw URLs | 2.4.4 | Say where it goes: "View the Spring 2027 Advising Guide (PDF)" |
| Lists | Bullets typed as dashes/asterisks or emojis | 1.3.1 | Use the built-in list tool |
| Tables | No header row; merged/split cells; tables used only for layout; blank spacer rows/columns | 1.3.1 | Mark the header row; keep tables simple and rectangular; don't use tables for layout |
| Color meaning | "Items in red are required" | 1.4.1 | Add text or a symbol too ("Required*") |
| Contrast | Light text on light background, or colors failing 4.5:1 (3:1 for 18pt+). FSU warns: black text on garnet fails, and FSU Gold text on white fails (3.0:1) | 1.4.3 | Darken the text, use light text on dark, or make it large. Check with the WebAIM Contrast Checker. See the FSU brand color table in `media-web-social` |
| Sensory instructions | "See the box on the right" | 1.3.3 | Name the thing too ("See the 'Deadlines' table") |
| Other languages | Passages in another language not marked | 3.1.2 | Set the language for that text |

## Microsoft Word (.docx)
- Run Review > Check Accessibility and fix every error before saving.
- Headings: Styles pane, Heading 1 for the title, Heading 2 for sections, and so on.
- Tables: select the top row → Table Design > Header Row; also Table Properties > Row > "Repeat as header row at the top of each page."
- Images: right-click > View Alt Text; check "Mark as decorative" for decoration. Images should be "In line with text" so they stay in reading order.
- Text boxes and floating shapes: content in them is often skipped or read out of order. Move the text into the body.
- Exporting to PDF: File > Save As Copy > PDF with the option for accessibility/electronic distribution (tagged PDF). Never "Print to PDF", because that strips all tags.
- Can't verify from the upload: the Accessibility Checker result itself, how a screen reader reads it.

## PDF
FSU: "A PDF is only as accessible as its source file." Fix the Word/PowerPoint source and re-export when possible. Adobe Reader can't fix PDFs. Acrobat Pro is required.
- Scanned PDF: no selectable text → Critical. Fix: Acrobat Pro > Scan & OCR, then tag. Better: re-export from the source.
- Untagged PDF: if the export method looks like "Print to PDF" or the structure is lost, say tags are likely missing. Fix: re-export correctly, or Acrobat Pro > Accessibility > Autotag, then fix.
- Title: File > Properties > Description; set "Initial View" to show the document title.
- Reading order: check that the extracted text order makes sense (columns, sidebars, footnotes). Fix with the Reading Order tool / Order panel.
- Form fields: every fillable field needs a name/tooltip ("First name"); logical tab order. Unlabeled fields on a form = Critical.
- Fonts: embed fonts.
- Run Acrobat Pro All Tools > Prepare for accessibility > Check for accessibility and then a manual check, since the automated check misses things.
- Can't verify from the upload: the tag tree, whether tags match visual structure, and real screen reader behavior. Always list them under "Needs manual testing" and suggest Acrobat Pro's checker or PAC (the free PDF Accessibility Checker).

## PowerPoint (.pptx)
- Every slide has a unique title. Missing or duplicate titles ("Untitled," three slides called "Results") → Medium. To hide a title visually, use the Selection Pane, but keep the text.
- Reading order: Review > Check Accessibility > Reading Order Pane. Order should go top to bottom, title first.
- Outline View (View > Outline View): text missing from the outline (it lives in text boxes, not placeholders) is likely missed by screen readers.
- Use slide layouts/placeholders, not free text boxes.
- Images, charts, SmartArt: alt text, or mark decorative.
- Video/audio on slides: captions (see `media-web-social`).
- Animations/transitions: nothing essential only in an animation; nothing flashing more than 3×/second (2.3.1).
- Font size: very small text on slides (under ~18pt) → Low/Medium readability note.
- Can't verify: speaker notes behavior, auto-advancing timing, animation effects.

## Excel (.xlsx)
- No merged cells, nested tables, or blank spacer rows/columns. These break screen reader navigation.
- Headers: Insert > Table with "My table has headers."
- Sheet names describe the content ("Fall 2027 Budget," not "Sheet1"). Delete empty sheets.
- Charts have alt text explaining the trend.
- Color-coded cells ("green = approved") also need a text column.
- Start data in A1 with clear headings; instructions in the first cell of each sheet if needed.
- Can't verify: formulas' hidden behavior, screen reader table navigation.

## Canva designs, flyers, and infographics
- Text semantics: File > Accessibility > Edit text semantics; tag each text block as Heading 1–6, Paragraph, or Quote. If you skip it, Canva guesses (often wrong).
- Reading order: Position panel; the bottom layer is read first. Before downloading, choose to match reading order to layers.
- Export: Share > Download > PDF Standard (not PDF Print), "Flatten PDF" unchecked (flattening deletes all tags).
- Run Canva's Design Accessibility Checker for contrast.
- Flyer posted as an image (PNG/JPG, or on social media): all the event info is trapped in a picture → Critical unless the post or page repeats it. FSU's fix: the caption or nearby text includes who, what, where, when, and the RSVP link, and the alt text repeats the key text.
- Infographics: every number or claim in the graphic also appears in real text (alt text, or a text version next to it).

## Not covered by FSU's guides (use WCAG directly)
- Math/STEM content: equations as images need alt text or real equation markup (Word's equation editor; MathML/LaTeX in Canvas). Flag equation images without text alternatives as High in math-heavy materials.
- Images, CSV, and other files: apply the universal checks that fit (alt text, headers, clear names).
