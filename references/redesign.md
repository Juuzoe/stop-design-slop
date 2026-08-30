# Redesign: executing tier 5

`directions.md` tells you what to commit to. This file tells you how to build it, and how to check that the result is actually designed rather than merely clean.

Read it when the clean pass finished and the page still reads generic. That is the expected outcome of tiers 1 to 4, not a failure of them: those tiers remove evidence, and evidence removal alone leaves the defaults standing.

## Why tiers 1 to 4 leave slop behind

Run the whole clean pass and the page still carries every structural default: the typeface, the palette, the centered stack, the card grid, the uniform radius. Tier 5 is where those live, and none of them can be fixed one at a time.

Worse, a clean page has nowhere to hide. Restraint magnifies inconsistency, so removing the decoration exposes the fact that nothing underneath was decided. The fix is not more removal.

## Step 1: the design read

Before touching anything, state one line:

> Reading this as: **\<page kind>** for **\<audience>**, with a **\<vibe>** language, leaning toward **\<aesthetic family>**.

Infer it from page kind, the words the user used, any products they named, the audience, and existing brand assets. Accessibility-critical, public-sector and regulated briefs override aesthetic preference entirely.

Ask at most one clarifying question, and only when the read genuinely diverges. If you can infer it, declare it and move.

## Step 2: set three dials

| Dial | 1 | 10 |
|---|---|---|
| `DESIGN_VARIANCE` | perfect symmetry | asymmetric, off-grid |
| `MOTION_INTENSITY` | static | cinematic |
| `VISUAL_DENSITY` | airy | packed |

Baseline **7 / 6 / 4** for a marketing page. Adjust from the read:

| Read | VARIANCE | MOTION | DENSITY |
|---|---|---|---|
| minimalist, calm, editorial, Linear-style | 5-6 | 3-4 | 2-3 |
| premium consumer, luxury | 7-8 | 5-7 | 3-4 |
| agency, experimental, Awwwards | 9-10 | 8-10 | 3-4 |
| trust-first, public-sector, regulated | 3-4 | 2-3 | 4-5 |
| developer tool, docs | 6 | 4-5 | 5-6 |

A `DESIGN_VARIANCE` of 5 or above rules out the centered single-column stack by itself, which is how tell #2 dies.

## Step 3: the category-reflex check, at two altitudes

The step that decides whether the redesign is real. Run it before writing CSS, and again on the result.

**First order.** Could somebody guess your theme and palette from the category alone? Fintech to navy and gold, devtool to dark mode and neon, wellness to beige and sage, AI to purple. If yes, you landed on the first training-data reflex. Rework.

**Second order.** Could somebody guess it from category plus the obvious anti-reference? "AI tool that isn't SaaS-purple, so editorial-serif." "Devtool that isn't terminal-dark, so cream and Fraunces." This is the trap one tier deeper: the first reflex got avoided and the second one did not. Rework until neither answer is obvious.

Both altitudes have to fail before you proceed.

## Step 4: derive, do not pick

Use `derivation.md` for the values themselves. The short version:

- **Hue** comes from something the brand owns, keeping only the hue angle and re-deriving lightness and chroma. Check it against your competitors' hues and move to an empty arc if three or more cluster on yours.
- **Type** comes from the four-axis brief score, then measured gates (x-height ratio at or above 0.52, open apertures, stroke contrast at or below 1.6:1, `Il1` distinguishable).
- **Spacing** derives from the type scale rather than being invented.
- **Radius** derives from the typeface's own geometry.

## Step 5: build against the bans

These come from `design-taste`, and they are the patterns that survive a clean pass and still shout. Match and refuse: if you are about to write one, restructure the element.

**Layout**
- **No three equal feature cards.** The identical icon-plus-heading-plus-text row is banned outright. Use a two-column zig-zag, an asymmetric grid, a spec list, or a horizontal scroll.
- **No nested cards.** Always wrong.
- Cards at all are the lazy answer. Group with borders, dividers and space unless elevation communicates real hierarchy.
- **No hero-metric template**: big number, small label, supporting stats.
- The hero fits the viewport. Headline at two lines or fewer, subtext under 20 words, CTA visible without scrolling.

**Type**
- **No gradient text.** `background-clip: text` over a gradient is decorative and never meaningful. Solid color, with emphasis from weight or size.
- Display clamp maxes out around 6rem. Letter-spacing floor at -0.04em, since tighter makes letters touch.
- Avoid Inter as a reflex, and avoid Fraunces and Instrument Serif as the reflex "characterful" answers.
- Serif is discouraged as a default. "Feels premium" is not a reason.
- No oversized H1 that only shouts. Control hierarchy with weight and color, not raw scale.

**Surface**
- **No side-stripe borders.** A colored `border-left` above 1px on cards, callouts or alerts is never intentional.
- **No ghost cards:** a 1px border plus a soft shadow of 16px blur or more on the same element. Pick one.
- Cards top out at 12 to 16px radius. Choosing 24, 32 or 40px is its own tell.
- No glassmorphism by default. No neon or outer glows. No pure `#000` or `#fff`.

**Scaffolding**
- **No tiny uppercase tracked eyebrow above every section.** One named kicker as a deliberate system is voice; an eyebrow on every section is grammar.
- **No numbered section markers** (01 / 02 / 03) as default scaffolding. Numbers earn their place when the section genuinely is a sequence.
- **No generic step labels.** "Stage 1 / Stage 2", "Phase 01". The step content is the label.
- No scroll cues. Somebody looking at the hero knows what scrolling is.
- No decorative status dots, no rotated vertical text, no crosshair hairlines as decoration.
- The middle dot `·` is rationed to one per line.

**Fakery**
- **No div-based fake product UI.** A fake task list, terminal or dashboard built from styled divs is the single most reliable LLM-design tell. Use a real screenshot, a real embed, or no preview at all.
- No hand-drawn or sketchy SVG illustrations as a fallback. If you cannot render the scene with real assets, ship no illustration.
- No fake version footers inside fake screenshots.
- **No version or build stamps on a marketing page.** `v1.4.2`, `Build 0048`, `last sync 4s ago` are devtool fixtures. They belong in docs, an app shell or a changelog, never a landing hero or footer.
- No locale, city, time or weather strips unless the brief is genuinely about a place.

**Content**
- No generic names (John Doe, Sarah Chen). No generic avatars. No startup-slop brand names (Acme, Nexus).
- No fake-perfect numbers. `99.99%` and `50%` read as invented; real data is messy.
- Zero em dashes anywhere visible, which is the most-violated tell of all.

## Step 6: never ship the first version

The first version is a draft that exists to be critiqued. The polish separating designed work from clean work lives in the second and third pass.

```
read the brief -> build -> critique with fresh eyes -> refine -> pre-flight -> ship
```

Skipping the critique is the failure mode. Come back to the page after doing something else, and write the critique as a Before / After / Why table before touching the code again.

## Step 7: pre-flight

Check every line before calling it done.

**Composition**
- [ ] One dominant focal point, with everything else demonstrably subordinate
- [ ] Asymmetry specified numerically, not just "avoid centering"
- [ ] At least one element touching, bleeding past or overlapping a container edge
- [ ] A decisive scale jump between display and body, not incremental steps
- [ ] Spacing that groups: tight within a unit, wide between sections
- [ ] One named exception where the system is broken on purpose

**Type and color**
- [ ] Two families at most, plus optional mono, paired on a contrast axis
- [ ] Body 65 to 75ch, line-height 1.5 to 1.6, headings 1.1 to 1.2
- [ ] `text-wrap: balance` on headings, `pretty` on prose
- [ ] Body contrast at or above 4.5:1, large text at or above 3:1, placeholders included
- [ ] One accent, locked across the page, saturation under about 80%
- [ ] Neutrals tinted toward the brand hue rather than reflexively warm

**States and motion**
- [ ] All eight states designed: default, hover, focus, active, disabled, loading, error, success
- [ ] `:focus-visible` present everywhere, never `outline: none` without a replacement
- [ ] Motion under 300ms, ease-out for entrances, never `ease-in` on UI
- [ ] Only `transform` and `opacity` animated
- [ ] `prefers-reduced-motion` fallback on every animation
- [ ] Touch targets at or above 44px

**The tests**
- [ ] Five-second test: the first-impression sentence names neither "generic" nor a tool
- [ ] Lineup test: a stranger can pick this page out of five competitors with the logos removed
- [ ] Category-reflex check passes at both altitudes
- [ ] Squint test: something has a distinct silhouette
- [ ] Text-strip test: with all copy removed, something still says whose site this is

## Step 8: score

The redesign gate needs both numbers, unlike the clean pass:

```
Slop Score       = 3×instant + 2×strong + 1×mild   ->  0 to 8
Commitment Score = filled, propagated, nameable      ->  5 or more
```

Plus every mandatory positive from `method.md`, and no regression in contrast, focus visibility, page weight, functionality or mobile layout.

## Worked example

`examples/hero-redesign.html` takes the same FlowSync page through this file. Its design read, dials and the reasoning behind each move are documented in `examples/README.md`, including the two reflexes it had to refuse before arriving at the direction it uses.

## Sources

The `design-taste` skill, which synthesizes Emil Kowalski's design-engineering, impeccable, and taste-skill · involve.me and moburst on 2026 landing-page typography and contrast · muffingroup and themex.studio on why minimal work reads generic without art direction · plus `directions.md`, `derivation.md` and `art-direction.md` in this repo.
