# Catalog 3/7 — Typography (#94–121)

Font choices, pairing, hierarchy, headline styling, labels, casing, micro-typography. Severity: **instant** / **strong** / **mild** (see SKILL.md).

## Font choice

**94. Inter as the only typeface** (instant)
Tell: `font-family: Inter` (or Inter → system-ui) for headline, body, buttons, and labels alike.
Why: Inter has become the Helvetica of the LLM era — the most-used face in training data and the single most recognizable signature of a generated site.
Fix: keep Inter for UI text if needed, but self-host a characterful display face for headlines (Fontshare's Clash Display/Cabinet Grotesk/Satoshi, or foundry faces like Söhne, GT Sectra, Tiempos); the identity must not rest on a neutral grotesque alone.

**95. The trendy-font shelf** (strong)
Tell: Space Grotesk, Sora, Syne, Outfit, Manrope, Plus Jakarta Sans, DM Sans, Figtree — the Google-Fonts "modern startup" rotation, used straight.
Why: these are the faces models name when told "not Inter"; they appear in ~15.8% of audited AI pages and now co-signal generated design.
Fix: choose type by brief, not availability — browse beyond Google's top-50 (Fontshare, Klim, Grilli, ABC Dinamo, OH no Type); test by setting your real H1 and asking whether the screenshot could belong to any other startup.

**96. Poppins geometric-rounded default** (strong)
Tell: Poppins everywhere — perfectly circular O's, wide friendly geometry — on headings and body of "approachable" sites.
Why: the pre-AI freelancer default the models absorbed; paired with pastel gradients it screams template.
Fix: if geometric warmth is the goal, use a face with text optimization and character (General Sans, Gabarito sparingly, or a licensed geometric); never set long body copy in a display geometric.

**97. Untouched Geist outside Vercel** (strong)
Tell: `GeistSans`/`GeistMono` from `next/font` as the whole identity of a non-Vercel product.
Why: Geist is Vercel's commissioned brand voice; unmodified it marks "scaffolded with a Next.js AI template."
Fix: treat Geist as scaffolding — swap the display layer for a face chosen for this brand, or at minimum re-tune weights/tracking and pair against a contrasting display serif or slab.

**98. The "not-Inter" escape hatch** (mild)
Tell: Bricolage Grotesque, Schibsted Grotesk, Hanken Grotesk, or Onest chosen as the "distinctive" alternative — straight from the same Google shortlist.
Why: the second-ring Google faces are what models pick when prompted "avoid Inter," so they now pattern-match in aggregate.
Fix: source the display face from an actual foundry or licensed catalog, self-host it, and customize deployment (weight axis, tracking, optical size) so even a known face is set in a non-default way.

**99. Fraunces/Playfair editorial cosplay** (mild)
Tell: Fraunces, Playfair Display, or Cormorant headline + cream background + brown ink — instant "artisanal" preset, often with gold accents.
Why: these display serifs are reached for whenever something needs to feel expensive, making the shortcut itself recognizable.
Fix: if editorial is right, use a serif with different provenance (Newsreader, GT Sectra, Tiempos Headline, Gambarino) tuned via optical-size axes, paired with a non-obvious text face rather than the cream-and-gold kit.

**100. Instrument Serif oversized italic hero** (instant)
Tell: huge Instrument Serif (usually italic) display headline on an otherwise sans page.
Why: the 2025 generated-landing signature — "oversized italic serif as primary hero has become the universal AI-startup hero."
Fix: set the display in roman with deliberate tracking, or choose a different characterful display face entirely; keep italics for genuine emphasis inside running text.

## Pairing & hierarchy

**101. No pairing — headline is body scaled up** (strong)
Tell: one neutral sans at one weight doing every job; the H1 is literally body text at 64px.
Why: the clearest generated-typography tell — a single neutral sans for headings and body.
Fix: a two-voice system — expressive display face for H1/H2 + restrained text face for everything else; if one family must stay, exploit its extremes (Black vs Book, condensed vs normal, optical sizes).

**102. The canned pairing** (strong)
Tell: recurring combos — Space Grotesk heads/Inter body, Instrument Serif accents/Geist body — recycled across unrelated generated sites.
Why: LLM pairing suggestions converge on the same few duos, so the pairing itself is now a fingerprint.
Fix: pair by contrast logic (era, width, construction) from at least one non-default source — a sharp Dutch serif with a plain grotesk, a mono-display with a humanist text face; verify the combo doesn't appear in font-pairing listicles.

**103. Flat type scale** (strong)
Tell: h2/h3/body sizes clustered within a few px (20/18/16), nothing clearly most important; hierarchy attempted via gray shades alone.
Why: models emit "safe" incremental scales; absence of decisive jumps is a core generated-typography tell.
Fix: rebuild on a ≥1.25 ratio with one deliberately oversized display step; each level must differ by at least two of size/weight/spacing so reading order is obvious at squint distance.

**104. Two-weight universe** (mild)
Tell: entire site set in exactly 700 and 400 — no medium, no semibold, no light display weight — despite loading a 9-weight variable font.
Why: default Tailwind classes drive weight choice, so generated pages ignore the loaded family's range.
Fix: assign weights by role (display 650–800 tuned to the face, UI labels 500–550, body 400–450) using the variable axis; big type usually wants less weight than models give it.

**105. Two-tone text hierarchy (white + gray-400)** (strong)
Tell: every heading pure white, every other string `text-gray-400`/`text-muted-foreground` — the entire hierarchy expressed as one gray.
Why: heading-white/body-muted is the shadcn/LLM default pair; real systems mix weight, size, spacing, and more than two ink values.
Fix: introduce third and fourth ink steps (e.g., 95%/78%/60% L) mapped to real priority levels; let some secondary text keep full contrast at a smaller size instead of graying out.

**106. Monospace as house voice** (strong)
Tell: JetBrains Mono/IBM Plex Mono/Geist Mono on eyebrows, captions, dates, copyright lines, and nav of a non-code product.
Why: reflexive mono outside data contexts — models use it to signal "technical" the way they use purple to signal "premium."
Fix: reserve mono for genuine data (code, timestamps, IDs, prices) with tabular figures; set editorial micro-text in the text face at a smaller size/weight step.

## Headline styling

**107. Gradient keyword via bg-clip-text** (instant)
Tell: exactly one word of the hero headline set in `bg-clip-text text-transparent bg-gradient-to-r from-indigo-500 to-purple-600`.
Why: the gradient-highlighted keyword is a P0 tell in AI-design catalogs, and it often fails contrast mid-gradient.
Fix: a solid accent color for the keyword (checked ≥4.5:1 against the real background), or emphasis via the display face's heaviest weight; if brand demands gradient type, confine it to the standalone wordmark.

**108. Serif-italic accent word in a sans headline** (instant)
Tell: one word of the H1 swapped to italic serif — "The *modern* way to ship" — while everything else is Inter/Geist.
Why: a listed model default — emphasis as costume, not hierarchy.
Fix: earn emphasis within the system (weight jump, accent color, or size shift in the same family) or commit the whole headline to the serif; never a one-word font swap.

**109. tracking-tight bold hero reflex** (strong)
Tell: `text-6xl font-extrabold tracking-tight` (or tighter) on every headline, letters nearly touching, applied regardless of typeface.
Why: models learned "big text = negative tracking" from Tailwind examples; crushing tracking on faces not designed for it costs legibility and reads as default styling.
Fix: track display type optically per face and size — some faces need 0 or positive tracking large; set it by eye at final size, and vary heading treatments instead of one global crush.

**110. The text-5xl→7xl centered hero formula** (strong)
Tell: `text-5xl md:text-7xl font-bold text-center` H1, ~2-line max-width, identical on every generated site.
Why: the default LLM hero typography, part of the centered-hero-with-generic-sans pattern.
Fix: keep the scale but break the formula — left-align against an asymmetric layout, a 1–3 word punch headline much larger, or a longer headline set smaller with a hanging indent; any *authored* decision about size vs. length.

**111. The hero subhead formula** (strong)
Tell: `text-lg md:text-xl text-gray-400 max-w-2xl mx-auto text-center` paragraph immediately under the H1, on effectively every generated site.
Why: the exact subhead recipe (size step down, muted gray, centered, ~65ch cap) ships as a unit with the centered hero.
Fix: vary its construction — full-contrast at smaller size, a left-aligned two-column lede, or fold the key clause into the headline; change at least two of color/alignment/width from the default.

**112. Staircase headline with dangling accent word** (mild)
Tell: display headline wrapped into 3–4 short centered lines, the final line a single (often gradient/italic) emphasized word hanging alone.
Why: models don't compose line breaks — the emphasis word lands alone, disconnected.
Fix: hold display heads to 1–2 lines via wording or size; hand-place breaks or use `text-wrap: balance` so emphasis lands mid-phrase, attached to its clause.

## Labels & casing

**113. ALL-CAPS letter-spaced eyebrow** (instant)
Tell: `text-xs uppercase tracking-widest text-indigo-400` micro-label — "FEATURES", "WHY CHOOSE US" — floating above headings.
Why: the tiny uppercase letter-spaced label above an oversized headline is the default AI SaaS hero; it borrows editorial authority without earning it. (Structural repetition angle: #11.)
Fix: delete most eyebrows and let the H2 carry the section; where a wayfinding label genuinely helps, set it sentence-case in the text color, or fold the word into the heading.

**114. Eyebrow tick-rule** (mild)
Tell: a ~30px horizontal hairline or dot preceding the uppercase label — "— PRODUCT".
Why: a decorative tic copied without the editorial system it came from.
Fix: remove the rule; if a marker helps scanning, use a real index (01, 02) tied to actual page structure, in the type's own color.

**115. One label costume for every micro-text** (mild)
Tell: the same letterspaced-uppercase (or mono) treatment on eyebrows, buttons, nav links, table headers, and the footer colophon.
Why: a single treatment used everywhere is template, not voice — the model owns one label style and stamps it.
Fix: differentiate by function — buttons sentence-case medium weight, nav in the text face, table headers small+semibold; tracked caps for at most one label tier.

**116. Title Case On Every Heading** (mild)
Tell: All Headings, Buttons, And Nav Items In Title Case — including mid-page H3s and feature card titles.
Why: models default to American title case uniformly; human systems pick a casing stance, and sentence case now dominates product UI.
Fix: adopt sentence case globally (headings, buttons, labels), capitals only for proper nouns — an instant humanizing pass that also improves scanability.

**117. Whole headings in ALL-CAPS** (mild)
Tell: entire H2s/H3s uppercase with added tracking, sometimes combined with bold and centering.
Why: caps remove word shapes; models use them as a hierarchy crutch.
Fix: sentence case with hierarchy via the scale; uppercase only for ≤2-word functional labels, modest tracking (0.04–0.08em).

**118. All-caps body passages** (mild)
Tell: full sentences or multi-line blocks (manifesto lines, banners) set entirely uppercase.
Why: long uppercase passages destroy word recognition; caps deployed as drama without a length budget.
Fix: reset to sentence case; carry the intended weight via size/weight/color; cap uppercase runs at ~4 words.

**119. Letterspaced all-caps serif wordmark** (mild)
Tell: brand name in a default serif, uppercase, wide-tracked — "L U X E  S T U D I O" — as instant "elegance."
Why: tracking out a default serif treated as instant elegance lands on every generated fashion/real-estate/fine-dining brand.
Fix: design the wordmark as an artifact — deliberate case, custom spacing per letter pair, a face chosen for the brand — or a strong lowercase mark instead of the tracked-caps reflex.

## Micro-typography

**120. Unmanaged line length** (mild)
Tell: body paragraphs running 90–120+ characters full-width on desktop, or prose jammed into uniform max-w-7xl containers.
Why: >80ch lines are a listed legibility failure of generated pages — the model styles the container, not the reading experience.
Fix: cap running text at 65–75ch (`max-w-[65ch]` / `max-w-prose`) independent of the section container; widen only data tables and imagery.

**121. Default leading at display size** (mild)
Tell: hero headlines at 1.5 line-height (gappy) or body copy at 1.2 (cramped) — the framework default applied at every size.
Why: regular weight, default line-height, default letter-spacing on big headlines is a core unmodified-defaults tell.
Fix: tune leading per tier — display 0.95–1.1, subheads ~1.2–1.3, body 1.5–1.7; check descender/ascender collisions at final size rather than trusting the default.

## VOCAB — greppable signals for this file

- Fonts: `Inter` `Manrope` `Plus Jakarta Sans` `Space Grotesk` `Poppins` `Sora` `Syne` `Outfit` `DM Sans` `Figtree` `Instrument Serif` `Fraunces` `Playfair Display` `Cormorant` `Bricolage Grotesque` `Hanken Grotesk` `Schibsted Grotesk` `Onest` `Geist` `GeistSans` `GeistMono` `JetBrains Mono` `IBM Plex Mono` `fonts.googleapis.com` `next/font/google`
- Classes: `tracking-tight(er)` `tracking-widest` `uppercase` `text-5xl|6xl|7xl` `font-bold` `font-extrabold` `text-center` `max-w-2xl mx-auto` `bg-clip-text` `text-transparent` `italic` `font-serif` `leading-tight`
- Checks: count distinct font families (1 = tell) · count distinct weights (2 = tell) · measure H1/H2 size ratio (<1.25 = flat scale) · body line length in ch · casing consistency across headings/buttons

Sources: developersdigest.tech Show-HN audit · pols.dev/slop · impeccable.style/slop · bruvora.com "Stop AI slop typography" · github.com/funboy322/avoid-ai-design
