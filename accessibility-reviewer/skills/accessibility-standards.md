---
name: accessibility-standards
description: FSU accessibility rules (ADA Title II + WCAG 2.1 AA, Sections 504/508, Fla. Stat. 282.603, FSU policy), exceptions, deadlines, key WCAG criteria, and the rubric for rating content Good / Somewhat Good / Neutral / Bad / Very Bad. Use on every accessibility review.
---

# Accessibility Standards, Exceptions, and Rating Rubric

*Sources compiled 2026-11-12 from FSU Digital Accessibility (digitalaccessibility.fsu.edu), the DOJ Title II rule and its April 2026 extension, and Florida Statutes. Not legal advice.*

## 1. Which rules apply to FSU content

| Rule | What it requires | Why it matters here |
|---|---|---|
| ADA Title II + DOJ web rule (28 CFR Part 35, Subpart H; published April 24, 2024) | State and local government web content and mobile apps must meet WCAG 2.1 Level AA | FSU is a public university, so this is the main rule. It covers documents, course content, videos, and social media |
| DOJ extension (interim final rule, effective April 20, 2026) | Moved the compliance dates back one year: April 26, 2027 for entities serving 50,000+ people (FSU's category), April 26, 2028 for smaller ones. The standard didn't change (still WCAG 2.1 AA) | FSU's FAQ now gives April 26, 2027. Older FSU pages still say April 24, 2026 |
| Section 504 (Rehabilitation Act) | Programs receiving federal funding can't discriminate on the basis of disability | Basis for individual accommodations, which still apply even when content is "exempt" |
| Section 508 (Rehabilitation Act) | Federal ICT accessibility standards (2017 refresh uses WCAG 2.0 AA, including non-web documents) | FSU ITS cites 508 alongside WCAG 2.1; Florida law points to it |
| Florida Statute 282.603 | State agencies' electronic and information technology must conform to Section 508 standards, unless that's an undue burden (then provide an alternative way to access the information) | State-level backing. Whether "state agency" includes universities isn't defined in the section, so cite it as context, not as the main rule |
| FSU Digital Accessibility policy | Public web content, mobile apps, and digital course materials meet WCAG 2.1 AA. Includes password-protected content (Canvas), student organization and faculty lab sites, and content from vendors/contracts | Tells you the scope is broad: "it's behind a login" or "it's just an RSO" is not an exception |

FSU-specific points to apply:
- Canvas course materials for current and future courses must be accessible.
- RSO (student organization) and faculty lab web content counts as FSU content (the RSO Handbook is treated as a license to operate under FSU).
- Content provided through contracts or licenses (vendors) is covered.
- Personal social media accounts are excluded unless used for university business or to promote FSU programs.

## 2. Exceptions (flag them, don't decide them)
Under the DOJ rule, as summarized by FSU. If one *might* apply, mention it, still give the review, and send the final call to DigitalAccessibility@fsu.edu.

1. Archived web content: created before the compliance date, kept only for reference/research/recordkeeping, kept in a special archive area, and not changed since being archived. All four conditions must hold.
2. Preexisting conventional electronic documents: Word, PDF, PowerPoint, or spreadsheet files posted before the compliance date. Does not apply if the document is still used to apply for, access, or participate in a program or service (e.g., a current form, a syllabus, a current course reading).
3. Third-party content: narrow; independent content like public comments on a message board. Does not cover RSOs, labs, or vendors working for FSU.
4. Individualized, password-protected documents: about a specific person (e.g., personal records, a bill).
5. Preexisting social media posts: posted before the compliance date. FSU still asks that pinned or essential posts get alt text and captions.

Even when an exception applies, a person with a disability can still request an accommodation (ADA/504). So "exempt" never means "doesn't matter."

## 3. WCAG 2.1 AA criteria that matter most for documents
Cite by number + short name. If you're unsure of the number, describe the problem plainly instead.

| WCAG | Name | What it means in a document |
|---|---|---|
| 1.1.1 | Non-text Content | Informative images, charts, and icons have alt text; decorative ones are marked decorative; a scanned page needs real text |
| 1.2.1 | Audio-only and Video-only (Prerecorded) | Audio-only → transcript; silent video → text or audio description |
| 1.2.2 | Captions (Prerecorded) | Videos have accurate captions |
| 1.2.4 | Captions (Live) | Live events have captions |
| 1.2.5 | Audio Description (Prerecorded) | Important visual-only info in video is described |
| 1.3.1 | Info and Relationships | Real headings, lists, table header rows, and form labels, not just visual formatting |
| 1.3.2 | Meaningful Sequence | Reading order matches the visual order |
| 1.3.3 | Sensory Characteristics | Instructions don't rely only on shape/position ("click the round button on the right") |
| 1.4.1 | Use of Color | Color isn't the only way information is shown ("required fields are red") |
| 1.4.3 | Contrast (Minimum) | Text contrast ≥ 4.5:1; large text (18pt, or 14pt bold) ≥ 3:1 |
| 1.4.5 | Images of Text | Use real text, not pictures of text (logos excepted) |
| 1.4.11 | Non-text Contrast | Chart lines, icons, and form field borders ≥ 3:1 against neighbors |
| 2.1.1 | Keyboard | Everything interactive works with a keyboard |
| 2.2.2 | Pause, Stop, Hide | Auto-moving content can be paused |
| 2.3.1 | Three Flashes | Nothing flashes more than 3 times per second |
| 2.4.2 | Page Titled | The document has a real title (document properties), not a filename |
| 2.4.4 | Link Purpose (In Context) | Link text says where it goes, not "click here" |
| 2.4.6 | Headings and Labels | Headings and labels describe the content |
| 3.1.1 | Language of Page | Document language is set |
| 3.1.2 | Language of Parts | Passages in another language are marked |
| 3.3.2 | Labels or Instructions | Form fields have labels/instructions |
| 4.1.2 | Name, Role, Value | Form fields and controls have accessible names (e.g., PDF form field tooltips) |

## 4. Severity levels (for each finding)
- Critical: blocks access to the whole thing or its main purpose for a group of users. Examples: a scanned image-only PDF with no real text; a video with no captions; a fillable form with no field labels; a flyer that's one image with no text alternative.
- High: blocks access to important parts. Examples: data tables with no header row; informative charts/images with no alt text; body text that fails contrast; reading order that scrambles the content; no document title *and* no headings in a long document.
- Medium: makes it noticeably harder to use. Examples: skipped heading levels; vague link text throughout; color-only meaning in a few places; missing slide titles on some slides; document language not set.
- Low: minor or best practice. Examples: decorative image not marked decorative; sheet named "Sheet1"; a raw URL used as link text once; hashtags not in CamelCase.

## 5. Rating rubric
Find the first row from the top that matches.

| Rating | When to give it |
|---|---|
| Very Bad | Any Critical finding that affects the whole document's main content (e.g., the whole PDF is a scan, the whole flyer is one image of text, the only video has no captions) |
| Bad | Any other Critical finding, or 3+ High findings |
| Neutral | 1–2 High findings, or 4+ Medium findings |
| Somewhat Good | No Critical/High; 1–3 Medium findings and/or any number of Low |
| Good | No findings above Low in everything you could check |

Adjustments (use judgment, and say why in one line if you use one):
- Repeats: the same issue repeated many times (e.g., 20 images without alt) counts once, but its severity can go up one level if it covers most of the content.
- Couldn't check much: if you could only see a small part of the file (e.g., the text extraction was garbled), cap the rating at Neutral and say the rating is provisional.
- Good ≠ compliant. A "Good" rating still comes with the manual testing list.

## 6. Who to contact
- FSU Digital Accessibility: DigitalAccessibility@fsu.edu (questions, exceptions, help).
- Canvas / course content: Office of Digital Learning, canvas@fsu.edu.
- Siteimprove access (web scans, ADA Title II score): request through the FSU ITS Service Catalog ("Accessibility and Link Checking").
- Training: Siteimprove Academy, and LinkedIn Learning's "Accessibility Basics" (free for FSU).
