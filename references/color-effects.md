# Catalog 2/7 — Color, gradients & surface effects (#64–93)

Palettes, gradients, glow, glass, backgrounds, borders, radius, shadows, theme defaults. Severity: **instant** / **strong** / **mild** (see SKILL.md).

## Palette

**64. Untouched indigo/violet accent** (instant)
Tell: primary buttons, links, and focus rings in stock Tailwind `indigo-500`/`violet-500`/`purple-600` (#6366f1, #8b5cf6, #a855f7) with zero hue customization.
Why: Tailwind UI's indigo default saturated the training corpus, so every LLM reaches for it — the single most-cited "AI made this" color.
Fix: derive the accent from the product's actual domain (fintech → deep ledger green, audio → VU-meter amber, legal → oxblood), define it as a custom oklch token with hand-tuned hover/active steps, and verify it sits visibly far from #6366f1.

**65. Dark-by-default page on #0a0a0a** (instant)
Tell: permanent dark theme (`bg-zinc-950`, #0a0a0a/#09090b) with neon accent, no light option, regardless of audience.
Why: an audit of 1,590 Show HN pages found permanent dark theme the #1 single tell (34%); dark + purple accents is the default aesthetic LLMs reach for.
Fix: choose the mode the audience actually reads in; if dark is right, build custom dark tokens — warm or green-black base instead of neutral zinc, elevation via lighter surface steps (+4–6% L per level) rather than glow.

**66. Cyan-on-dark hacker glow palette** (strong)
Tell: near-black ground with electric cyan/teal (#22d3ee) glows, terminal-green accents, glowing keylines — the "dev-tool" skin.
Why: cyan-on-dark is cited alongside purple gradients as the most recognizable tell of generated UIs.
Fix: if the product is genuinely technical, ground the palette in a real reference (oscilloscope amber, print-on-matte, an IDE theme you own) and cap luminous accents to data/status only, never decoration.

**67. Oversaturated accent vibrating on near-black** (strong)
Tell: 100%-saturation purple/cyan text and buttons on #0a0a0a causing halation/vibration, especially thin text in accent color.
Why: models pair maximum-chroma accents with maximum-dark grounds because both are "dramatic" defaults; designed dark UIs desaturate.
Fix: drop accent chroma 15–25% and raise lightness slightly for dark mode (Material-style tonal shift); never set body-size text in a saturated hue on near-black.

**68. Barely-passing gray body text on dark** (strong)
Tell: `text-gray-500`/`text-slate-400` body copy on `bg-zinc-950`, hovering at or below 4.5:1.
Why: generated dark themes routinely ship body text that fails WCAG AA — mid-gray-on-dark is the default muted-text token.
Fix: set dark-mode body at gray-200/#d4d4d8+ (aim toward 7:1), reserve mid-grays for genuinely tertiary metadata at large sizes, and audit every muted token against the real background.

**69. The slop gray (#f3f4f6)** (mild)
Tell: cool UI-kit gray (#f3f4f6–#e7ecf3, `bg-gray-100`) as footer band, divider fill, and card background across the page.
Why: the untouched Tailwind/Figma neutral — signals nobody chose a neutral palette.
Fix: mix custom neutrals from the brand hue (2–4% chroma of the accent's hue in oklch) so grays feel warm or cool on purpose; one consistent neutral ramp instead of framework grays.

**70. Cream/beige "tasteful" default** (mild)
Tell: warm cream/bone page (#faf7f2-ish) + serif headline + brown-black text — the "premium editorial" preset.
Why: the cream-editorial look became the LLM's second default once purple got called out; it is now itself a recognized generated aesthetic.
Fix: keep warmth but earn it — pick a specific off-white tied to the brand (paper, sand, plaster), add one non-obvious secondary (ink blue, moss), and carry a distinctive display face rather than the stock serif-on-cream combo.

**71. Evenly-weighted multi-accent palette** (mild)
Tell: 4+ hues (indigo, cyan, pink, emerald) distributed at similar visual weight across icons, tags, and section accents with no dominant.
Why: models decorate each section with "a" color rather than building hierarchy — a timid, averaged palette.
Fix: enforce 60/30/10 — one dominant neutral field, one secondary, one sharp accent; recolor section decorations to tints of the single accent.

## Gradients

**72. Blue-to-purple-to-pink hero gradient** (instant)
Tell: `bg-gradient-to-r from-blue-500 via-purple-500 to-pink-500` (or indigo→purple→fuchsia) flooding the hero, CTA, or section backgrounds.
Why: cross-hue cool gradients are the statistical average of SaaS training data; audits found gradient backgrounds on ~27% of AI-fingerprinted pages.
Fix: a single-hue tonal gradient (two lightness steps of one brand hue) or a solid surface plus subtle grain; if two hues are needed, pick neighbors on the wheel anchored to the brand hue.

**73. The 135° stock gradient** (instant)
Tell: `linear-gradient(135deg, #667eea 0%, #764ba2 100%)` — or any 135deg periwinkle→grape — on buttons, heroes, auth screens.
Why: this exact pair is the most-copied CSS gradient snippet on the internet, so models emit it verbatim.
Fix: if a diagonal gradient stays, rebuild from two brand-derived stops in oklch, change the angle to match a real light direction, and never reuse it on more than one element role.

**74. Mesh/aurora blob background** (strong)
Tell: 3–4 overlapping soft radial-gradient blobs (violet, cyan, pink) at 40–60% opacity, blurred and blend-moded, melting into pastel haze behind the hero.
Why: the Stripe-derived mesh hero was cloned by every template, then memorized by every model.
Fix: one deliberate surface — flat color with 2–3% noise, a tight two-stop tonal wash, or an actual rendered scene; if a mesh must stay, constrain it to brand hues and pin it inside one contained shape, not full-bleed. (Animated version: #171.)

**75. Pastel candy gradient wash** (mild)
Tell: butter-yellow→peach→strawberry-milk or mint→lavender full-page washes with soft blur.
Why: the "sherbet aurora" is the LLM's friendly-mode default, now on every generated consumer landing page.
Fix: pick one pastel as a true surface color, pair it with an unexpected dark ink (deep green, aubergine) for structure; kill multi-hue washes; add grain to any remaining transition.

**76. Banded gradient transitions** (mild)
Tell: visible stepping/banding across large background gradients, especially dark purple→black.
Why: models emit sRGB two-stop gradients over huge areas; the banding marks an untouched machine output no designer reviewed.
Fix: interpolate in oklch, add intermediate stops, or overlay 2% noise dithering so the transition reads as continuous material.

## Glow & atmosphere

**77. Floating blurred glow orbs** (instant)
Tell: absolutely-positioned `rounded-full bg-purple-500/30 blur-3xl` divs parked behind the hero corners of a dark page.
Why: the decorative radial blob bleeding from a corner is a canned generated-UI atmosphere shortcut with no compositional purpose.
Fix: delete the orbs; build atmosphere from one authored element — a real image, a fine grain layer, or a single directional light wash with specific falloff and an unexpected (non-purple) temperature.

**78. Colored glow box-shadows** (instant)
Tell: `shadow-lg shadow-purple-500/50` or `box-shadow: 0 0 40px rgba(139,92,246,.5)` haloing buttons, cards, screenshots.
Why: neon under-glow is the LLM's default signifier of "premium tech"; real elevation systems use neutral, directional shadows.
Fix: a tight, low-offset neutral shadow (`0 1px 2px` + `0 8px 24px` at 8–12% opacity, tinted toward the surface color) implying one light source; reserve colored light for one hero moment, if anywhere.

**79. Radial spotlight haze behind headings** (mild)
Tell: faint accent-colored radial haze centered behind each section heading or icon row, like a stage spotlight.
Why: a listed generated-UI shortcut — light without a source or subject.
Fix: remove; if depth is wanted, light the composition from one consistent direction with a specific falloff, or let the surface stand alone.

**80. Glow clipped by section overflow** (mild)
Tell: a soft radial glow sliced flat by `overflow:hidden` at a section boundary, ending in a hard horizontal line.
Why: half-finished effect assembly — the model added the glow and never looked at the seam.
Fix: let the glow live fully inside its section (scale down, reposition) or extend it across the boundary; check every soft element's edges at full-page zoom.

**81. Dot-grid background with masked glow** (strong)
Tell: faint `radial-gradient(circle, #333 1px, transparent 1px)` dot matrix across the hero, fading via `mask-image`, often with a glow spot behind the headline.
Why: the dotted "engineering canvas" backdrop is a stock Tailwind-snippet atmosphere every generator reuses.
Fix: delete unless the surface genuinely represents a canvas/map; replace with a plain field plus grain, or make the grid specific — real ruler ticks, sparse registration marks, or a grid aligned to the actual layout columns.

**82. Blueprint line-grid backdrop** (mild)
Tell: full-bleed graph-paper hairlines behind sections, unconnected to any measurable content.
Why: the blueprint look only earns its place when sparing and specific; as wallpaper it reads as generated filler.
Fix: constrain the grid to one section where it annotates something real (diagram, spec sheet), align its module to the layout grid, drop it everywhere else.

**83. Noise overlay sitting on content** (mild)
Tell: an SVG `feTurbulence`/PNG grain layer at visible opacity laid over the entire viewport, including text and UI.
Why: "premium grain" is a memorized trick; applied above content it fights legibility and reads as a filter, not a material.
Fix: grain behind content only, at 2–4% opacity on large flat fills and gradients (where it kills banding); it should be felt, never seen.

## Surfaces, borders, radius & shadow

**84. Reflexive glassmorphism** (strong)
Tell: `backdrop-blur-md bg-white/10 border border-white/20` cards and navs floating over nothing worth refracting.
Why: frosted-glass cards appear on ~17% of AI-fingerprinted pages, applied as decoration rather than to solve layering.
Fix: keep blur only where content genuinely scrolls beneath (sticky nav); elsewhere use solid surfaces one tonal step off the background. If glass stays: give it a real backdrop, an inner top-edge highlight, and check for blur banding.

**85. 1px white/10 borders on every dark card** (strong)
Tell: every dark-mode panel wrapped in `border border-white/10` (or `border-slate-800`) as the universal card treatment.
Why: shadcn/template default card styling, repeated identically across thousands of generated UIs.
Fix: self-colored borders (the surface's own color nudged one step lighter) plus a slight tonal fill difference, or drop borders and separate cards purely by surface-value steps; vary treatment by component role.

**86. Static gradient border rings** (strong)
Tell: cards or CTAs ringed by an indigo→pink gradient stroke via the double-background border trick.
Why: a copy-pasted MagicUI/Aceternity signature that models emit unprompted. (Animated orbiting version: #173.)
Fix: a 1px border in the accent at 30–40% opacity, or a solid 2px accent on exactly one priority element; if a gradient stroke survives, keep it inside a small contained mark (logo, badge), never on layout containers.

**87. Uniform rounded-xl/2xl on everything** (strong)
Tell: identical 12–16px radius — or blob-level 24px+ — on cards, inputs, buttons, images, and sections alike.
Why: one radius token applied indiscriminately is the "16px border radius everywhere" fingerprint of generated layouts.
Fix: a radius hierarchy by role (2–4px inputs, 8–12px cards, full-pill only for tags/buttons — or commit to 0px sharp as a brand stance); never round a container more than its parent.

**88. Default soft shadow on every card** (mild)
Tell: `shadow-md`/`shadow-lg` bloomed symmetrically on all sides of every white card, added by reflex.
Why: symmetric all-around shadows ignore light direction — the default stack models paste with every card.
Fix: reserve shadows for genuinely floating elements (menus, modals); give resting cards a border or tonal fill instead; when shadowing, layer directional values (small tight + large soft, downward offset).

**89. Hairline border + wide diffuse shadow together** (mild)
Tell: cards carrying both a 1px light border and a large soft drop shadow simultaneously.
Why: the model hedging between two card recipes — commit to one: defined edge or soft elevation.
Fix: pick the edge system (border, flat) or the elevation system (shadow, borderless) per surface level and apply consistently.

## Theme & component color patterns

**90. Untouched shadcn zinc theme** (strong)
Tell: stock shadcn look — zinc/slate neutrals, `--radius: 0.5rem`, muted indigo or plain-black primary, `text-muted-foreground` grays, default Card/Button styling.
Why: ~23.5% of audited AI pages ship shadcn defaults verbatim; apps blend into the endless sea of identical dashboards.
Fix: re-theme the tokens once and everything updates — swap the neutral ramp (warm gray or green-gray instead of zinc), set `--radius` to a deliberate 0/0.25/1rem, replace primary with a saturated brand accent, add one signature token (grain, shadow style, easing) the kit doesn't ship.

**91. Colored left-border accent card** (instant)
Tell: `border-l-4 border-indigo-500` (or a 3–4px top stripe, sometimes gradient) on feature/testimonial cards, clashing with rounded corners.
Why: "colored left borders are almost as reliable a sign of AI-generated design as em-dashes."
Fix: remove the stripe; differentiate cards via tonal background, heading weight, or scale; if a category color is needed, use a small solid dot or tag inside the card, not an edge bar.

**92. Gradient pre-footer CTA slab** (strong)
Tell: full-width `rounded-3xl` box flooded with the same blue→purple gradient, centered white headline + two buttons, just above the footer.
Why: the gradient CTA banner is the canonical closing block of every generated SaaS template. (Structural angle: #22.)
Fix: keep the conversion block but change its material — solid brand color with grain, an inverted dark-on-light panel, or a full-bleed product/photographic background; left-align inside it and reuse the page's real accent.

**93. "Linear glow" screenshot frame** (strong)
Tell: dark hero with the product screenshot wrapped in a glowing gradient rim, blurred color bloom underneath, often perspective-tilted.
Why: Linear's 2021 hero was cloned into every template and model; the exact glow-rim treatment now reads as costume. (Chrome-frame angle: #4.)
Fix: present the product honestly — flat screenshot, 1px surface border, correct-direction shadow, or an actual working embed; spend the effect budget on the screenshot's content being real and dense.

## VOCAB — greppable signals for this file

- Gradient/color classes: `from-indigo-500` `from-purple-500` `from-violet-500` `via-purple-500` `to-pink-500` `to-purple-600` `to-fuchsia-500` `bg-gradient-to-r` `bg-gradient-to-br` `bg-indigo-500|600` `bg-violet-600` `text-indigo-400|600` `ring-indigo-500` `bg-zinc-950` `bg-gray-950` `bg-slate-900` `bg-gray-50|100` `text-gray-400|500` `text-slate-400` `text-muted-foreground`
- Effects: `backdrop-blur(-md)` `bg-white/10` `bg-white/5` `border-white/10|20` `blur-3xl` `blur-2xl` `shadow-purple-500` `shadow-indigo-500/50` `shadow-lg` `shadow-xl` `rounded-xl|2xl|3xl` `border-l-4` `border-t-4` `mask-image` `mix-blend-multiply` `feTurbulence`
- CSS values/hex: `linear-gradient(135deg` `#6366f1` `#8b5cf6` `#a855f7` `#7c3aed` `#4f46e5` `#667eea` `#764ba2` `#ec4899` `#d946ef` `#22d3ee` `#0a0a0a` `#09090b` `#f3f4f6` `rgba(139, 92, 246` `rgba(99, 102, 241` `box-shadow: 0 0`
- shadcn tokens: `--radius: 0.5rem` `baseColor: "zinc"|"slate"` `bg-background` `text-foreground` `bg-card` `border-border` `bg-primary`

Sources: dev.to "Why every AI-built website looks the same — blame Tailwind's indigo-500" · github.com/funboy322/avoid-ai-design · pols.dev/slop · impeccable.style/slop · developersdigest.tech Show-HN audit · freedesignmd.com "Why shadcn looks generic"
