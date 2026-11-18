---
name: media-web-social
description: Accessibility checklists for web and Canvas pages, video/audio (captions, transcripts, audio description), social media posts, and color contrast, including FSU's brand color pass/fail table. Use for web, media, or social content, or any FSU-branded design.
---

# Web, Media, Social, and Color Checklists

*Based on FSU Digital Accessibility's guides plus WCAG 2.1 AA. WCAG numbers and severity levels are defined in `accessibility-standards`.*

## Web pages and Canvas pages
FSU's four requirements for editors: real headings, descriptive links, alt text, and 4.5:1 contrast.

| Check | Problem looks like | WCAG | Fix |
|---|---|---|---|
| Page title | Missing or generic `<title>` | 2.4.2 | Descriptive title |
| Language | No `lang` on `<html>` | 3.1.1 | `<html lang="en">` |
| Headings | No `<h1>`, skipped levels, bold text used as headings | 1.3.1, 2.4.6 | Real `<h1>`–`<h6>` in order |
| Images | `<img>` with no `alt`; alt = filename/"image" | 1.1.1 | Meaningful alt; `alt=""` for decorative |
| Links | "Click here," "read more"; PDF links not labeled | 2.4.4 | Say the destination, add "(PDF)" |
| Skip link | No "Skip to Main Content" link. FSU requires one on every site (first focusable element, hidden until focused) | 2.4.1 | Add it |
| Landmarks | Missing `<header>`, `<nav>`, `<main>` | 1.3.1, 2.4.1 | Use semantic landmarks |
| Fake buttons | `<div>`/`<span>` with `onclick` used as buttons or nav (FSU: "Do not use `<div>` for buttons or navigation") | 2.1.1, 4.1.2 | Use `<button>` / `<a href>` |
| Forms | `<input>` with no `<label>`; placeholder used as the label; errors not tied to fields | 1.3.1, 3.3.2, 4.1.2 | `<label for>`; `aria-describedby` for errors/format hints |
| Focus | `outline: 0` / `outline: none` with no replacement (FSU: "Never use `outline: 0`") | 2.4.7 | `:focus-visible` with a high-contrast style |
| Dynamic updates | Status messages/result counts change with no announcement | 4.1.3 | `aria-live="polite"` |
| Modals | No `role="dialog"`, focus not trapped, Esc doesn't close | 2.1.2, 4.1.2 | Fix all three |
| Iframes | No `title`, or a generic one ("frame," "widget") | 4.1.2 | Descriptive `title`; hide tracking frames with `aria-hidden="true"` + `tabindex="-1"` |
| Embedded content | Inaccessible embeds or autoplay (FSU: "You are responsible for the compliance of anything embedded on your site") | 1.4.2, 2.2.2 | Accessible embeds; no autoplay |
| `tabindex` > 0 | Custom tab order | 2.4.3 | Remove; use DOM order |

Canvas: use Ally or the Canvas Accessibility Checker; FSU's ODL also recommends TidyUP to archive unused/duplicate content (which improves the course accessibility score). Scanned readings are inaccessible, so check FSU Libraries for accessible versions.

Can't verify from source: rendered contrast (unless colors are in readable CSS), keyboard-only use, focus order, screen reader output (FSU suggests NVDA on Windows, VoiceOver on Mac), 400% zoom/reflow, content loaded by JavaScript. Suggest Siteimprove (FSU's tool; check Accessibility > Compliance > ADA Title II), WAVE, or axe.

## Video and audio
| Content | Requirement (FSU) | WCAG | Missing → severity |
|---|---|---|---|
| Prerecorded video | Captions *and* audio description are both required. Full script, captions reviewed to accuracy, final VTT/SRT uploaded | 1.2.2, 1.2.5 | No captions → Critical; no audio description where visuals carry key info → High |
| Live events (Zoom/Teams) | Live captions on; an accommodation process ready if quality is poor | 1.2.4 | No captions → Critical |
| Audio only (podcasts) | Transcript: "a separate, clean, scrollable text page containing the full content of the audio" | 1.2.1 | No transcript → Critical |
| YouTube | Full transcript in the description under the heading "Full Text Transcript" | 1.2.1 | Medium/High |

Auto-captions: FSU says "Automated captions are not compliant alone." They must be reviewed and corrected by a person. Aim for 99%+ accuracy.

Caption quality checklist (when a caption/transcript file is uploaded):
- Synced to the audio
- Speakers identified when more than one
- Non-speech sounds in brackets: [applause], [music]
- Proper nouns, FSU names, and technical terms spelled correctly
- Punctuation present
- Max ~42 characters per line; captions kept out of the bottom 20% when on-screen text is there

Audio description: needed when important visuals aren't spoken (on-screen text, charts, demonstrations). The easiest way is to describe visuals naturally in the script ("As you can see on this chart, enrollment doubled"). A transcript does not replace audio description under WCAG 2.1 AA.

Also check: no autoplay with sound (1.4.2); nothing flashing more than 3 times per second (2.3.1); the player has keyboard-usable controls.

## Social media posts
| Check | Rule (FSU) | Severity if missing |
|---|---|---|
| Alt text | Every image, with content + context. Instagram: Advanced Settings; X: "Add Description"; Facebook: review auto alt text; LinkedIn: Edit on the image | High (Critical if the image is the whole message, like a flyer) |
| Video | Accurate captions (edit auto-captions); Instagram Stories/Reels: Captions sticker; Facebook: upload .SRT | Critical |
| Flyer images | Caption includes who, what, where, when, and the RSVP link | Critical if the info is only in the image |
| Hashtags | CamelCase (#GoNoles), at the end of the post | Low |
| Emojis | Not as bullets; at the end of sentences, not mid-sentence; don't overuse | Low/Medium |
| Fancy text | No Unicode "fancy fonts" or ASCII art (screen readers skip or misread them) | Medium |
| Contrast | Text on images ≥ 4.5:1 | High |
| Flashing | Nothing over 3 flashes per second | Critical |
| Shared PDFs | Fully tagged (see `document-review`) | Per document |

Exceptions: posts made before the compliance date don't have to be fixed, but pinned/essential posts should be. Personal accounts are excluded unless used for FSU business or to promote FSU programs.

## Color and FSU brand colors
- Minimum contrast: 4.5:1 for normal text; 3:1 for large text (18pt+, or 14pt bold) and for icons/chart lines/field borders (1.4.11).
- FSU's examples: black on white 21.0:1 (pass) · FSU Garnet on white 8.5:1 (pass) · dark gray on white 4.5:1 (pass) (the minimum) · FSU Gold on white 3.0:1 (fail)
- "Do not trust your eyes." Recommend the WebAIM Contrast Checker for anything borderline.
- Fixes: darken the text; put light text on a dark background; or make the text large enough for the 3:1 rule.
- Don't use color alone to carry meaning (1.4.1).

FSU brand color table (text color across, background down). A = acceptable, L = large text only, D = don't use.

| Background | Black text | White text | Garnet text | Gold text |
|---|---|---|---|---|
| FSU Garnet #782F40 | D | A | D | L |
| FSU Gold #CEB888 | A | D | L | D |
| White #FFFFFF | A | D | A | D |
| Stadium Night #101820 | D | A | D | L |
| Plaza Brick #572932 | D | A | D | L |
| Gulf Sands #DFD1A7 | A | D | L | D |
| Legacy Blue #425563 | D | A | D | D |
| Westcott Water #5CB8B2 | A | D | D | L |
| Vault Garnet #A6192E | D | A | D | D |
| Vault Gold #FFC72C | A | D | D | D |

Using a D combination for body text → High. Using an L combination for small text → High. If you can identify the colors in a document (e.g., garnet heading bar with black text), name the combination and cite this table.
