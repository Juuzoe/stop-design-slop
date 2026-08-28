# Catalog 2/7: Color, gradients & surface effects (#64–93)

Palettes, gradients, glow, glass, backgrounds, borders, radius, shadows, theme defaults. Severity: **instant** / **strong** / **mild** (see SKILL.md).

## Palette

**64. Untouched indigo/violet accent** (instant)
Tell: primary buttons, links, and focus rings in stock Tailwind `indigo-500`/`violet-500`/`purple-600` (#6366f1, #8b5cf6, #a855f7) with zero hue customization.
Why: Tailwind UI's indigo default saturated the training corpus, so every LLM reaches for it. Reviewers name this color more than any other when they flag a page as "AI made this."
Fix: derive the accent from the product's domain (fintech → deep ledger green, audio → VU-meter amber, legal → oxblood), define it as a custom oklch token with hand-tuned hover/active steps, then check that it sits far from #6366f1.

**65. Dark-by-default page on #0a0a0a** (instant)
Tell: permanent dark theme (`bg-zinc-950`, #0a0a0a/#09090b) with neon accent, no light option, regardless of audience.
Why: an audit of 1,590 Show HN pages found permanent dark theme the #1 single tell (34%), and dark plus purple accents is the aesthetic LLMs fall back on.
Fix: choose the mode your audience reads in. If dark is right, build custom dark tokens: a warm or green-black base in place of neutral zinc, and elevation through lighter surface steps (+4–6% L per level) rather than glow.

**66. Cyan-on-dark hacker glow palette** (strong)
Tell: near-black ground, electric cyan/teal (#22d3ee) glows on keylines, terminal-green accents. The "dev-tool" skin.
Why: writers cite cyan-on-dark alongside purple gradients as the most recognizable tell of a generated UI.
Fix: if the product is technical, ground the palette in a real reference (oscilloscope amber, print-on-matte, an IDE theme you own) and cap luminous accents to data and status, never decoration.

**67. Oversaturated accent vibrating on near-black** (strong)
Tell: 100%-saturation purple/cyan text and buttons on #0a0a0a causing halation, worst on thin text in the accent color.
Why: models pair maximum-chroma accents with maximum-dark grounds because both read as dramatic defaults. Designers desaturate dark UIs.
Fix: drop accent chroma 15–25% and raise lightness a step for dark mode (the Material-style tonal shift). Never set body-size text in a saturated hue on near-black.

**68. Barely-passing gray body text on dark** (strong)
Tell: `text-gray-500`/`text-slate-400` body copy on `bg-zinc-950`, sitting at or below 4.5:1.
Why: generated dark themes ship body text that fails WCAG AA, because mid-gray-on-dark is the default muted-text token.
Fix: set dark-mode body at gray-200/#d4d4d8+ (aim toward 7:1), reserve mid-grays for tertiary metadata at large sizes, and audit every muted token against the real background.

**69. The slop gray (#f3f4f6)** (mild)
Tell: cool UI-kit gray (#f3f4f6–#e7ecf3, `bg-gray-100`) as footer band, divider fill, and card background across the page.
Why: nobody picked this neutral. The builder shipped the Tailwind/Figma default untouched.
Fix: mix custom neutrals from the brand hue (2–4% chroma of the accent's hue in oklch) so grays run warm or cool on purpose, and use one consistent neutral ramp in place of framework grays.

**70. Cream/beige "tasteful" default** (mild)
Tell: warm cream/bone page (#faf7f2-ish) with serif headline and brown-black text: the "premium editorial" preset.
Why: the cream-editorial look became the LLM's second default once people called out purple, and reviewers now flag it as its own generated aesthetic.
Fix: keep the warmth but earn it. Pick a specific off-white tied to the brand (paper, sand, plaster), add one non-obvious secondary (ink blue, moss), and carry a distinctive display face in place of the stock serif-on-cream combo.

**71. Evenly-weighted multi-accent palette** (mild)
Tell: 4+ hues (indigo, cyan, pink, emerald) spread at similar visual weight across icons, tags, and section accents with no dominant.
Why: models give each section "a" color rather than building hierarchy, so the palette averages out and nothing leads.
Fix: enforce 60/30/10: one dominant neutral field, one secondary, one sharp accent. Recolor section decorations to tints of that single accent.

## Gradients

**72. Blue-to-purple-to-pink hero gradient** (instant)
Tell: `bg-gradient-to-r from-blue-500 via-purple-500 to-pink-500` (or indigo→purple→fuchsia) flooding the hero, CTA, or section backgrounds.
Why: cross-hue cool gradients are the statistical average of SaaS training data, and audits found gradient backgrounds on ~27% of AI-fingerprinted pages.
Fix: use a single-hue tonal gradient (two lightness steps of one brand hue), or a solid surface plus subtle grain. If you need two hues, pick neighbors on the wheel anchored to the brand hue.

**73. The 135° stock gradient** (instant)
Tell: `linear-gradient(135deg, #667eea 0%, #764ba2 100%)`, or any 135deg periwinkle→grape, on buttons, heroes, and auth screens.
Why: this exact pair is the most-copied CSS gradient snippet on the internet, so models emit it verbatim.
Fix: if a diagonal gradient stays, rebuild it from two brand-derived stops in oklch, change the angle to match a real light direction, and use it on a single element role.

**74. Mesh/aurora blob background** (strong)
Tell: 3–4 overlapping soft radial-gradient blobs (violet, cyan, pink) at 40–60% opacity, blurred and blend-moded into a pastel haze behind the hero.
Why: template authors cloned the Stripe-derived mesh hero everywhere, and models memorized it from them.
Fix: build one deliberate surface: flat color with 2–3% noise, a tight two-stop tonal wash, or a rendered scene. If a mesh must stay, constrain it to brand hues and pin it inside one contained shape rather than full-bleed. (Animated version: #171.)

**75. Pastel candy gradient wash** (mild)
Tell: butter-yellow→peach→strawberry-milk or mint→lavender full-page washes under a soft blur.
Why: the "sherbet aurora" is the LLM's friendly-mode default, and it now covers generated consumer landing pages.
Fix: pick one pastel as a true surface color and pair it with an unexpected dark ink (deep green, aubergine) for structure. Kill the multi-hue washes, and add grain to any transition you keep.

**76. Banded gradient transitions** (mild)
Tell: visible stepping across large background gradients, worst on dark purple→black.
Why: models emit sRGB two-stop gradients over huge areas, and nobody reviewed the output before it shipped.
Fix: interpolate in oklch, add intermediate stops, or overlay 2% noise dithering so the transition looks like continuous material.

## Glow & atmosphere

**77. Floating blurred glow orbs** (instant)
Tell: `rounded-full bg-purple-500/30 blur-3xl` divs with `position:absolute`, parked behind the hero corners of a dark page.
Why: models bleed a decorative radial blob in from the corner as canned atmosphere, and it does no compositional work.
Fix: delete the orbs. Build atmosphere from one authored element: a real image, or a single directional light wash with specific falloff and a non-purple temperature.

**78. Colored glow box-shadows** (instant)
Tell: `shadow-lg shadow-purple-500/50` or `box-shadow: 0 0 40px rgba(139,92,246,.5)` haloing buttons, cards, and screenshots.
Why: models use neon under-glow as their default signifier of "premium tech." Real elevation systems use neutral, directional shadows.
Fix: use a tight, low-offset neutral shadow (`0 1px 2px` plus `0 8px 24px` at 8–12% opacity, tinted toward the surface color) that implies one light source. Reserve colored light for a single hero moment, if you use it at all.

**79. Radial spotlight haze behind headings** (mild)
Tell: faint accent-colored radial haze centered behind each section heading or icon row, like a stage spotlight.
Why: catalogs list this one as a generated-UI shortcut: light with no source and no subject.
Fix: remove it. If you want depth, light the composition from one consistent direction with a specific falloff, or leave the surface alone.

**80. Glow clipped by section overflow** (mild)
Tell: a soft radial glow sliced flat by `overflow:hidden` at a section boundary, ending in a hard horizontal line.
Why: the model added the glow and never looked at the seam.
Fix: let the glow live inside its section (scale it down, reposition it) or extend it across the boundary. Check every soft element's edges at full-page zoom.

**81. Dot-grid background with masked glow** (strong)
Tell: faint `radial-gradient(circle, #333 1px, transparent 1px)` dot matrix across the hero, fading via `mask-image`, often with a glow spot behind the headline.
Why: the dotted "engineering canvas" backdrop is a stock Tailwind snippet, and every generator reuses it.
Fix: delete it unless the surface represents a canvas or a map. Replace it with a plain field plus grain, or make the grid specific: real ruler ticks, or a module aligned to the actual layout columns.

**82. Blueprint line-grid backdrop** (mild)
Tell: full-bleed graph-paper hairlines behind sections, unconnected to any measurable content.
Why: the blueprint look earns its place when a designer keeps it rare and points it at something measurable. Spread as wallpaper, it is filler.
Fix: constrain the grid to one section where it annotates something real (a diagram, a spec sheet), align its module to the layout grid, and drop it everywhere else.

**83. Noise overlay sitting on content** (mild)
Tell: an SVG `feTurbulence` or PNG grain layer at visible opacity laid over the entire viewport, text and UI included.
Why: "premium grain" is a memorized trick. Stacked above content it fights legibility and looks like a filter.
Fix: keep grain behind content, at 2–4% opacity on large flat fills and gradients, where it kills banding without becoming visible.

## Surfaces, borders, radius & shadow

**84. Reflexive glassmorphism** (strong)
Tell: `backdrop-blur-md bg-white/10 border border-white/20` cards and navs sitting over backgrounds that hold nothing to refract.
Why: frosted-glass cards appear on ~17% of AI-fingerprinted pages, where builders apply them as decoration rather than to solve a layering problem.
Fix: keep blur where content scrolls beneath it, such as a sticky nav. Elsewhere use solid surfaces one tonal step off the background. If glass stays, give it a real backdrop and an inner top-edge highlight, then check for blur banding.

**85. 1px white/10 borders on every dark card** (strong)
Tell: every dark-mode panel wrapped in `border border-white/10` (or `border-slate-800`) as the universal card treatment.
Why: shadcn and template starters ship this card styling, and generated UIs repeat it without a change.
Fix: use self-colored borders (the surface's own color nudged one step lighter) plus a slight tonal fill difference, or drop borders and separate cards by surface-value steps alone. Vary the treatment by component role.

**86. Static gradient border rings** (strong)
Tell: cards or CTAs ringed by an indigo→pink gradient stroke via the double-background border trick.
Why: a copy-pasted MagicUI/Aceternity signature that models emit unprompted. (Animated orbiting version: #173.)
Fix: use a 1px border in the accent at 30–40% opacity, or a solid 2px accent on a single priority element. If a gradient stroke survives, keep it inside a small contained mark such as a logo or badge, and off layout containers.

**87. Uniform rounded-xl/2xl on everything** (strong)
Tell: identical 12–16px radius, or blob-level 24px+, on cards, inputs, buttons, images, and sections alike.
Why: one radius token stamped across every component is the "16px border radius everywhere" fingerprint of generated layouts.
Fix: build a radius hierarchy by role (2–4px inputs, 8–12px cards, full-pill for tags and buttons), or commit to 0px sharp as a brand stance. Never round a container more than its parent.

**88. Default soft shadow on every card** (mild)
Tell: `shadow-md`/`shadow-lg` bloomed on all sides of every white card, added by reflex.
Why: symmetric all-around shadows ignore light direction, and models paste this stack with every card they write.
Fix: reserve shadows for elements that float, such as menus and modals, and give resting cards a border or tonal fill. When you do shadow something, layer directional values: a small tight one plus a large soft one, offset downward.

**89. Hairline border + wide diffuse shadow together** (mild)
Tell: cards carrying both a 1px light border and a large soft drop shadow.
Why: the model hedged between two card recipes and shipped both.
Fix: pick the edge system (border or flat) or the elevation system (shadow, no border) for each surface level, then hold to it across the page.

## Theme & component color patterns

**90. Untouched shadcn zinc theme** (strong)
Tell: stock shadcn look, meaning zinc/slate neutrals, `--radius: 0.5rem`, muted indigo or plain-black primary, `text-muted-foreground` grays, and default Card/Button styling.
Why: ~23.5% of audited AI pages ship shadcn defaults verbatim, so a new app lands in the middle of a very large pile of identical dashboards.
Fix: re-theme the tokens once and the rest follows. Swap the neutral ramp (warm gray or green-gray for zinc), set `--radius` to a deliberate 0/0.25/1rem, replace primary with a saturated brand accent, and add one signature token the kit doesn't ship (grain, shadow style, easing).

**91. Colored left-border accent card** (instant)
Tell: `border-l-4 border-indigo-500` (or a 3–4px top stripe, sometimes gradient) on feature and testimonial cards, clashing with the rounded corners.
Why: "colored left borders are almost as reliable a sign of AI-generated design as em-dashes."
Fix: remove the stripe and differentiate cards through tonal background, heading weight, or scale. If you need a category color, put a small solid dot or tag inside the card rather than an edge bar.

**92. Gradient pre-footer CTA slab** (strong)
Tell: full-width `rounded-3xl` box flooded with the same blue→purple gradient, centered white headline plus two buttons, sitting above the footer.
Why: the gradient CTA banner closes every generated SaaS template. (Structural angle: #22.)
Fix: keep the conversion block and change its material: solid brand color with grain, an inverted dark-on-light panel, or a full-bleed product photograph. Left-align the content inside it and use the page's real accent.

**93. "Linear glow" screenshot frame** (strong)
Tell: dark hero with the product screenshot wrapped in a glowing gradient rim, blurred color bloom underneath, often perspective-tilted.
Why: template authors cloned Linear's 2021 hero everywhere and models learned it from them, so the glow-rim treatment now dates a page. (Chrome-frame angle: #4.)
Fix: show the product as it is: flat screenshot, 1px surface border, a shadow in the right direction, or a working embed. Spend the effect budget on making the screenshot's content real and dense.

## VOCAB: greppable signals for this file

- Gradient/color classes: `from-indigo-500` `from-purple-500` `from-violet-500` `via-purple-500` `to-pink-500` `to-purple-600` `to-fuchsia-500` `bg-gradient-to-r` `bg-gradient-to-br` `bg-indigo-500|600` `bg-violet-600` `text-indigo-400|600` `ring-indigo-500` `bg-zinc-950` `bg-gray-950` `bg-slate-900` `bg-gray-50|100` `text-gray-400|500` `text-slate-400` `text-muted-foreground`
- Effects: `backdrop-blur(-md)` `bg-white/10` `bg-white/5` `border-white/10|20` `blur-3xl` `blur-2xl` `shadow-purple-500` `shadow-indigo-500/50` `shadow-lg` `shadow-xl` `rounded-xl|2xl|3xl` `border-l-4` `border-t-4` `mask-image` `mix-blend-multiply` `feTurbulence`
- CSS values/hex: `linear-gradient(135deg` `#6366f1` `#8b5cf6` `#a855f7` `#7c3aed` `#4f46e5` `#667eea` `#764ba2` `#ec4899` `#d946ef` `#22d3ee` `#0a0a0a` `#09090b` `#f3f4f6` `rgba(139, 92, 246` `rgba(99, 102, 241` `box-shadow: 0 0`
- shadcn tokens: `--radius: 0.5rem` `baseColor: "zinc"|"slate"` `bg-background` `text-foreground` `bg-card` `border-border` `bg-primary`

Sources: dev.to "Why every AI-built website looks the same — blame Tailwind's indigo-500" · github.com/funboy322/avoid-ai-design · pols.dev/slop · impeccable.style/slop · developersdigest.tech Show-HN audit · freedesignmd.com "Why shadcn looks generic"
