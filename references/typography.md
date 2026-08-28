# Catalog 3/7: Typography (#94–121)

Font choices, pairing, hierarchy, headline styling, labels, casing, micro-typography. Severity: **instant** / **strong** / **mild** (see SKILL.md).

## Font choice

**94. Inter as the only typeface** (instant)
Tell: `font-family: Inter` (or Inter → system-ui) for headline, body, buttons, and labels alike.
Why: Inter became the Helvetica of the LLM era. It is the most-used face in the training data, and it is the mark readers spot first on a generated site.
Fix: keep Inter for UI text if you need it, but self-host a characterful display face for headlines (Fontshare's Clash Display, Cabinet Grotesk, or Satoshi; foundry faces like Söhne, GT Sectra, Tiempos). A neutral grotesque cannot carry the identity alone.

**95. The trendy-font shelf** (strong)
Tell: Space Grotesk, Sora, Syne, Outfit, Manrope, Plus Jakarta Sans, DM Sans, Figtree, the Google-Fonts "modern startup" rotation, used straight.
Why: models name these faces when you tell them "not Inter." They appear in ~15.8% of audited AI pages and now co-signal generated design.
Fix: choose type from the brief. Browse past Google's top 50 (Fontshare, Klim, Grilli, ABC Dinamo, OH no Type), set your real H1 in the candidate, then ask whether that screenshot could belong to any other startup.

**96. Poppins geometric-rounded default** (strong)
Tell: Poppins on the headings and body of "approachable" sites, with its circular O's and wide friendly geometry.
Why: freelancers reached for Poppins long before the AI era and the models absorbed it from them. Set it against pastel gradients and every reader sees a template.
Fix: if you want geometric warmth, use a face built for text with some character (General Sans, Gabarito in small doses, or a licensed geometric). Never set long body copy in a display geometric.

**97. Untouched Geist outside Vercel** (strong)
Tell: `GeistSans`/`GeistMono` from `next/font` carrying the whole identity of a non-Vercel product.
Why: Vercel commissioned Geist as its own brand voice, so an unmodified Geist page looks like a Next.js AI template scaffold.
Fix: treat Geist as scaffolding. Swap the display layer for a face chosen for this brand, or re-tune the weights and tracking and pair it against a contrasting display serif or slab.

**98. The "not-Inter" escape hatch** (mild)
Tell: Bricolage Grotesque, Schibsted Grotesk, Hanken Grotesk, or Onest picked as the "distinctive" alternative, straight off the same Google shortlist.
Why: models reach for the second-ring Google faces whenever a prompt says "avoid Inter," so in aggregate these now pattern-match too.
Fix: source the display face from an actual foundry or licensed catalog, self-host it, and customize the deployment (weight axis, tracking, optical size) so even a known face arrives set in a non-default way.

**99. Fraunces/Playfair editorial cosplay** (mild)
Tell: Fraunces, Playfair Display, or Cormorant headline over a cream background with brown ink, often with gold accents. The "artisanal" preset.
Why: designers reach for these display serifs whenever something has to feel expensive, and the shortcut shows.
Fix: if editorial is right, use a serif with a different provenance (Newsreader, GT Sectra, Tiempos Headline, Gambarino) tuned through its optical-size axes, and pair it with a non-obvious text face in place of the cream-and-gold kit.

**100. Instrument Serif oversized italic hero** (instant)
Tell: huge Instrument Serif display headline, italic in most cases, on an otherwise sans page.
Why: the 2025 generated-landing signature. One catalog puts it this way: "oversized italic serif as primary hero has become the universal AI-startup hero."
Fix: set the display in roman with tracking you chose by eye, or pick a different characterful display face. Keep italics for emphasis inside running text.

## Pairing & hierarchy

**101. No pairing, headline is body scaled up** (strong)
Tell: one neutral sans at one weight doing every job, with the H1 set as body text at 64px.
Why: a single neutral sans covering both headings and body is the clearest typography tell in generated work.
Fix: build a two-voice system: an expressive display face for H1 and H2, a restrained text face for everything else. If one family has to stay, exploit its extremes (Black against Book, condensed against normal, optical sizes).

**102. The canned pairing** (strong)
Tell: recurring combos such as Space Grotesk heads with Inter body, or Instrument Serif accents with Geist body, recycled across unrelated generated sites.
Why: LLM pairing suggestions converge on the same few duos, so the pairing itself became a fingerprint.
Fix: pair by contrast logic (era, width, construction) with at least one face from a non-default source: a sharp Dutch serif against a plain grotesk, or a mono display against a humanist text face. Check that your combo does not appear in the font-pairing listicles.

**103. Flat type scale** (strong)
Tell: h2/h3/body sizes clustered within a few px (20/18/16), nothing standing out as most important, hierarchy carried by gray shades alone.
Why: models emit "safe" incremental scales, and the missing jumps are a core generated-typography tell.
Fix: rebuild on a ≥1.25 ratio with one oversized display step. Each level should differ by at least two of size, weight, and spacing, so the reading order survives a squint test.

**104. Two-weight universe** (mild)
Tell: the whole site set in 700 and 400, with no medium, semibold, or light display weight, despite a 9-weight variable font in the build.
Why: default Tailwind classes drive the weight choice, so generated pages ignore the range of the family they loaded.
Fix: assign weights by role (display 650–800 tuned to the face, UI labels 500–550, body 400–450) along the variable axis. Big type wants less weight than models give it.

**105. Two-tone text hierarchy (white + gray-400)** (strong)
Tell: every heading in pure white, every other string in `text-gray-400`/`text-muted-foreground`, the whole hierarchy carried by one gray.
Why: heading-white with body-muted is the shadcn and LLM default pair. Designed systems mix weight, size, spacing, and more than two ink values.
Fix: add third and fourth ink steps (95%/78%/60% L, say) mapped to real priority levels. Let some secondary text keep full contrast at a smaller size instead of graying out.

**106. Monospace as house voice** (strong)
Tell: JetBrains Mono, IBM Plex Mono, or Geist Mono on eyebrows, captions, dates, copyright lines, and nav of a product that contains no code.
Why: models reach for mono outside data contexts to signal "technical," the same way they reach for purple to signal "premium."
Fix: reserve mono for real data (code, timestamps, IDs, prices) with tabular figures. Set editorial micro-text in the text face, one size and weight step down.

## Headline styling

**107. Gradient keyword via bg-clip-text** (instant)
Tell: a single word of the hero headline set in `bg-clip-text text-transparent bg-gradient-to-r from-indigo-500 to-purple-600`.
Why: AI-design catalogs rank the gradient-highlighted keyword as a P0 tell, and it often fails contrast partway through the gradient.
Fix: use a solid accent color for the keyword, checked at ≥4.5:1 against the real background, or carry the emphasis with the display face's heaviest weight. If the brand demands gradient type, confine it to the standalone wordmark.

**108. Serif-italic accent word in a sans headline** (instant)
Tell: one word of the H1 swapped to italic serif, as in "The *modern* way to ship", while everything else stays Inter or Geist.
Why: a listed model default. The swap dresses the word up without giving it a place in the hierarchy.
Fix: earn the emphasis inside the system (a weight jump, an accent color, a size shift within the same family), or commit the whole headline to the serif. Skip the one-word font swap.

**109. tracking-tight bold hero reflex** (strong)
Tell: `text-6xl font-extrabold tracking-tight`, or tighter, on every headline, letters almost touching, whatever the typeface.
Why: models learned "big text = negative tracking" from Tailwind examples. Crushing the tracking on a face never drawn for it costs legibility and looks like default styling.
Fix: track display type by eye, per face and per size. Some faces want 0 or positive tracking at large sizes. Vary the heading treatments instead of applying one global crush.

**110. The text-5xl→7xl centered hero formula** (strong)
Tell: `text-5xl md:text-7xl font-bold text-center` H1, a two-line max-width, identical from one generated site to the next.
Why: this is the default LLM hero typography, shipped as part of the centered-hero-with-generic-sans pattern.
Fix: keep the scale and break the formula. Left-align it against an asymmetric layout, cut the headline to 1–3 words and set it much larger, or run a longer headline smaller with a hanging indent. Any *authored* decision about size against length will do.

**111. The hero subhead formula** (strong)
Tell: `text-lg md:text-xl text-gray-400 max-w-2xl mx-auto text-center` paragraph sitting under the H1 on close to every generated site.
Why: the recipe (one size step down, muted gray, centered, ~65ch cap) ships as a unit with the centered hero.
Fix: vary the construction. Try full contrast at a smaller size, a left-aligned two-column lede, or fold the key clause into the headline. Change at least two of color, alignment, and width from the default.

**112. Staircase headline with dangling accent word** (mild)
Tell: display headline wrapped into 3–4 short centered lines, the last line a single emphasized word (gradient or italic) hanging alone.
Why: models do not compose line breaks, so the emphasis word lands by itself, cut off from its clause.
Fix: hold display heads to one or two lines through wording or size. Place the breaks by hand, or use `text-wrap: balance` so the emphasis lands mid-phrase with its clause.

## Labels & casing

**113. ALL-CAPS letter-spaced eyebrow** (instant)
Tell: `text-xs uppercase tracking-widest text-indigo-400` micro-label such as "FEATURES" or "WHY CHOOSE US" floating above the heading.
Why: the tiny tracked-caps label over an oversized headline is the default AI SaaS hero, and it borrows an editorial authority the page has not earned. (Structural repetition angle: #11.)
Fix: delete most eyebrows and let the H2 carry the section. Where a wayfinding label helps, set it in sentence case in the text color, or fold the word into the heading.

**114. Eyebrow tick-rule** (mild)
Tell: a ~30px horizontal hairline or dot in front of the uppercase label, as in "— PRODUCT".
Why: a decorative tic copied over without the editorial system it came from.
Fix: remove the rule. If a marker helps people scan, use a real index (01, 02) tied to the page structure, in the type's own color.

**115. One label costume for every micro-text** (mild)
Tell: the same letterspaced-uppercase or mono treatment on eyebrows, buttons, nav links, table headers, and the footer colophon.
Why: the model owns one label style and stamps it everywhere, which is how a template behaves.
Fix: differentiate by function: buttons in sentence case at medium weight, nav in the text face, table headers small and semibold. Keep tracked caps for one label tier at most.

**116. Title Case On Every Heading** (mild)
Tell: All Headings, Buttons, And Nav Items In Title Case, down to mid-page H3s and feature card titles.
Why: models apply American title case across the board. Human systems pick a casing stance, and sentence case now dominates product UI.
Fix: adopt sentence case throughout (headings, buttons, labels) and capitalize proper nouns. It is the fastest humanizing pass you can run, and it improves scanability.

**117. Whole headings in ALL-CAPS** (mild)
Tell: entire H2s and H3s in uppercase with added tracking, sometimes bold and centered on top of that.
Why: caps erase word shapes, and models lean on them as a hierarchy crutch.
Fix: use sentence case and build the hierarchy in the scale. Save uppercase for functional labels of two words or fewer, with modest tracking (0.04–0.08em).

**118. All-caps body passages** (mild)
Tell: full sentences or multi-line blocks (manifesto lines, banners) set in uppercase throughout.
Why: long uppercase passages destroy word recognition, and the writer reached for drama with no length budget.
Fix: reset to sentence case and carry the intended weight through size, weight, and color. Cap any uppercase run at about four words.

**119. Letterspaced all-caps serif wordmark** (mild)
Tell: brand name in a default serif, uppercase, wide-tracked, as in "L U X E  S T U D I O".
Why: designers treat a tracked-out default serif as shorthand for elegance, and it now lands on every generated fashion, real-estate, and fine-dining brand.
Fix: design the wordmark as an artifact, with a chosen case, custom spacing per letter pair, and a face picked for this brand. A strong lowercase mark also beats the tracked-caps reflex.

## Micro-typography

**120. Unmanaged line length** (mild)
Tell: body paragraphs running 90–120+ characters full-width on desktop, or prose poured into uniform max-w-7xl containers.
Why: lines over 80ch are a listed legibility failure of generated pages, because the model styled the container and left the reading experience alone.
Fix: cap running text at 65–75ch (`max-w-[65ch]` / `max-w-prose`) independent of the section container. Widen data tables and imagery on their own.

**121. Default leading at display size** (mild)
Tell: hero headlines at 1.5 line-height (gappy) or body copy at 1.2 (cramped), the framework default applied at every size.
Why: regular weight with default line-height and default letter-spacing on big headlines is a core unmodified-defaults tell.
Fix: tune leading per tier (display 0.95–1.1, subheads ~1.2–1.3, body 1.5–1.7) and check ascender and descender collisions at the final size.

## VOCAB: greppable signals for this file

- Fonts: `Inter` `Manrope` `Plus Jakarta Sans` `Space Grotesk` `Poppins` `Sora` `Syne` `Outfit` `DM Sans` `Figtree` `Instrument Serif` `Fraunces` `Playfair Display` `Cormorant` `Bricolage Grotesque` `Hanken Grotesk` `Schibsted Grotesk` `Onest` `Geist` `GeistSans` `GeistMono` `JetBrains Mono` `IBM Plex Mono` `fonts.googleapis.com` `next/font/google`
- Classes: `tracking-tight(er)` `tracking-widest` `uppercase` `text-5xl|6xl|7xl` `font-bold` `font-extrabold` `text-center` `max-w-2xl mx-auto` `bg-clip-text` `text-transparent` `italic` `font-serif` `leading-tight`
- Checks: count distinct font families (1 = tell) · count distinct weights (2 = tell) · measure H1/H2 size ratio (<1.25 = flat scale) · body line length in ch · casing consistency across headings/buttons

Sources: developersdigest.tech Show-HN audit · pols.dev/slop · impeccable.style/slop · bruvora.com "Stop AI slop typography" · github.com/funboy322/avoid-ai-design
