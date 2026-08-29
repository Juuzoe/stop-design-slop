# Craft details: the marks of a human hand (C1–C64)

Positive counterpart to the tell catalogs. Each entry is implementable, most in one line. Cited as "C12" in reports.

Generated UI is thinnest exactly here, because these decisions never appear in a prompt. Start with the **Top 15** at the bottom if you have an hour rather than a day.

## 1. Typographic craft

**C1. Real punctuation characters** (trivial)
Use `’` for apostrophes, `“ ”` `‘ ’` for quotes, `—` for breaks, `–` for ranges (`2019–2024`), `…` for ellipsis, `−` (U+2212) for minus. Never `'` `"` `--` `...`.
Signals: somebody read the text at character level. Straight quotes are the loudest generated-text tell there is.

**C2. Hanging punctuation** (trivial)
`html { hanging-punctuation: first allow-end last; }` with a fallback: `blockquote { text-indent: -0.45em }` inside `@supports not (hanging-punctuation: first)`.
Caveat: Safari only. Can cause horizontal scroll when the container has no side padding.

**C3. Optical margin on display quotes** (trivial)
Pull the opening `“` left by its optical width: `.pullquote { text-indent: -0.42em }`. The value is font-specific, so store it as `--quote-hang`.

**C4. Kill faux bold, italic and small caps** (trivial)
`font-synthesis: none` on `:root`, then load the real weights and the `smcp` set.
Caveat: without real files, text silently renders at the wrong weight. Audit after enabling.

**C5. True small caps** (small)
`font-variant-caps: small-caps`, or `all-small-caps` for acronym runs. Where the font lacks `smcp`, fake it deliberately: `text-transform: uppercase; font-size: 0.82em; letter-spacing: 0.06em; font-weight: 500`.

**C6. Old-style figures in prose** (trivial)
`article p, li { font-variant-numeric: oldstyle-nums proportional-nums }` so `1867` sits in the lowercase rather than above it.

**C7. Tabular lining figures for anything that changes or stacks** (trivial)
`table, .metric, time, .price { font-variant-numeric: tabular-nums lining-nums }`. Stops digit jitter in counters and ragged price columns.

**C8. Decimal alignment in numeric columns** (small)
`td.num { text-align: right; font-variant-numeric: tabular-nums }`, and format to a fixed decimal count server-side so the points stack. Character alignment (`text-align: "."`) is specified but unimplemented.

**C9. Slashed zero for codes** (trivial)
`code, .sku, .otp, kbd { font-variant-numeric: slashed-zero }`. Signals you pictured someone reading an ID aloud over the phone.

**C10. Real fractions** (trivial)
`.recipe { font-variant-numeric: diagonal-fractions }` turns `1/2` into a true ½.

**C11. `text-wrap: balance` on short blocks** (trivial)
`h1,h2,h3,h4,h5,h6,figcaption,blockquote,.card-title { text-wrap: balance }`. No more two-word second lines under a headline.
Caveat: Chromium stops balancing past 6 lines, Firefox past 10. Headlines only.

**C12. `text-wrap: pretty` on body copy** (trivial)
`p, li, dd { text-wrap: pretty }` removes last-line orphans and stacked hyphenated line-ends. Scope it to prose, since it is the slowest wrap algorithm.

**C13. Tuned hyphenation** (trivial)
`p { hyphens: auto; hyphenate-limit-chars: 7 3 3 }` and set `lang="en"` on `<html>`, without which no dictionary loads.

**C14. Tracking that changes with size** (trivial)
Token it: `--track-display: -0.03em; --track-body: 0; --track-caps: 0.08em`. The single most reliable typographer's tell, and default tracking at every size is the AI signature. Never track lowercase text negatively below -0.01em.

**C15. Optical vertical centering in boxes** (trivial)
`button, .chip, .badge { text-box: trim-both cap alphabetic; padding-block: 0.6em }` trims half-leading so equal padding looks equal.
Caveat: Chrome 133+, Safari 18.2+, Firefox 154+. Recheck padding in older browsers.

**C16. Ligature discipline** (trivial)
`body { font-variant-ligatures: common-ligatures contextual }` and `code, pre, kbd { font-variant-ligatures: none }` so `!=` never fuses into a glyph.

**C17. Optical sizing** (trivial)
`body { font-optical-sizing: auto }`, or pin it with `h1 { font-variation-settings: "opsz" 48 }`. Display type becomes a display cut rather than body type enlarged.

**C18. Mid-sentence weight shift** (small)
`.lede strong { font-variation-settings: "wght" 560 }`. A half-step rather than a jump to 700, which reads as emphasis calibrated by eye.

**C19. Non-breaking glue** (small)
`5&nbsp;km`, `Fig.&nbsp;3`, `Nov.&nbsp;12`, or `.unit { white-space: nowrap }`. Nothing wraps a number away from its unit.

**C20. A measured measure** (trivial)
`.prose { max-width: 66ch }` (45–90 characters is the working range), `line-height: 1.5` body, `1.15` display. Check with the real face loaded, since `ch` varies by font.

**C21. Drop cap or small-caps opener** (small)
`p.opener::first-letter { initial-letter: 3 3; margin-right: 0.08em }` with a float fallback in `@supports not (initial-letter: 3)`. Or set the first two or three words in small caps.
Caveat: `initial-letter` is unsupported in Firefox. Always supply the fallback.

**C22. Sidenotes in the margin** (medium)
A full-bleed grid with a named `[note]` column, `.sidenote { grid-column: note; font-size: 0.8rem }`, collapsing below ~1100px into an inline `<details>`. The strongest editorial-designer tell available.

## 2. Layout craft

**C23. Optical rather than mathematical centering** (trivial)
For hero text, modals and empty states, bias content upward: `padding-block: 8vh 12vh`. The visual center sits about 5% above the geometric one, so symmetric padding reads as sagging.

**C24. Optically aligned icons** (small)
Nudge asymmetric glyphs. A play triangle gets `transform: translateX(1px)`; circular icons render about 4% larger than square ones in the same row. Keep the nudges inside the icon component.

**C25. Align to the type's edge, not its box** (small)
For large flush-left headings, cancel the left side bearing with `h1 { margin-left: -0.045em }` so the stem lines up with the paragraph below. The value is font-specific.

**C26. Full-bleed inside a contained measure** (small)
```css
.article { display: grid; grid-template-columns:
  [full-start] minmax(1rem,1fr) [content-start] min(66ch,100%) [content-end] minmax(1rem,1fr) [full-end]; }
.bleed { grid-column: full; }
```

**C27. Break the grid in exactly one place** (small)
One element per page gets `grid-column: 2 / span 4; transform: translateY(-2rem) rotate(-1.2deg)` while everything else obeys. Two breaks read as an accident, three as no grid at all.

**C28. Hang elements into the margin** (small)
`.figure-num { float: left; margin-inline-start: -4.5rem; width: 4rem; text-align: right }`. The margin becomes space rather than emptiness.

**C29. Asymmetric page margins** (trivial)
`.article { margin-inline: max(2rem, 12vw) auto }` leaves a deliberate wide gutter on one side for notes and figures. Reflow to symmetric below ~900px.

**C30. Subgrid so cards line up** (small)
`.card { display: grid; grid-template-rows: subgrid; grid-row: span 3 }` aligns titles, body and CTA across cards whatever the title length. Eyeballed padding never achieves this.

**C31. Overlap across a section boundary** (trivial)
`.feature-card { margin-block-start: -4rem; position: relative; z-index: 1 }` where the background color changes. Sections read as composed rather than stacked.

**C32. Real baseline rhythm** (medium)
Define `--lh: 1.5rem` and derive every vertical value from it. Treat it as a spacing scale rather than a pixel guarantee, since images and font swap will break strict alignment.

**C33. Asymmetric heading space** (trivial)
`h2 { margin-block: 2.5em 0.6em }`. Roughly three to four times more space above than below, so a heading binds to the text it owns. Use `em` so it scales.

**C34. Deliberate use of the fold** (trivial)
`min-height: calc(100svh - var(--header)); padding-block-end: 12vh` so the next section peeks in. Use `svh`/`dvh` rather than `vh`, or mobile browser chrome will crop it.

**C35. Never justify without hyphenation** (trivial)
`text-align: justify` only alongside `hyphens: auto` and a measure under about 45ch. Justified narrow columns without hyphenation are one of the loudest amateur tells.

## 3. The detail layer

**C36. Custom `::marker`** (trivial)
`li::marker { content: "—  "; color: var(--accent) }`, or counters with `decimal-leading-zero`. `::marker` accepts only font, color and content, so use `::before` for anything positional.

**C37. Hanging bullets** (trivial)
`ul { list-style-position: outside; padding-inline-start: 1.1em }` so wrapped lines align under the text. `inside` is the template default and looks wrong at every size.

**C38. Styled `::selection`** (trivial)
`::selection { background: color-mix(in oklab, var(--accent) 28%, transparent); color: var(--ink); text-shadow: none }`. The highest delight-per-byte rule in CSS. Keep contrast at 4.5:1.

**C39. A brand focus ring** (trivial)
`:focus-visible { outline: 2px solid var(--focus); outline-offset: 3px; border-radius: inherit }`. On busy backgrounds use a two-tone ring: `outline: 2px solid var(--ink); box-shadow: 0 0 0 4px var(--paper)`.
Caveat: needs 3:1 against adjacent colors. Never `outline: none` without a replacement.

**C40. Tuned tap highlight** (trivial)
`html { -webkit-tap-highlight-color: color-mix(in srgb, var(--accent) 18%, transparent) }` plus a real `:active` state. Setting it transparent with no replacement removes essential touch feedback.

**C41. `caret-color`** (trivial)
`input, textarea, [contenteditable] { caret-color: var(--accent) }`.

**C42. `accent-color`** (trivial)
`:root { accent-color: var(--accent) }` recolors native checkboxes, radios and ranges without rebuilding them as divs.

**C43. Restrained custom scrollbars** (trivial)
`.pane { scrollbar-width: thin; scrollbar-color: var(--rule) transparent }`, on inner panes only, never on `<html>`. Do not go below about 10px effective width, which harms motor-impaired users.

**C44. `scrollbar-gutter: stable`** (trivial)
`html { scrollbar-gutter: stable }` so content stops jumping 15px when a modal opens.

**C45. Underline craft** (trivial)
```css
a { text-decoration-thickness: 1px; text-underline-offset: 0.18em;
    text-decoration-skip-ink: auto;
    text-decoration-color: color-mix(in oklab, currentColor 45%, transparent);
    transition: text-decoration-color 150ms, text-underline-offset 150ms; }
a:hover { text-decoration-color: currentColor; text-underline-offset: 0.14em; }
```
Declare offset and skip-ink separately, since neither belongs to the `text-decoration` shorthand.

**C46. Rules rather than boxes in tables** (small)
`border-collapse: collapse`, a single `border-block-end` per cell, a heavier rule under `thead`. No outer frame, no zebra, no vertical rules. For dense tables use `tr:hover` instead of stripes.

**C47. Form field detail** (small)
`input:user-invalid` rather than `:invalid`, which fires before typing. Add `textarea { field-sizing: content; min-height: 4lh }`, and set `inputmode`, `autocomplete` and `enterkeyhint` correctly.

**C48. Cursors as affordances** (trivial)
`grab`/`grabbing` on draggables, `zoom-in` on lightbox images, `col-resize` on table dividers. Never `pointer` on non-interactive text.

**C49. A real print stylesheet** (small)
`@page { margin: 18mm }`, hide nav and footer, expose link URLs with `a[href^="http"]::after { content: " (" attr(href) ")" }`, and `break-inside: avoid` on figures and tables. Almost nobody bothers.

**C50. `:target` highlight for footnote jumps** (trivial)
`.footnote:target { background: color-mix(in oklab, var(--accent) 14%, transparent); scroll-margin-block-start: 4rem }`. The `scroll-margin` is what stops a sticky header covering the target.

**C51. `overscroll-behavior: contain`** (trivial)
On drawers, modal bodies and dropdowns, so scrolling to the end stops yanking the page behind it.

## 4. Micro-interaction craft

**C52. Five genuinely distinct states** (small)
`:hover` shifts the surface, `:active` adds `transform: scale(0.985)`, `:focus-visible` shows the ring, `[disabled]` reduces contrast and explains why, `[data-loading]` puts a spinner inside the button with the width locked so nothing reflows.
Prefer `aria-disabled="true"` when the user still needs to reach the control to learn why it is off.

**C53. Asymmetric enter and exit timing** (trivial)
`.btn { transition: background 250ms } .btn:hover { transition-duration: 120ms }`. Fast in, slow out. Modals exit faster than they enter. Keep any single transition under about 400ms.

**C54. Easing tokens with stated intent** (trivial)
`--ease-out-quart: cubic-bezier(0.25,1,0.5,1)` for entrances, `--ease-in-quart: cubic-bezier(0.5,0,0.75,0)` for exits, `--ease-standard: cubic-bezier(0.4,0,0.2,1)` for in-place moves. Comment why each exists. `transition: all 0.3s ease` is the template signature.

**C55. A real spring, once** (small)
Sample a spring into `linear()` and use it on exactly one gesture. It produces overshoot a cubic-bezier physically cannot. Chrome 113+, Firefox 112+, Safari 17.2+.

**C56. Animate only `transform` and `opacity`** (small)
Replace `height`/`top`/`margin` animation with `translateY()` and `scale()`. Set `will-change` on hover-intent rather than permanently.

**C57. Honor `prefers-reduced-motion` without stripping feedback** (trivial)
Reduce durations to `0.01ms` in the media query, but keep opacity cross-fades, which are usually safe. A state change with no transition still needs a visible difference.

**C58. Animate `display` properly** (small)
`transition: opacity 200ms, overlay 200ms allow-discrete, display 200ms allow-discrete` plus `@starting-style`. Overlays then fade both ways rather than only in.

**C59. Motion that shows causality** (medium)
Set `transform-origin` to the element that triggered the change, so a menu grows from its button corner. Use `view-transition-name` to carry a thumbnail into its detail view. Feature-detect `document.startViewTransition`.

**C60. Hover-intent delay on menus** (trivial)
Slow to close, instant to open: `transition-delay: 300ms` at rest, `0ms` on hover. Keyboard and touch need their own logic.

**C61. Guard hover behind a hover query** (trivial)
`@media (hover: hover) and (pointer: fine)` so hover styles stop sticking after a tap.

**C62. Spinner delay plus a matching skeleton** (small)
Suppress any loading indicator for the first 300–400ms, then show a skeleton whose block sizes match the real line count and card height. A mismatched skeleton is worse than a spinner.

**C63. Empty states with three parts** (small)
Status ("No invoices for October 2026"), a learning cue ("Invoices appear the day after a payment settles"), and a path (a primary button plus a "How billing works" link). Distinguish "no data yet" from "no results for this filter", which need different copy.

**C64. Error states that preserve work** (small)
Say what failed, why, and what to do next. Keep the user's input. Put the message next to the failing control with `aria-live="polite"`. Never clear a form on error.

## 5. Content craft

Every item here is unfakeable, because it derives from facts only you have.

- **Captions that add information.** A `<figcaption>` says what the image does not: subject, place, date, why it is here. Caption and alt text should differ.
- **Credits on every image.** `Photo: Nadia Reyes, 2024`, set in small caps and muted. Stock and generated imagery never carries a name.
- **Machine-readable dates.** `<time datetime="2026-03-14">14 March 2026</time>`, and where it matters, "Published 14 Mar · Updated 2 Aug".
- **A "last updated" that is wired up.** Derive it from git commit time or CMS `updatedAt` at build. A date that never changes is worse than none.
- **A build stamp in the footer.** `v2.4.1 · 8f3c9d2` at 0.75rem, muted.
- **A changelog somebody wrote.** "Fixed: CSV export dropped the last row when the table was filtered. Reported by @ptr." Generated changelogs all say "improved performance and fixed bugs."
- **Footnotes with backlinks**, plus `scroll-margin-block-start` on both ends and an `aria-label` on the return arrow.
- **Author attribution with roles.** "Words by Maya Osei. Charts by Tom Lin." Division of labor implies real labor.
- **Alt text with voice.** `alt="The 1962 prototype, its case pried open, wire nuts still taped to the chassis"` rather than `alt="vintage electronics"`.
- **Microcopy with a point of view.** "Send the invoice" rather than "Submit". "We couldn't reach the payment processor, your card wasn't charged" rather than "Something went wrong".
- **Honest disclosure of limitations,** placed next to the affected feature. "Data through Q2 2026." "Search covers titles only." Marketing copy never admits an edge.
- **A colophon** naming the typefaces, the host, the tools, and one decision you would defend.
- **A 404 written for the person who arrived**, naming what they probably wanted.

## 6. Texture and materiality

- **Grain, placed and restrained.** An `feTurbulence` SVG at 5–10% opacity with `mix-blend-mode: overlay`, on one or two elements rather than the whole page. Use a fixed tiling asset, since turbulence is expensive to rasterize, and never animate `baseFrequency`.
- **Paper and ink rather than white and black.** `--paper: #FDFCF8; --ink: #14120E`, with greys from `color-mix(in oklab, var(--ink) 55%, var(--paper))`. Verify contrast after warming.
- **Rules that behave like rules.** One hairline on one edge, instead of a 1px box around every card.
- **Ink-colored, two-layer shadows.** `0 1px 2px` tight plus `0 8px 24px` diffuse, hue-matched via `color-mix`. `rgba(0,0,0,.1)` is a fingerprint. In dark mode switch to a border or an inner highlight, since shadows barely read.
- **Duotone imagery.** A gradient over the photo with `background-blend-mode: color`. Check text contrast over it, and leave one photo untreated when the subject matters more than the mood.
- **Letterpress on one element.** Inset highlight above, inset shadow below. One element, not a skeuomorphic theme.
- **Mixed media, once.** A scanned note, a real sketch, a whiteboard photograph, at a fractional rotation against clean vector UI. It has to be a genuine artifact, since a generated "sketch" reads worse than none.
- **Deckle edge via `mask-image`** rather than the ubiquitous CSS diagonal `clip-path`.
- **The one weird detail.** A single unjustifiable flourish: a footer ornament that changes with the season, a hover that reveals a type specimen. Exactly one, and it must not block the primary task.

## 7. Evidence of hands

- **Fractional rotation on placed objects.** `rotate(-1.4deg)`, never a round number, never the same twice. Exclude body copy, where rotation degrades subpixel rendering.
- **One irregular gap.** `2.75rem` where the scale says `3rem`, because the neighbor carries weight. Comment it so a later refactor does not "fix" it.
- **A hand-drawn underline.** An inline SVG stroke under a key phrase, `aria-hidden="true"`, with the text still underlined or colored for anyone who cannot see it.
- **Hand-set headlines.** Insert `<br>` at the break you want on the one or two headlines that matter, hidden below the breakpoint. No algorithm chooses a break on meaning.
- **Non-uniform corner radii.** `border-radius: 14px 14px 14px 4px` on a chat bubble. Keep it consistent per component type.
- **Optically equalized elements.** A circular avatar rendered 4% larger than the square thumbnail beside it. Document the offsets or they get normalized away.
- **Quirks that survive because someone liked them.** An old joke in a `<head>` comment, a favicon that changes on the anniversary. Never at the cost of accessibility.
- **Real photographs of real things.** The actual desk, team or hardware, imperfectly lit, credited and dated. The fastest way to prove a person exists. Get consent, and never pass off stock or generated imagery as real.

## Top 15, by signal per hour

1. **C1 Real punctuation.** Applies to every word; straight quotes are the loudest tell.
2. **C11 `text-wrap: balance`** on headings. One selector, every headline widow gone.
3. **C14 Tracking tuned by size.** Three tokens. Nothing else moves a page further from default type.
4. **C39 Brand focus ring.** Carries accessibility and identity in one rule.
5. **C38 Styled `::selection`.** One rule, seen every time a reader drags across text.
6. **C12 `text-wrap: pretty`** on prose. Removes orphans site-wide.
7. **C7 Tabular figures** on anything numeric or live.
8. **C45 Underline craft.** Four lines, and links stop looking like 1998.
9. **C54 + C53 Easing tokens and asymmetric timing.** Replaces `transition: all 0.3s ease`.
10. **C52 Five distinct control states.** Where generated UI is thinnest.
11. **C63/C64 Empty and error states.** The screens nobody generates.
12. **C15 `text-box: trim-both`.** Deletes the whole "label sits high in the button" class of bug.
13. **C46 Rules rather than boxes.** The cheapest way to stop looking like a component-library demo.
14. **C4 `font-synthesis: none`.** Stops shipping smeared glyphs.
15. **Content specificity.** A working "last updated", a build stamp, one real credit, one honest limitation.

## Sources

practicaltypography.com · MDN on `font-variant-numeric`, `font-variant-caps`, `hyphenate-limit-chars`, `transition-behavior`, `interpolate-size`, `-webkit-tap-highlight-color`, `caret-color` · developer.chrome.com on `text-wrap: pretty`, `text-box-trim`, `initial-letter`, linear easing, scrollbar styling · clagnut.com on text-wrap · alistapart.com on web typography in tables · css-tricks.com on hanging punctuation, grainy gradients, `accent-color`, `text-underline-offset`, print URLs · joshwcomeau.com on CSS transitions · nngroup.com on empty-state design · edwardtufte.github.io/tufte-css · railsdesigner.com on optical alignment · ux.redhat.com on focus indicators · web.dev on blend modes · logrocket on optimistic UI · fonts.google.com/knowledge on hanging punctuation
