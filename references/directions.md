# Directions: complete specifications you can commit to

Thirteen art directions, each specified far enough to build from. Pick one in the COMMIT phase, then fill `DESIGN.md` from it and parameterize with `derivation.md`.

**These are starting positions, not finished designs.** A direction taken straight off the shelf produces the same page as everyone else who took it. Section 3 covers the customization that has to follow.

## 1. Choosing a direction

Three filters, applied in order. They exist so two projects running this skill land in different places.

**Filter 1: attributes.** Your disambiguated attributes from `art-direction.md` step 4 narrow the field. The attribute map in section 2 translates each one into concrete grammar.

**Filter 2: what competitors already occupy.** Cross off every direction your competitive audit found clustered. A direction that fits your attributes *and* sits empty on your white-space plot beats one that fits slightly better and is crowded.

**Filter 3: what your content can support.** This one kills more candidates than the other two.

| Direction | Dies without |
|---|---|
| High-Contrast Fashion | genuinely excellent photography |
| Scientific / Data-Forward | real data and real methodology |
| Editorial / Magazine | long-form writing somebody wants to read |
| Archival Index | a large, interesting item set with real metadata |
| Cinematic Dark | production-grade video or product photography |
| Technical Documentation | actual technical depth |
| Terminal / Code Brutalism | users who live in a shell |

Choosing a direction your content cannot feed produces an empty template, which is the failure this skill exists to prevent. When the shortlist is empty after three filters, pick the direction whose failure mode you can most afford and note the gap in `DESIGN.md`.

## 2. Attribute map

The bridge from a brand adjective to a value. Use it to check a direction against your attributes, or to tune one.

**Precise / engineered.** Type: neo-grotesque, display tracking -1% to -2.5%, body 0, tight 1.2 to 1.25 scale, tabular lining numerals throughout, uppercase micro-labels at 11px and +8 to +12% tracking, one family in three or four weights. Color: near-neutral gray ramp, one saturated accent reserved for interactive state, off-black rather than pure black. Geometry: 0 to 2px radius, strict 8pt grid, 1px hairlines at 10 to 15% opacity, borders instead of shadows. Motion: 120 to 180ms, `cubic-bezier(0.4, 0, 0.2, 1)`, no overshoot.

**Warm / human.** Type: humanist sans with large x-height and open apertures, tracking 0 to +0.5%, leading 1.6 to 1.7. Color: warm ground near #FAF7F2 rather than white, ink near #1A1614 rather than black, earth or muted accents, two maximum. Geometry: 8 to 16px radius, 24 to 32px gutters, organic shapes. Motion: 220 to 320ms ease-out with slight overshoot, fade plus an 8 to 12px rise.

**Editorial / serious.** Type: high-contrast or transitional serif display over a restrained sans, 1.333 to 1.5 scale, measure 60 to 75 characters, small caps and hairline rules, two families maximum. Color: paper and ink plus one editorial accent used for emphasis rather than decoration. Geometry: 12 columns with deliberately asymmetric spans, 0 to 4px radius, 4pt baseline, full-bleed imagery breaking the text column. Motion: 200ms opacity only, never on text.

**Playful / irreverent.** Type: geometric or quirky display at 700 to 900, big jumps at 1.5 to 1.618, occasional -2 to +3 degree rotation, mixed case and size inside one headline. Color: three to five high-chroma hues in unexpected pairings, flat fills, minimal gray. Geometry: pill or 20 to 24px radius, 2 to 3px solid borders, hard offset shadows, deliberate overlap. Motion: spring, 400 to 600ms, 8 to 15% overshoot.

**Luxury / restrained.** Type: high-contrast serif or a generously spaced sans, weights 200 to 400, uppercase display at +2 to +8% tracking, one family with whitespace instead of decoration, wordmark kerned by hand. Color: onyx anchor near #0A0A0A, warm ivory near #F4EADE, exactly one accent. Geometry: 0 radius, section padding 120 to 200px, few items per viewport. Motion: 500 to 800ms ease-in-out, opacity or a 1.0 to 1.03 scale, nothing else.

**Utilitarian / tool-like.** Type: neo-grotesque plus monospace, base 13 to 14px, leading 1.4, compressed 1.15 to 1.2 scale, tabular numerals mandatory, mono for IDs and timestamps. Color: neutral ramp, color reserved for semantics and one interactive accent. Geometry: 4px radius, 4pt grid, 8 to 12px control padding, visible borders and table rules, no shadows. Motion: 80 to 120ms or none.

**Institutional / trustworthy.** Type: one flexible family across the estate, base around 19px, leading 1.5 or more, left-aligned single-column measures, hierarchy from size and weight only. Color: a constrained palette where contrast comes from brightness and saturation rather than added black, every pair passing 4.5:1. Geometry: 0 to 2px radius, thick 2 to 4px focus outlines in a bright signal color, 40 to 60px section spacing, no gradients or nested cards. Motion: near zero, decorative animation excluded.

**Raw / underground.** Type: default monospace and system faces used on purpose, no optical tracking correction, violent scale jumps. Color: pure black on pure white plus one high-intensity accent, browser-default link blue retained as a signal. Geometry: 0 radius, hard 1 to 2px borders, asymmetric overlapping blocks over a strict underlying grid. Motion: none, or abrupt and linear.

## 3. Mandatory customization

Every direction below ships as a default. Four changes convert it into yours.

1. **Derive the palette from your own source material** using `derivation.md`. The hex values in each spec are placeholders that prove the structure works. Two sites in one direction should not share an accent.
2. **Pick the display face from the alternatives listed**, driven by your attributes rather than by which name you recognize.
3. **Invent the signature move.** Each spec has a layout signature that identifies the direction. Yours needs one more thing, specific to this project, that no recipe supplied.
4. **Name the exception.** One place where you break your own system on purpose. A direction applied without exception produces that direction's fingerprint.

---

## 4. The directions

### Swiss International / Grid-Driven
**Suits:** design studios, type foundries, architecture practices, developer infrastructure, anything claiming rigor over warmth.
**Display:** Neue Haas Grotesk Display, Suisse Int'l, LL Akkurat, Helvetica Now Display. Free: **Archivo**, **Public Sans**, **Switzer**, **Aileron**.
**Body:** Söhne, ABC Diatype. Free: **Switzer** (79% x-height, holds up dense), **Public Sans**, **HK Grotesk**.
**Type conventions:** exactly two weights, never more. Display tracking -0.02 to -0.03em, body 0, micro-labels uppercase +0.08em at 11px. Leading 0.95 to 1.05 display, 1.5 body. Fixed 1.333 five-step ramp with no fluid clamps between steps. Uppercase reserved for eyebrows and section numbers.
**Palette:** achromatic ramp plus one accent appearing fewer than five times per page. Ground #FFFFFF, ink #111111, secondary #6E6E6E, rules #E5E5E5, accent #E1251B or #0000FF. Color marks a state or a link, never decorates.
**Geometry:** radius 0 everywhere, inputs and images included. 1px hairlines are the entire separation vocabulary. Zero shadows; whitespace and rule weight carry elevation.
**Space:** 12 columns, 8pt base, fixed 24px gutters, margins snapping at breakpoints rather than scaling fluidly. Flush left, baseline aligned. Centered text effectively banned.
**Layout signature:** full-width hairline rules dividing the page into registers, with content hanging *from* the rule rather than floating between rules, a section number in the left margin outside the text column, and one deliberately huge asymmetric void.
**Imagery:** documentary photography at exact grid-column widths or full-bleed, nothing between. No filters, no rounded corners, no shadows.
**Motion:** near zero. 120 to 180ms opacity and transform only.
**Copy:** declarative, noun-heavy, no exclamation marks. "Identity, wayfinding, 2024" beats "We craft unforgettable brands."
**Real examples:** Vercel, xAI, Uber, SpaceX, Optimo, Lineto, A.P.C.
**Fails as:** airport signage, technically correct and emotionally dead, with no hierarchy beyond one grotesque at several sizes. Drift risk: add an 8px radius and a soft shadow and you have re-derived generic SaaS.

### Editorial / Magazine
**Suits:** publications, essays, research, agency thought leadership, food and travel brands, anywhere reading time is the product.
**Display:** Tiempos Headline, Canela, GT Sectra, Lyon Display, Freight Display. Free: **Newsreader** (3 optical sizes, 42 styles), **Fraunces**, **Zodiak**, **Gambetta**.
**Body:** Tiempos Text, Lyon Text, Publico. Free: **Newsreader**, **Literata**, **Source Serif 4**.
**Type conventions:** display at 400 to 500 only. Never bold a high-contrast serif at 80px. Display tracking -0.015em, leading 1.05 to 1.15. Body 18 to 19px, leading 1.6 to 1.75, measure locked at 62 to 72ch. Real optical sizes where the family ships them. `oldstyle-nums` in prose, `lining-nums tabular-nums` in tables. Drop cap via `initial-letter: 3`.
**Palette:** paper, ink, and one editorial accent rather than a brand palette. Ground #FBFAF7 (warm off-white, never #FFF), ink #1A1A18, captions #5C5A54, rules #DCD8CF, accent #A4331F for links and kickers.
**Geometry:** radius 0, 2px maximum on inputs. Hairline rules replace all cards. Zero shadows. A caption sits 8px from its image with a rule, not inside a container.
**Space:** asymmetric 12 columns. Text takes 7, a 2-column marginal rail carries captions and notes, 3 stay empty. Baseline grid. Headings take large space above, tight space below.
**Layout signature:** the **marginalia rail**. Captions, credits, footnotes and pull-quotes live outside the text measure in a narrow side column, so the reading column stays a clean rectangle while metadata orbits it. One pull-quote per ~900 words, breaking the measure at a column edge at 1.5 to 2× body size, no quotation marks.
**Imagery:** art-directed and deliberately varied in size, never a uniform grid of equal images. Every image captioned. Exactly one full-bleed image per article, used as a chapter break.
**Motion:** text never animates in. Images crossfade at ~400ms.
**Copy:** bylines, datelines, standfirsts, kickers. Long sentences allowed. First person allowed. Written by a person with a name.
**Real examples:** WIRED, The Verge, Every, Notion, Sanity.
**Fails as:** a wedding blog, if you reach for Playfair plus Lato plus three decorative pull-quotes. Also fatal: body serif at 1.4 leading, synthesized small caps, or a Didone at 700.

### Technical Documentation
**Suits:** developer tools, APIs, infrastructure, protocol specs, internal platforms.
**Display:** IBM Plex Sans, Geist Sans, Berkeley Mono, Söhne. Free: **IBM Plex Sans**, **Geist Sans**, **Public Sans**.
**Body:** **IBM Plex Sans**, **Switzer**, **Public Sans**.
**Mono, mandatory second family:** **JetBrains Mono**, **IBM Plex Mono**, **Geist Mono**, **Fragment Mono**, **Iosevka**.
**Type conventions:** body 14 to 15px rather than 16 to 18, because docs are scanned rather than read. Leading 1.6 prose, 1.45 code. Mono for every identifier, path, env var, version, flag and unit, inline as well as in blocks. `tabular-nums` on all numerics. Three weights maximum.
**Palette:** neutral ramp, one signal accent, a strict four-token semantic set that never varies. Surfaces #FFFFFF and #F6F7F8, ink #0B0C0E, secondary #6A7178, borders #E3E6E8, accent #0B5FFF, semantics #16A34A / #D97706 / #DC2626 / #0B5FFF.
**Geometry:** radius 4 to 6px applied uniformly, never mixed. 1px borders do all separation. Shadows only on true overlays such as popovers and the command palette, never on cards or code blocks.
**Space:** 4px base (4/8/12/16/24/32/48). Three-pane shell: 240px nav, 68 to 75ch content, 220px anchor rail. Whitespace is not a design feature here.
**Layout signature:** persistent left nav tree plus a right "On this page" rail, with **code blocks breaking the text measure** out to full content width, each carrying a language tag, a copy button and a filename strip.
**Imagery:** diagrams, never photographs. Line diagrams share the UI's stroke weight and palette. Screenshots cropped tight with a 1px border, no fake browser chrome, no shadow, no perspective.
**Motion:** effectively instant, 100 to 150ms. Smooth anchor scrolling is the whole motion budget.
**Copy:** imperative second person, present tense. "Install the CLI. Set `API_KEY`. Run `deploy`." Zero adjectives, zero benefit claims.
**Real examples:** Mintlify, ClickHouse, Stripe Docs, IBM Carbon, Supabase, Cal.com.
**Fails as:** mono applied to everything until nothing is emphasized, or docs styled like a marketing page with 18px body and hero gradients, which destroys scan speed.

### Terminal / Code Brutalism
**Suits:** dev tools, CLI products, security, AI infrastructure, indie technical portfolios.
**Display:** **Berkeley Mono** (paid), **Geist Mono**, **Departure Mono** (pixelated 1980s computing), **Terminal Grotesque**, **VG5000**.
**Body:** **Geist Mono**, **IBM Plex Mono**, **JetBrains Mono**, **Fragment Mono**, **Iosevka**, **Sligoil**.
**Type conventions:** one monospaced family, two weights, everything 13 to 15px. **Hierarchy comes from color and brightness rather than size**, which is the defining constraint. Uppercase headers at +0.05em. Line-height locked to a fixed character-cell row (20px) so text sits on a terminal matrix.
**Palette:** near-black ground, one phosphor accent, a three-step gray ramp. Ground #0A0A0A, surface #141414, primary #E6E6E6, dim #7A7A7A, rules #262626, accent #00E599 or #FFD100.
**Geometry:** radius 0. 1px borders forming closed boxes that echo box-drawing characters. No shadows. Dividers built from repeated characters (`─────`, `······`) are idiomatic rather than lazy.
**Space:** a character grid. Widths in `ch` (`max-width: 80ch`), vertical rhythm in fixed row heights. Things line up because they share a character width.
**Layout signature:** the page reads as a **terminal session**: fixed-width text block, ASCII rules, bracketed index labels (`[01]`), a blinking caret, box-drawn frames instead of cards, a status line at the bottom.
**Imagery:** ASCII art, 1-bit dithered images, wireframe diagrams. Photographs posterized to 2 to 4 tones.
**Motion:** one typewriter reveal maximum, caret blink at `1s steps(2, start)`. Motion reads as latency here, so keep it near zero.
**Copy:** terse, lowercase, command-shaped. Status lines, exit codes, a version and commit hash in the footer.
**Real examples:** Ollama, Warp, Resend, OpenCode.
**Fails as:** punishing. Monospaced body copy past ~400 words genuinely hurts to read, so put prose in a sans. Green-on-black on a non-technical product is a costume and gets spotted instantly.

### Brutalist / Raw HTML
**Suits:** artist and studio portfolios, cultural projects, anti-corporate fashion, archives, manifestos.
**Display:** the system stack itself, Times New Roman, Helvetica. Or libre picks with character: **Karrik** (deliberate weight and width irregularities), **Le Murmure**, **Terminal Grotesque**, **Redaction**.
**Body:** system-ui stack, Times, Georgia. Free: **Public Sans**, **Karrik**.
**Type conventions:** browser defaults are a legitimate decision here. `h1 { font-size: 2em }` untouched. No tracking adjustments. Underlined links in #0000EE, visited #551A8B. Sizes may jump violently with nothing between them.
**Palette:** default-adjacent, near-monochrome, one violent accent. #FFFFFF, #000000, link #0000EE, visited #551A8B, accent #FF3B00. Color is a shout rather than a system.
**Geometry:** radius 0 absolutely, buttons and inputs included. Borders 1 to 3px solid black. No shadows. Elements may overlap and collide.
**Space:** no grid, or a visible one. Asymmetric and very large margins. Density varies wildly between sections.
**Layout signature:** **the page shows its own bones.** Outlined boxes, a nav that is visibly a `<ul>`, exposed anchors, raw reflow, one long scroll punctuated by hard black rules.
**Imagery:** unretouched, visibly compressed, sometimes deliberately low-resolution. No consistent crop ratio. Alt text sometimes surfaced as a visible caption.
**Motion:** none, or exactly one aggressive interaction. Never a tasteful fade.
**Copy:** blunt, first person, zero marketing register. Lists over prose.
**Real examples:** Balenciaga (identity by Bureau Borsche), Are.na, Gucci Vault, Craig Ward.
**Fails as:** hostility mistaken for rigor. Unusable navigation, 2:1 contrast, 8px type. Brutalism is a claim about honesty of structure, not a licence to fail WCAG. If a visitor cannot find the work, the position collapses.

### Neo-Vintage / Print Revival
**Suits:** spirits, skincare, coffee, hospitality, member clubs, heritage-coded DTC.
**Display:** ITC Garamond, Benton Modern, Mrs Eaves, Filosofia, ITC American Typewriter. Free: **Basteleur**, **Bespoke Serif**, **Cormorant**, **Inknut Antiqua**, **BioRhyme**, **Redaction**.
**Body:** **Cardo**, **EB Garamond**, **Neuton**, **Alegreya**, **Gelasio**. Premium: Sabon, Plantin.
**Type conventions:** `oldstyle-nums` in prose. **Real** small caps on a family that ships them (Mrs Eaves does), tracked +0.05em. Discretionary ligatures on. Display at 400 with leading 1.1 to 1.2. Italic as a distinct voice for decks and asides rather than mere emphasis.
**Palette:** aged paper and printing inks, never pure white or pure black. Stock #F3EBDD, ink #2B2118, secondary #7A6A55, accents #1D3557 (process blue), #9B2226 (rubine), #C6812E (ochre). Two ink colors maximum per page, as if it were a two-color press run.
**Geometry:** radius 0. Ornamental rules replace borders: double rules, thick-thin pairs, hairline frames on images. No shadows. A paper-grain or halftone overlay at 3 to 6% opacity unifies the page.
**Space:** symmetric composition is permitted here, unlike Swiss. Wide book-like margins. Centered title blocks are correct rather than a mistake.
**Layout signature:** **the title block.** A centered display line, a thick-thin rule beneath it, a small-caps deck, and an issue or date line, sitting on a textured ground, with every image inside a hairline frame and every caption in italic beneath.
**Imagery:** warm-shifted photography, halftone or duotone, or engraved line art. Always framed, always captioned. Grain ties disparate sources together.
**Motion:** crossfades only, slow at 500 to 700ms, and rare. Motion should feel like paper.
**Copy:** period-flavored without cosplay. Products numbered ("No. 04"). Ingredient lists and provenance.
**Real examples:** Vacation (verified as ITC Garamond plus Benton Modern), Poolsuite.
**Fails as:** theme-park pastiche. A wood-type font, a sepia filter, a paper texture, and no typographic craft underneath. The instant tell is synthesized small caps and lining figures in running text.

### Warm Organic / Humanist
**Suits:** wellness, ceramics, food, care products, climate, education, AI products wanting to read as non-threatening.
**Display:** **Fraunces** (variable, SOFT and WONK axes), **Sentient**, **Gambetta**, **Alegreya**. Premium: GT Alpina, Canela, Ogg.
**Body:** **Alegreya Sans**, **Karla**, **Work Sans**, **Proza Libre**, **Newsreader**.
**Type conventions:** a warm serif display over a humanist sans body, or the inverse. Two weights. Tracking 0 to -0.01em, never tight. Leading deliberately loose at 1.65 to 1.8. Sentence case everywhere. On Fraunces, set `WONK` to 1 and `SOFT` to 20 to 40 for hand-made warmth without novelty.
**Palette:** desaturated earth tones, one saturated bloom, one genuinely dark anchor. Ground #FAF6F0, ink #34302A, muted #8A8377, sage #6B7F5E, terracotta #C1663B. Keep saturation under ~45% except for the single accent.
**Geometry:** radius large and soft at 12 to 20px, or organic on decorative shapes. Borders rare, with separation from a tonal background shift. Shadows soft and **warm-tinted**: `0 6px 24px rgba(60,45,30,0.06)`, never neutral gray.
**Space:** relaxed. 8pt base with generous multiples (48/64/96/128). Max width ~68ch. Adjacent blocks offset a few pixels vertically so the page never reads as machined.
**Layout signature:** **one off-grid handmade element per view.** A hand-drawn arrow, a scanned botanical, a marker underline beneath a keyword, a photo rotated 1.5deg, placed to break an otherwise calm layout.
**Imagery:** natural light, warm white balance, real hands and materials. Arch-topped or rounded masks. Film grain at ~4%. No stock-photo gloss.
**Motion:** slow ease-out, 500 to 700ms, `cubic-bezier(0.16, 1, 0.3, 1)`. Elements drift rather than snap. Nothing bounces.
**Copy:** first person plural, plain words, short paragraphs. Talks about process, materials and people. Admits limits.
**Real examples:** Claude, Airbnb, Clay.
**Fails as:** oatmeal. Beige on beige, #C9BFB2 text on #F5F0E8, no contrast anywhere, every corner at 16px. Without one dark anchor and one saturated accent the whole thing dissolves.

### High-Contrast Fashion Editorial
**Suits:** fashion, eyewear, furniture, galleries, music, photographers. Anywhere the imagery is genuinely excellent.
**Display:** Druk, Monument Extended, Obviously, Tusker Grotesk. Free: **Boska**, **Stardom**, **Archivo Expanded**, **Bebas Neue**.
**Body:** Suisse Int'l, Neue Haas Grotesk, ABC Diatype. Free: **Switzer**, **Archivo**, **Public Sans**.
**Type conventions:** only two sizes exist, enormous and small. Display at `clamp(3rem, 12vw, 14rem)`, tracking -0.03 to -0.05em, leading 0.85 to 0.92, uppercase. Body and captions 13 to 14px, micro-labels 10 to 11px uppercase at +0.15em. Nothing occupies the middle of the scale, and that emptiness is the effect.
**Palette:** monochrome plus the photography. #FFFFFF, #000000, #E4E4E4, and at most one saturated hit such as #FF2D00. All chromatic energy comes from imagery.
**Geometry:** radius 0. Hairlines used like registration marks. No shadows. Buttons are underlined text or a 1px rectangle, never a filled pill.
**Space:** full-bleed, with a page gutter as small as 16 to 24px so imagery touches the viewport. Vertical space between sections enormous at 160 to 240px. Text pinned to corners rather than centered.
**Layout signature:** **type at architectural scale, cropped by the viewport**, over or beside a full-bleed image, with the only other text on screen a 10px uppercase caption in a corner. It should look like a spread rather than a page.
**Imagery:** full-bleed, aggressively cropped so the subject exits the frame. 4:5 and 3:4 ratios. No rounded corners, no gradient overlays.
**Motion:** clip-path or mask wipes at 600 to 900ms. Horizontal-scroll galleries. The cursor becomes a text label. Motion is choreographed.
**Copy:** almost nonexistent. Season names, collection numbers, material lists. Silence is the tone.
**Real examples:** Balenciaga, Nike, Bugatti, Tesla.
**Fails as:** enormous type with nothing behind it. This direction depends entirely on good photography and dies without it. Second failure: 12vw display reflowing into five orphan lines at 375px.

### Utilitarian Tool / Density-First
**Suits:** issue trackers, email clients, trading and analytics dashboards, admin panels, launchers.
**Display:** none. The body family is the display family. Söhne, ABC Diatype, Geist Sans. Free: **Switzer** (79% x-height, built for dense dashboards), **Public Sans**, **Archivo**, **Geist Sans**.
**Body:** **Switzer**, **Public Sans**, **IBM Plex Sans**, **Geist Sans**. **Mono** for IDs and timestamps: **JetBrains Mono**, **Geist Mono**.
**Type conventions:** base 13px, not 16. Leading 1.4 to 1.5. Weights 400/500/600, never 700. Tracking -0.005em at 13px. `tabular-nums` mandatory on every column of numbers. Uppercase only on 10px table headers at +0.06em. A strict three-level text-color ramp does all hierarchy work.
**Palette:** dark-first neutral ramp, one high-chroma accent, semantics. Ground #08090A, surface #131416, border #1F2023, primary #E6E6E7, secondary #8A8F98, accent #5E6AD2. Note that indigo is the category convention here (Linear, Superhuman, Kraken all land there), so pick a different hue when differentiation matters more than genre legibility.
**Geometry:** radius 4 to 6px. 1px low-contrast borders carry all separation. Shadows only on floating layers such as the command palette. Cards never have shadows.
**Space:** 4px base. Fixed row heights (28/32/36px). Padding 8 to 12px, never 24. Sidebar locked at 240px. Numerics right-aligned. Whitespace is a cost here rather than a feature.
**Layout signature:** a **persistent three-pane shell** (nav, list, detail) with a ⌘K palette overlay, every row exposing its keyboard hint on hover, and zero decorative gap between rows. Every action is a UI element, a shortcut, and a palette entry at once.
**Imagery:** essentially none. One 16px icon set at a single stroke weight. Avatars at 20 to 24px.
**Motion:** 80 to 150ms ease-out. The palette opens instantly. **No entrance animations on lists**, since rows must feel like they were already there. Optimistic updates so the UI never appears to wait.
**Copy:** terse labels, verbs, no articles. "Assign to", "Due", "3 open", "Merged 2h ago". Tooltips carry the shortcut.
**Real examples:** Linear, Superhuman, Raycast, Sentry.
**Fails as:** a wall of noise. 13px gray-on-gray with no anchor. Adding breathing room to fix it just makes a worse tool with more scrolling.

### Neubrutalist / Toy
**Suits:** creator tools, community products, education, kids and family, games, dev-tool marketing that wants to feel un-corporate.
**Display:** **Syne** 800, **Archivo Black**, **Bebas Neue**, **Stardom**. Premium: Obviously, Hobeaux.
**Body:** **Public Sans**, **Karla**, **Work Sans**, **Chivo**. **Mono:** Space Mono, JetBrains Mono.
**Type conventions:** display at 700 to 900 only, tracking -0.02em, leading 0.95. Body 400 at 16 to 18px, leading 1.5. Buttons and labels uppercase. Scale ratio 1.5 or higher, with big obvious jumps.
**Palette:** flat unapologetic fills side by side on cream or white, no gradients. Published token set: black #000000, off-white #FFFDF5, yellow #FFD23F, coral #FF6B6B, sky #74B9FF, green #88D498, orange #FFA552, lavender #B8A9FA. Minimum 4.5:1 against text.
**Geometry:** radius 0. Border `3px solid #000` (2px thin, 4px thick variants). Hard offset shadows with zero blur: `3px 3px 0 0 #000`, scaling to `12px 12px 0 0`. These two properties are non-negotiable, and removing either collapses the style.
**Space:** a conventional grid underneath, disrupted only at macro level. Chunky internal padding at 20 to 32px. Elements may overlap by 8 to 16px. Micro-alignment stays mechanically precise, and reading order stays predictable.
**Layout signature:** **every surface is a bordered box with a hard offset shadow on a flat color field, and it physically moves on press.** Hover `translate(-2px,-2px)` with the shadow growing 2px, active `translate(3px,3px)` with `box-shadow: none`, transitions 0.1 to 0.15s. Focus ring `outline: 3px solid #74B9FF; outline-offset: 3px`.
**Imagery:** cut-out PNGs, flat vector illustration, sticker shapes, saturated photography with a 3px black border. No gradients, no glassmorphism.
**Motion:** fast and physical, 100 to 150ms. The press state is the motion language.
**Copy:** loud, funny, second person. Exclamation marks are earned here rather than banned. Self-aware.
**Real examples:** Gumroad (the 2021 redesign is the canonical case), Tony's Chocolonely, Figma, PostHog.
**Fails as:** borders and offset shadows bolted onto a generic SaaS template. The style only holds when color and copy are equally loud. Also: 3px black borders are invisible on dark grounds, so this is light-mode-only unless you invert the border color.

### Archival Index / Institutional Catalog
**Suits:** type foundries, galleries, libraries, research collections, studio work indexes, curated reference sites.
**Display:** **Karrik**, **Le Murmure**, **Archivo Narrow**, **Syne**. Premium: Basis Grotesque, ABC Favorit, Monument Grotesk.
**Body:** **Public Sans**, **Archivo**, **Work Sans**, **Source Serif 4**. **Mono for metadata, required:** **DM Mono**, **Space Mono**, **Fragment Mono**.
**Type conventions:** small type is the point. Body 13 to 14px, metadata 11px. Two weights maximum. Uppercase category labels at +0.08em. Leading tight at 1.45. Visible numbering everywhere (`001`, `[04]`, `No. 0231`) in tabular figures. Dates in a fixed format.
**Palette:** muted and near-monochrome so specimens carry the color. Ground #F2F0EC, item surfaces #FFFFFF, ink #1C1B19, metadata #767268, rules #DAD6CE, one desaturated accent #5A6E5E for active filter state only.
**Geometry:** radius 0. 1px rules everywhere: around thumbnails, between rows, beneath labels. No shadows. Single exception: tags as 1px outlined pills at 2px radius.
**Space:** dense. Four to six column thumbnail grids with small 8 to 16px gutters. Rows separated by hairlines rather than gaps. Tight outer margins, so the page feels full, like a plan chest.
**Layout signature:** **exposed taxonomy.** Every item carries a visible index number, date and category tag. A persistent filter rail lives in the margin. The grid toggles to a list view whose columns read like a catalog record: No. / Title / Type / Year / Collection.
**Imagery:** uniform thumbnail ratio, no crop drama, a consistent 1px border on every image. Images are specimens rather than heroes.
**Motion:** hover reveals metadata at 120ms. Filtering is instant and unanimated, so it feels like a query rather than a transition.
**Copy:** neutral and descriptive, like a catalog entry. "Poster, offset lithograph, 700 × 1000mm, 1974. Collection no. 0231."
**Real examples:** Are.na, Fonts In Use, Optimo.
**Fails as:** a spreadsheet with better fonts, without a strong image set or genuinely interesting metadata. Watch contrast: 11px #767268 on #F2F0EC sits at the floor, so verify it.

### Scientific / Data-Forward
**Suits:** research organizations, public-interest data, biotech, climate and health reporting, analytics products with a point of view.
**Display:** **Source Serif 4** (5 optical sizes), **Literata** (4 optical sizes), **IBM Plex Serif**. Premium: Greta Text, Publico.
**Body:** **Source Sans 3**, **Noto Sans**, **Lato**, **IBM Plex Sans**, **Literata**, chosen because all ship **tabular lining figures**, which is the real selection criterion.
**Numerals:** **Recursive** (multiplexed, so character widths stay constant across weights and numbers do not reflow when bolded), **IBM Plex Mono**.
**Type conventions:** prose in a serif at 17 to 18px, leading 1.7, measure 65 to 70ch. Every chart label, axis and UI element in a sans at 12 to 13px. `tabular-nums lining-nums` on all figures. No chart label below 11px. Captions numbered ("Fig. 3") above a source line.
**Palette:** a neutral page and a **separate, disciplined** chart palette: a colorblind-safe categorical set plus sequential and diverging ramps that never mix. Page #FFFFFF / #16181D. Series #4269D0, #EFB118, #FF725C, #6CC5B0, #3CA951. Grid #E4E6EB, annotation #6B7280. Chart color encodes data and never decorates.
**Geometry:** radius 0 to 3px. 1px axis and grid rules, with grid strictly lighter than axis. **No shadows anywhere.** A chart with a drop shadow is the fastest credibility tell there is.
**Space:** narrow reading column with figures breaking out wider. 8px base. Consistent figure margins so charts optically align across thousands of pixels of scroll.
**Layout signature:** **the article column with break-out figures.** Body at ~68ch, charts stepping out to roughly 1.4× that width and occasionally full-bleed, each with a numbered caption, an explicit source line, and a link to data and methodology.
**Imagery:** charts, not photographs. One chart carries one idea. Direct-label series on the plot instead of using a legend where geometry allows. Annotations inside the chart.
**Motion:** transitions only when they encode a change, such as a filter or a year step, at 300 to 400ms. Never animate a chart on entrance, which implies the data is arriving.
**Copy:** precise, hedged where hedging is honest, units always stated. "Deaths per 100,000, age-standardised." Sources cited inline. Uncertainty stated rather than smoothed.
**Real examples:** Our World in Data, Observable, Datawrapper.
**Fails as:** decorated data. Gradient-filled bars, 3D, drop shadows, rainbow categorical palettes, 9px axis labels. Second failure: a beautiful article template wrapped around charts that are still default library output.

### Cinematic Dark / Product Theater
**Suits:** hardware, automotive, AI media tools, launches. Anywhere a single object must feel monumental.
**Display:** Monument Extended, Druk Wide, Termina, Obviously. Free: **Archivo Expanded**, **Bebas Neue**, **Stardom**, **Boska**.
**Body:** Suisse Int'l, Söhne, ABC Diatype. Free: **Switzer**, **Public Sans**, **Geist Sans**.
**Type conventions:** display uppercase, tracking +0.02 to +0.08em when small and -0.02em when huge. Commit to one weight extreme, 300 for elegance or 800 for force, never both. Body 15 to 16px at 1.6. Body text is never pure white on black; #E8E8EA reduces halation.
**Palette:** true or near-black ground, exactly one accent, all remaining light from imagery. Ground #000000 or #0B0B0C, raised surface #141416, primary #E8E8EA, secondary #8E8E93, accent #D4AF37, #E10600 or #00E599. A second accent destroys the effect.
**Geometry:** radius 0 to 4px. Borders as `1px solid rgba(255,255,255,0.08)`. Shadows are useless on black, so elevation comes from a subtle radial glow or a genuinely lighter surface tone.
**Space:** full-viewport sections where each scroll step is one shot. Content pinned to a corner or the lower third, never vertically centered in a card. Sections separated by darkness rather than spacing tokens.
**Layout signature:** **full-viewport media as the ground with minimal type in the lower third**, chaptered so each scroll-snap section reads as a new camera shot, plus a thin progress indicator down one edge.
**Imagery:** the video and photography are the design. Dark-graded, high dynamic range, subject lit against black, always full-bleed. The only permitted overlay is a bottom-up scrim for legibility.
**Motion:** the one direction where motion is primary. Scroll-linked reveals at 600 to 1200ms, `cubic-bezier(0.22, 1, 0.36, 1)`. Muted autoplay loops. Ship a static poster frame under `prefers-reduced-motion`.
**Copy:** very few words, present tense, high confidence. Specification numbers promoted to display type ("1,479 hp", "0–100 in 2.1s"). No paragraphs above the fold.
**Real examples:** Bugatti, Lamborghini, Tesla, Shopify, Runway, ElevenLabs.
**Fails as:** dark mode as a mood with nothing behind it. #000 background, generic stock video, 4.2:1 gray body text. Also a 30MB hero video with no poster frame, which makes the whole premise a blank black screen for three seconds.

### Libre / Post-Digital Experimental
**Suits:** cultural institutions, festivals, music, art schools, zines, personal sites, anything with a curatorial voice.
**Display:** **Le Murmure**, **Pilowlava**, **Basteleur**, **Gulax**, **Fungal**, **Lithops**, **Trickster**, **Avara**, **Outward**, all Velvetyne and all libre.
**Body:** **Karrik**, **Compagnon**, **Sligoil**, **VG5000**, with **Public Sans** as the sober partner that keeps it readable.
**Type conventions:** one wild display face carries the identity, paired with one quiet body face. Never two wild faces. Use OpenType alternates deliberately, since Le Murmure ships randomizing alternates by design. Tracking may go extreme (+0.3em) on a single word. Sizes may mix within a line. Variable axes animated or randomized on interaction.
**Palette:** high-chroma and unexpected, often two colors that should not work together. #101010, #F0EFEA, #FF4A1C, #1E00FF, #C6FF00. Or duotone the page and let imagery inherit it.
**Geometry:** radius 0 or absurd. Border treatment intentionally inconsistent. No shadows; depth comes from overlap and `mix-blend-mode: difference`.
**Space:** a broken grid. Elements overlap, rotate and hang off the viewport. A hidden 12-column grid still exists and gets violated in only two or three deliberate places, and that ratio is what separates this from noise.
**Layout signature:** **type as image.** One word set enormous, then cropped, rotated or masked by a photograph, while the rest of the page stays conventionally organized so the disruption reads as a decision.
**Imagery:** scanned, photocopied, halftoned, blend-moded. Collage with visible tape and tears. Low resolution is often the point.
**Motion:** one signature interaction only, with everything else completely still.
**Copy:** essayistic or cryptic. Lowercase. Often bilingual. Credits long and specific.
**Real examples:** Velvetyne, Studio Brot, Craig Ward.
**Fails as:** noise without a spine. If everything is broken, nothing reads as intentional. Practical trap: these libre display faces often lack italics, hinting and non-Latin coverage, so never set body copy in Pilowlava, Fungal or Trickster.

---

## 5. Free type shelf

Verified as free or self-hostable. The overused shelf (Inter, Poppins, Montserrat, Space Grotesk, Sora, Outfit, DM Sans, Plus Jakarta, Figtree, Manrope, Playfair, Instrument Serif, Bricolage) is deliberately absent.

**Neutral grotesques.** **Switzer** (Fontshare, 79% x-height, the best free Inter replacement) · **Public Sans** (OFL, civic and institutional) · **Archivo** with Narrow, Expanded and Black (OFL, extreme width range in one family) · **Geist Sans** (Vercel, OFL) · **Mona Sans** and **Hubot Sans** (GitHub, OFL) · **Aileron** and **Nacelle** (Dot Colon) · **HK Grotesk** · **General Sans** and **Supreme** (Fontshare) · **Libre Franklin** · **Chivo** · **Work Sans** · **Be Vietnam Pro**.

**Reading serifs.** **Newsreader** (3 optical sizes, 42 styles) · **Literata** (4 optical sizes) · **Source Serif 4** (5 optical sizes, variable) · **Spectral** · **Alegreya** with **Alegreya Sans** · **EB Garamond** (true old-style figures) · **Cardo** (wide glyph coverage) · **Gelasio** (metrics-compatible with Georgia) · **Neuton** · **Lora**.

**Display serifs with attitude.** **Fraunces** (SOFT and WONK axes) · **Zodiak** · **Boska** · **Gambetta** · **Sentient** · **Bespoke Serif** and **Bespoke Stencil** · **Cormorant** (display only, breaks below 24px) · **Inknut Antiqua** · **BioRhyme** · **Eczar** · **Basteleur** (Velvetyne) · **Redaction** (7 grades of print degradation; **free for personal use only, commercial licence on request**).

**Monospace.** **JetBrains Mono** · **IBM Plex Mono** · **Geist Mono** · **DM Mono** · **Space Mono** (rare personality in a free mono) · **Fragment Mono** (survives as body copy) · **Iosevka** (very dense) · **Departure Mono** (pixelated 1980s) · **Cascadia Code** (real cursive italic) · **Recursive** (multiplexed widths) · **Terminal Grotesque**, **Compagnon**, **Sligoil** (Velvetyne).

**Condensed and poster.** **Le Murmure** (randomizing alternates) · **Bebas Neue** · **Archivo Black** and **Expanded** · **Syne** · **Stardom** · **Oswald** · **Khand** and **Teko** · **Gulax**.

**Vernacular and character-first.** **Karrik** (deliberate weight disadjustments, usable at body sizes) · **VG5000** · **Pilowlava**, **Fungal**, **Lithops**, **Avara**, **Outward**, **Trickster**, **Format 1452** (all Velvetyne, display only) · **Chillax** · **Lexend** (tuned for reading proficiency and dyslexia).

**Chart-safe, all shipping tabular lining figures.** **Lato** · **Noto Sans** · **Source Sans 3** · **IBM Plex Sans** · **Recursive** (numbers do not reflow when a cell bolds on hover).

**Licensing cautions.** Fontshare families are covered by the ITF Free Font License covering personal and commercial use. Velvetyne families are libre but frequently lack italics, hinting and non-Latin coverage, so verify the glyph set before committing one to body text. Redaction is the one non-open item here.

## 6. What is verified and what is specification

**Verified against primary or specimen sources:** Vacation uses ITC Garamond plus Benton Modern (Fonts In Use). Every uses Signifier plus Switzer. Our World in Data uses Playfair Display plus Lato. The Balenciaga identity is Bureau Borsche with a bespoke condensed bold. Gumroad's 2021 redesign is the origin case for neubrutalism. The neubrutalist token values (border widths, shadow offsets, palette hexes) are published spec, quoted exactly.

**Specification defaults rather than claims:** all other hex palettes, all leading, tracking and scale numbers, all motion timings, and all layout-signature descriptions. They are concrete and buildable, but do not cite them as a named site's actual tokens.

## Sources

typewolf.com (Site of the Day, Google Fonts and Adobe Fonts lists) · creativeboom.com top 50 fonts 2026 · getdesign.md brand design-system catalog · velvetyne.fr · fontshare.com · untitledui.com free fonts · madegooddesigns.com monospace 2026 · neubrutalism.com · nngroup.com on neobrutalism · datawrapper.de on fonts for data visualization · ourworldindata.org on their visualization redesign · nightingaledvs.com · pros.squarespace.com on the archival index trend · siteinspire.com · fontsinuse.com · bureauborsche.com · lineto.com · mattstromawn.com on UI density · blog.superhuman.com on command palettes · carmenansio.com on editorial typography in CSS
