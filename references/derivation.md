# Derivation: procedures that turn a brief into exact values

Executable procedures for the four decisions a direction leaves open. Every step runs without taste, and where taste is unavoidable the step says so and supplies a decision rule.

This file is what makes `directions.md` yours rather than a template. Two sites in the same direction should differ here.

---

# 1. Color

## Phase 1: source the hue, not the color

You extract **one number**, the hue angle `H`. Lightness and chroma from any sampled source are artifacts of lighting, print stock and JPEG compression. Discard them and re-derive.

Pick the first ladder that yields a physical referent:

| Ladder | Method |
|---|---|
| **Artifact** | The brand owns an object: product finish, packaging, uniform, vehicle. Sample the largest continuous mid-tone region, not a highlight or shadow. |
| **Material** | The core substance: kraft paper, oxidized copper, indigo dye, milled aluminium, roasted coffee. Sample a reference photograph. |
| **Place** | A geographic or architectural anchor the brand claims. Sample the dominant field, not the subject. |
| **Domain convention** | The functional signal color of the domain: marine safety orange, surgical green, blueprint cyan, terminal phosphor. Use the standardized value. |

**Decision rule** when several apply: use the earliest ladder producing a referent a customer could touch or has already seen. If none do, you have a positioning problem rather than a color problem, so return to the brief.

### The differentiation gate
Convert your six closest competitors' primaries to OKLCH and record each `H`. Plot on a 360° line and find the largest empty arc.

If your candidate hue sits inside an occupied ±20° cluster holding three or more competitors, you are invisible. Either move to the nearest edge of the largest empty arc, or keep the hue and differentiate on chroma and neutral temperature as a documented decision rather than a default.

Convert the sampled hex to OKLCH, keep `H`, discard the rest.

## Phase 2: find the hue's physical ceiling

Compute `Cmax(L, H)` by bisection: the largest chroma where `oklch(L C H)` stays inside sRGB.

```js
function maxChroma(L, H) {
  let lo = 0, hi = 0.5;
  for (let i = 0; i < 40; i++) {
    const mid = (lo + hi) / 2;
    inGamut(oklchToLinearSrgb(L, mid, H)) ? lo = mid : hi = mid;
  }
  return lo;
}
```

Sweep `L` from 0.03 to 0.99 in 0.002 steps and record the argmax to get `(L_peak, C_ceiling)`.

**This number dictates everything downstream, and it varies enormously by hue:**

| Hue | | `L_peak` | `C_ceiling` |
|---|---|---|---|
| 39° | orange | 0.678 | 0.215 |
| 99° | yellow | 0.905 | 0.188 |
| 159° | green | 0.880 | 0.201 |
| 189° | teal | 0.900 | 0.156 |
| 249° | blue | 0.665 | 0.185 |
| 279° | violet | 0.485 | 0.296 |

**Plan for the consequence.** Yellow, green and teal peak light (L 0.88 to 0.90) and therefore cannot carry white text at any saturation. Violet peaks dark and cannot carry black text. Orange and blue sit in the usable middle. If your hue peaks above L 0.75, your solid brand color is a **black-text surface**, so stop planning white-on-brand buttons now.

Set the working peak: `Cpeak = min(C_ceiling × 0.94, 0.19)`. The 0.94 is gamut safety, since clipping at the boundary produces banding and differs across browsers. The 0.19 is empirical: above roughly 0.20 in sRGB, color reads as vibrating rather than saturated.

## Phase 3: build the 12-step ramp

Use Radix's step semantics, the only widely-deployed scale where each step has a stated job.

| Step | Job |
|---|---|
| 1–2 | App background, subtle background |
| 3–5 | UI element background: base, hover, active |
| 6–8 | Borders: subtle separator, element border and focus ring, strong border |
| 9–10 | Solid background (the brand color proper) and its hover |
| 11–12 | Low-contrast text, high-contrast text |

**Lightness ladder (light mode).** These are the mean OKLCH `L` values obtained by reverse-converting Radix's hand-tuned orange, blue and slate scales. They are what expert-tuned scales converge on rather than an invented formula.

```
step: 1      2      3      4      5      6      7      8      9      10     11     12
L:    0.992  0.981  0.960  0.932  0.900  0.860  0.808  0.740  0.680  0.645  0.570  0.335
CM:   0.015  0.065  0.150  0.260  0.360  0.450  0.530  0.660  1.000  0.970  0.860  0.430
```

`C(i) = min(Cpeak × CM[i], maxChroma(L[i], H) × 0.94)`

Chroma rises super-linearly to a peak at step 9, then falls. Constant chroma, or chroma taken from HSL saturation, produces the classic failure where light tints go chalky pink and dark shades go muddy brown. The `min()` keeps the ramp in gamut at both extremes where the sRGB solid narrows.

**Why not HSL.** HSL lightness is `(max+min)/2` of the RGB channels and has no relationship to perceived lightness. `hsl(60 100% 50%)` and `hsl(240 100% 50%)` are both "50% lightness" and differ by roughly 20:1 in actual luminance. A Sass `darken()` ramp drifts hue, equal-L steps look unequal, and you cannot predict contrast from the numbers. In OKLCH, `L` is perceived lightness held constant across hue, which is what makes these ladders possible.

## Phase 4: solve contrast rather than eyeballing it

Target: step 11 at **APCA Lc 60** or better on step 2, step 12 at **Lc 90** or better.

| Lc | Minimum use |
|---|---|
| 90 | Body text at 14px/400, the preferred level for fluent reading |
| 75 | Minimum for columns of body text, 18px/400 |
| 60 | Non-body content text, 24px/400 or 16px/700 |
| 45 | Headlines with fine detail |
| 30 | Placeholder, disabled |
| 15 | Non-text, the floor of visibility |

**APCA against WCAG 2.** WCAG 2 is symmetric and polarity-blind. APCA is asymmetric, using different exponents for dark-on-light and light-on-dark, and it accounts for size and weight. WCAG 2 materially overstates contrast near black, which is why it cannot derive a dark mode.

**They disagree, so ship both.** Measured on real Radix pairs:

| Scale | APCA Lc | WCAG |
|---|---|---|
| orange 11 on 2 | 66.2 | **4.25, fails AA** |
| blue 11 on 2 | 68.9 | 4.53, passes |

Solve for APCA, since it predicts readability, then assert **WCAG ≥ 4.5 as a hard gate**, since that is what audits use. Warm hues (H 20 to 90) usually need the correction; cool hues usually do not.

**Holding 4.5:1 without losing saturation.** The naive move is to desaturate. Instead hold `H`, hold chroma at its ceiling, and bisect on `L` alone:

```js
function darkestForWhiteText(H, target = 4.5) {
  let lo = 0.2, hi = 0.9;
  for (let k = 0; k < 60; k++) {
    const m = (lo + hi) / 2, c = maxChroma(m, H) * 0.94;
    wcag('#ffffff', toHex(m, c, H)) >= target ? lo = m : hi = m;
  }
  return lo;
}
```

Because the chroma ceiling is a shallow curve near its peak, moving `L` down costs very little chroma. In the worked example below, dropping L from 0.680 to 0.586 to reach 4.5:1 costs 8% of chroma. Desaturating instead would have cost over 40%.

## Phase 5: tinted neutrals

Neutral chroma as a function of lightness, at the brand hue:

```
C_neutral(L) = 0.015 × sin(π·L)^0.8
```

This is an empirical fit to Radix slate. Evaluating it at H 250 with the slate lightness ladder reproduces `#f8f9fa`, `#eceef0` and `#e6e8eb`, byte-identical to Radix slate steps 2, 4 and 5. Ceiling: `C ≤ 0.015`, above which the ramp stops reading as neutral and competes with the brand color.

```
step: 1      2      3      4      5      6      7      8      9      10     11     12
L:    0.991  0.982  0.963  0.948  0.930  0.914  0.890  0.829  0.649  0.615  0.540  0.204
```

**Hue for the neutral.** Default to the brand hue. Two overrides: if the brand hue sits between 85° and 175° (yellow-green through green) the grays read sickly, so substitute 40° (warm) or 250° (cool) chosen by the brand's voice, defaulting to cool. And if the primary is high chroma across large fields, rotate the neutral 180° away at low chroma so the page does not read as one tinted wash.

## Phase 6: the accent, chosen by job

Do not "pick a complement." Enumerate candidates and select by function.

| Relationship | Offset | Use when |
|---|---|---|
| **Analogous** | ±30° | Visual interest without a second meaning: chart series, gradient ends. Never for CTAs, since it reads as the same color. |
| **Split-complement** | +150° and +210° | The default for product UI. A high-contrast accent plus a calmer one, both distinguishable at small sizes. Primary to surfaces, split-A to the CTA, split-B to informational states. |
| **True complement** | +180° | One accent, maximum separation. Two complements at high chroma adjacent to each other vibrate, so separate them with neutral. |
| **Triadic** | +120°, +240° | Multi-category systems where three peers are equally weighted. Needs strict 60/30/10 or it looks like a toy. |
| **Semantic, fixed** | success ~145°, warning ~75°, danger ~25°, info ~245° | Always ship these. If the brand hue collides with a semantic, shift the semantic by ±15° and raise its chroma so it still reads as an alarm. |

**Constraint:** run Phase 2 on the candidate. If its `L_peak` sits within 0.06 of the primary's, the two are indistinguishable in grayscale and to deuteranopes. Push one off-peak until the difference is at least 0.10.

## Phase 7: 60/30/10 as a surface-area budget

| Share | Role | Ramp steps |
|---|---|---|
| 60% | Dominant surface | Neutral 1–2. Almost always near-white or near-black, **not** the brand color. |
| 30% | Secondary structure | Neutral 3–8: cards, sidebars, borders, secondary text. |
| 10% | Accent | Brand 9–12 plus semantic solids: primary buttons, links, active nav, focus rings. |

**Audit executably:** screenshot a page, count pixels by nearest palette bucket, and assert the accent bucket sits between 4% and 12%. Below 4% the brand is invisible, above 12% the accent stops signaling.

## Phase 8: dark mode is a derivation, not an inversion

1. **Background floor.** Never `#000`. Bottom surface at L 0.18 to 0.21. Pure black causes halation against light text and leaves no headroom for elevation.
2. **Elevation is lightness.** Each surface level adds +0.03 to +0.05 L. Shadows are close to invisible on dark grounds.
3. **Chroma reduction.** Multiply mid-step chroma by ~0.85, and much harder at the top: the measured ratio of Radix dark step 12 to its step 9 is 0.27, against 0.43 in light mode. Saturated colors bloom on dark.
4. **The top compresses.** Step 12 lands at L ≈ 0.92 rather than 1.0, since full white on near-black is uncomfortable at length.

```
L_dark:  0.190  0.213  0.265  0.310  0.350  0.400  0.460  0.540  0.670  0.710  0.780  0.920
CM_dark: 0.100  0.130  0.290  0.440  0.500  0.520  0.570  0.670  1.000  0.910  0.700  0.270
```

**Invariants across modes:** hue is identical, and step 9 keeps the same `L` in both modes. Radix orange 9 is `#f76b15` in light and dark alike. This is what makes a button look like the same brand in both themes.

---

# 2. Type

## Phase 1: score the brief

Four independent axes, each −2 to +2. These are the only judgments here; everything after is lookup.

| Axis | −2 | +2 |
|---|---|---|
| Formality | vernacular, hand-made | institutional, official |
| Warmth | mechanical, neutral | human, calligraphic |
| Era | historical, pre-1900 | contemporary, technical |
| Density | editorial, airy | dense UI, data-heavy |

## Phase 2: classification, connotation, constraint

| Class | Structural markers | Connotes | Body text? |
|---|---|---|---|
| **Humanist serif** (Venetian, Garalde) | Diagonal stress, bracketed serifs, moderate contrast, small x-height | Scholarly, warm, pre-industrial, authored | Yes; best in print, adequate on screen at 18px+ |
| **Transitional serif** | Near-vertical axis, higher contrast, sharper brackets | Institutional, editorial authority | Yes |
| **Didone / Modern** | Extreme contrast, vertical axis, unbracketed hairlines | Luxury, fashion, cold precision | **No.** Hairlines vanish below ~24px. Display only. |
| **Slab** | Heavy, low contrast, prominent unbracketed serifs | Industrial, blunt, sturdy | Humanist slabs only; geometric slabs are display |
| **Grotesque** | Irregular curves, awkward weight distribution, spurred G | Utilitarian, period, characterful | Yes, and the quirks are the brand asset |
| **Neo-grotesque** | Regularized curves, closed apertures, horizontal terminals | Neutral, corporate, deliberately anonymous | Yes, though closed apertures hurt at small sizes |
| **Humanist sans** | Calligraphic skeleton, open apertures, two-storey a and g, varied widths | Approachable, legible, public signage | **Yes. The default for UI body.** |
| **Geometric sans** | Circle-and-line, monolinear, single-storey a, uniform widths | Modernist, minimal, Bauhaus | **No.** Among the least legible sans classes; display only. |
| **Monospace** | Fixed advance width, exaggerated spurs, large apertures | Technical, machine-authored, credible-as-data | Code, tabular numerals and short labels only |

**Mapping.** High Formality plus high Era goes neo-grotesque or transitional. High Warmth goes humanist. Low Era goes Garalde or grotesque. High Density goes humanist sans with a tall x-height. Geometric and didone are display-only whatever the scores: if the brief wants their connotation, use them at display over a humanist sans.

## Phase 3: evaluate a specific face

Load at 16px and measure.

| Metric | Gate for UI body | Gate for display |
|---|---|---|
| x-height ÷ cap-height | **≥ 0.52**, and ≥ 0.55 for dense UI | 0.45–0.55 (lower reads more elegant) |
| Aperture (render `c e s a` at 12px, zoom 3×) | **Open.** Closed apertures fill in under antialiasing | Any |
| Stroke contrast (thickest ÷ thinnest) | **≤ 1.6:1** | up to 8:1 |
| Width (advance of `nnnnnnnnnn` ÷ 10 ÷ em) | 0.50–0.58em dense, up to 0.62 editorial | Any |
| Disambiguation (`Il1\| rn m O0`) | `I`/`l`/`1` must be three distinct shapes; `rn` must not read as `m` | Less critical |
| Numerals | **Tabular required** if any tables, prices or data | — |
| Weights | ≥ 4, or a variable `wght` axis | ≥ 2 |

**Quirk features** are what make a face ownable: single-storey `a`, descending `J`, flat-topped `t`, spurless `G`, canted terminals, a distinctive ampersand, a splayed `R` leg, an open lower loop on `g`. Pick a face with **one or two**, never five.

**Decision rule for which quirk:** it must be visible in the brand name set at 48px in the display face. If the name contains no letter carrying the quirk, it is invisible to most viewers, so pick another.

## Phase 4: pairing

Three legal strategies. Pick one.

**A. Superfamily.** One family spanning serif, sans and mono from a shared skeleton. Members share x-height and rhythm by construction, so the pairing cannot fail. Use when Density ≥ +1. Cost: less distinctive.

**B. Contrast by class.** Pair across the table while holding one attribute constant (x-height, width, or era). Transitional serif display over humanist sans body gives editorial authority. Grotesque display over Garalde body gives period craft. Slab over neo-grotesque gives industrial.

**Measured gate:** x-height difference ≤ 8% at the same font-size. Above that, do not abandon the pair, correct it optically by setting the smaller face 1 to 2px larger or via `font-size-adjust: ex-height`.

**C. One face, many weights.** A single family with five or more weights plus an italic, where hierarchy comes from weight, size, case and color. Use when the face has strong quirks that a second family would dilute, or when the font budget is under 100KB.

**The prohibited zone:** two faces from the same class but different families. Too little difference to read as intentional, too much to read as one voice. It reads as a mistake, and it is the most common pairing failure.

**Hard cap: two families plus one mono.**

## Phase 5: setting conventions

**Tracking by size.** The rule is inverse: bigger gets tighter.

| Rendered size | `letter-spacing` |
|---|---|
| ≥ 56px | -0.03em |
| 40–56px | -0.022em |
| 32–40px | -0.018em |
| 24–32px | -0.012em |
| 20–24px | -0.006em |
| 16–20px (body) | **0. Never track body text.** |
| 13–16px | +0.005em |
| 11–13px | +0.015em |
| All-caps labels, any size | +0.06em to +0.10em |

Fonts are spaced for a reference size of roughly 10pt, so every departure needs compensation. **If the face has an `opsz` axis, skip this table entirely** and set `font-optical-sizing: auto`.

**Leading.**
```
ratio(size_px) = clamp(1.02, 1.75 − 0.011 × size_px, 1.65)
```
Adjust ±0.05 per ±10ch of measure beyond or below 60ch. Then round the computed line-height in px to the nearest 4 and verify the ratio lands in 1.4–1.65 for body, 1.0–1.45 for display. If body falls out of range, adjust the **font size** by ±1px rather than the line-height. This is why 16px and 18px are better base sizes than 17px: 16×1.5=24 and 18×1.556=28 both land on the grid, 17×1.5=25.5 does not.

**Measure.** 45 to 90 characters, target 60 to 75, classic optimum 66. Enforce with `max-width: 66ch`. Longer measures need more leading; the two are coupled.

**Weight.** Body at 400, never 300, since thin weights fail APCA at small sizes. Emphasis at 600 rather than 500, since 500 against 400 is imperceptible at 16px. Headings 600 to 700, with 800 and 900 reserved for display at 40px and above where closed counters stop mattering. **In dark mode**, light-on-dark strokes bloom, so drop body weight one step if a variable axis allows, or reduce foreground lightness rather than adding weight.

## Phase 6: delivery

**WOFF2 only.** Roughly 97% support and 30% smaller than WOFF.

**Variable against static:** variable wins at three or more weights or when animating an axis. At one or two weights a well-subset static pair is usually smaller. Compute both.

**Subset** with `pyftsubset`, cutting up to 90%:
```bash
pyftsubset Brand-VF.ttf --flavor=woff2 --layout-features='kern,liga,calt,tnum' \
  --unicodes='U+0000-00FF,U+2000-206F,U+2190-2193,U+2212,U+2713' \
  --output-file=brand-latin.woff2
```

**Preload exactly one file,** the one used above the fold. Preloading several creates competing high-priority requests and negates the benefit. Always `font-display: swap`, or `optional` when CLS matters more than first-paint brand fidelity.

**Metric-override fallback,** which takes swap CLS to 0.00:
```css
@font-face { font-family: "Brand-fallback"; src: local("Arial");
             ascent-override: 90.20%; descent-override: 22.48%;
             line-gap-override: 0%; size-adjust: 107.40%; }
```
Derive the numbers: `size-adjust = webfont.avgCharWidth / fallback.avgCharWidth`, and each override is the webfont metric divided by its `unitsPerEm`, divided by `size-adjust`.

---

# 3. Scale and space

## Choose the ratio by rule

| Ratio | Name | Use when |
|---|---|---|
| 1.125 | Major second | Extremely dense data UI needing 8+ steps in a small range |
| 1.200 | Minor third | **Product UI default.** Dashboards, admin, docs. |
| 1.250 | Major third | General purpose, safe at most sizes |
| 1.333 | Perfect fourth | **Marketing and editorial default.** Distinct hierarchy. |
| 1.414 | Augmented fourth | Poster-like pages with very few text levels |
| 1.5 / 1.618 | Perfect fifth, golden | Two-level pages only. At five steps from 16px you reach 178px. |

**Rule:** 1.2 if the page has six or more text levels or any tables. 1.333 if four or fewer levels plus a hero. 1.25 in between. For fluid scales use the smaller ratio at the small viewport and the larger at the large one, since hierarchy should be quieter on a phone.

## Choose the base

`base × target line-height` must land on a multiple of 4. 16px → 24 ✓. 18px → 28 ✓. 20px → 32 ✓. 17, 19 and 21 all fail; reject them.

## Generate and interpolate

`size(n) = base × ratio^n` for n from −2 to +6, rounded to whole px. Type sizes need not sit on the grid, but line-heights must.

```
slope = (maxRem − minRem) / (maxVWrem − minVWrem)
yInt  = (−minVWrem × slope) + minRem
font-size: clamp(minRem, yInt rem + (slope × 100) vw, maxRem)
```

**Accessibility gate:** the middle term must contain a `rem` component. A pure `vw` size ignores the user's browser font-size setting.

## Derive spacing from the type scale

Do not invent spacing values. Take **type step 0 as the space base** and apply multipliers:

```
3xs 0.25  2xs 0.50  xs 0.75  s 1.00  m 1.50  l 2.00  xl 3.00  2xl 4.00  3xl 6.00
```

Round each to the nearest 4. Use 4 rather than 8 as the rounding unit, since an 8pt grid leaves available line-heights too far apart for small text.

When the space base equals the body font-size, `--space-s` is one line of body text, `--space-m` is 1.5 lines and `--space-l` is two lines. Vertical rhythm then falls out rather than being enforced by hand.

---

# 4. Geometry

## Radius base, derived from the type

| Face character | `--r-base` | Reads as |
|---|---|---|
| Geometric or rounded-terminal humanist | 8–12px | Friendly, consumer |
| Neo-grotesque, flat terminals | 4–6px | Neutral, professional |
| Grotesque or slab, sharp forms | 2–4px | Precise, industrial |
| Didone or high-contrast serif | 0–2px | Editorial, luxury |

**Decision rule when ambiguous:** look at the counter of the face's `o`. A near-circle goes soft (8–12). A rounded rectangle goes 4–6. Visible flat sides go 0–4.

## Ramp and nesting

```css
--r-xs:   calc(var(--r-base) * 0.5);   /* checkbox, tag, badge */
--r-sm:   var(--r-base);               /* input, button */
--r-md:   calc(var(--r-base) * 1.5);   /* card */
--r-lg:   calc(var(--r-base) * 2.5);   /* modal, sheet */
--r-full: 9999px;                      /* pill, avatar */
```

Two hard constraints. Radius must stay at or below `min(width, height) / 2`, beyond which CSS reduces all corners proportionally and you get a stadium. And never mix a pill with square-cornered siblings in one control group.

**Nesting:** `innerRadius = outerRadius − padding`, which keeps arc centers concentric rather than merely smaller.

```css
.card > * { border-radius: max(0px, calc(var(--r-outer) - var(--pad))); }
```

Clamp at 0 rather than going negative. If the inner radius lands between 0 and 2px, snap to 0, since a 1px radius is indistinguishable from square. Three levels deep, apply recursively; when it reaches 0, stop nesting radii and switch to borders or spacing.

## Borders from the ramp

1px at all densities. 2px only for focus rings and selected states. Hairlines below 1px are unreliable across pixel ratios, so reduce contrast instead of width.

- Non-interactive separators, card edges, table rules: **neutral step 6**
- Interactive borders (inputs, buttons): **neutral step 7**
- Hover and emphasis: **neutral step 8**
- Focus ring: **brand step 7 or 8** at 2px with a 2px offset in the surface color

```css
box-shadow: 0 0 0 2px var(--surface), 0 0 0 4px var(--brand-8);
```

The ring must clear 3:1 against both the component and the adjacent background.

## Borders, shadows, or lightness

**Borders** when the surface is dark, the element sits in a dense list, the element does not move, or the boundary is functional rather than spatial.

**Shadows** when the element genuinely floats and could be dismissed, when it is draggable, or to show scrolled-under content.

**Surface lightness** in dark mode at every level: add +0.03 to +0.05 L per step instead of a shadow.

Never combine a strong shadow with a strong border on one element. An object cannot both float and be inset.

## Shadow construction

**Fix the light source once**, globally: above and slightly left, so shadows fall down and right, with `y-offset = 2 × x-offset`. Every shadow in the system shares that ratio.

**Layer rather than blur.** A single shadow has linear falloff; real penumbras do not. Stack layers doubling both offset and blur: `x = x₀·2ⁿ`, `y = 2x₀·2ⁿ`, `blur = y`.

**Budget the opacity.** Total darkness is roughly the sum, so divide a fixed budget across layers. Higher elevation means more layers at lower per-layer opacity, which produces the soft wide penumbra of a distant object.

**Never `rgba(0,0,0,x)`.** Black alpha desaturates what lies beneath and reads as grey haze. Derive the shadow from the palette: brand hue, L 0.30 to 0.35, C 0.04 to 0.06. Tokenize as a bare triplet so alpha varies per layer.

| Level | Job | Layers | x₀ | Total opacity |
|---|---|---|---|---|
| 1 | resting card, input | 1 | 0.5px | 0.20 |
| 2 | raised or draggable card | 3 | 1px | 0.30 |
| 3 | dropdown, popover, tooltip | 4 | 1px | 0.34 |
| 4 | modal, sheet | 5 | 2px | 0.35 |

**Couple motion to elevation.** When an element lifts on hover, it must translate up by roughly the shadow's y-offset delta. A shadow that grows while the object stays put is impossible.

---

# Worked example, end to end

**Brief:** *Halyard*, direct-to-consumer rigging and deck hardware for small sailboats. Voice: workshop practical, safety-serious, no nautical kitsch.

**Color Phase 1.** The artifact ladder applies, since the anodized cleats ship in one signature finish. Sampled mid-tone `#D9531E`. The domain ladder agrees, since marine safety convention is also orange, and two ladders agreeing is the strongest possible signal. Competitor audit: four of six cluster at H 220 to 250 (nautical navy), one at 145, one achromatic. The 20 to 90 arc is empty, so the hue is ownable. Keep **H = 39.4°**.

**Phase 2.** `C_ceiling` 0.215 at `L_peak` 0.678. `Cpeak = 0.190`.

**Phase 3 and 4, key steps:**

| Step | oklch | hex | WCAG vs 1 | APCA on 2 |
|---|---|---|---|---|
| 6 | `oklch(0.860 0.074 39.4)` | `#fcc1ad` | 1.54 | 22.1 |
| 9 | `oklch(0.680 0.190 39.4)` | `#f5642e` | 3.04 | 53.4 |
| 11 | `oklch(0.570 0.163 39.4)` | `#c34c1e` | 4.70 | **68.6** ✓ |
| 12 | `oklch(0.335 0.082 39.4)` | `#592513` | 12.09 | **93.8** ✓ |

**The interesting failure.** Step 9 `#f5642e` at L 0.680 fails white text (WCAG 3.11) and passes black (6.74). But Halyard's buttons need white, since dark text on safety orange reads as a hazard placard rather than a CTA. Bisecting `L` downward at ceiling chroma gives `oklch(0.586 0.175 39.4)` = `#cd4c17`, which clears white text at 4.52:1 and APCA Lc 75.9. **Cost: 7.9% of chroma.** Desaturating would have cost over 40%. Ship two step-9s: `--brand-9` for decorative fills and `--brand-solid` for anything bearing white text.

**Accent.** Split-complement gives 189.4° and 249.4°. Teal at 189.4° has an `L_peak` 0.22 away from the primary, so it is distinguishable; assign it to informational and links. Blue at 249.4° is the competitor cluster, so reject it as a brand accent and keep it only as the `info` semantic. Danger rotates from 25° to 12° to clear the brand by more than 25°, and warning rotates from 75° to 92°.

**Type.** Scores: Formality 0, Warmth +1, Era −1, Density +1. Warmth and Density point to humanist sans for body; Era points to grotesque for display. Geometric is rejected as Silicon-Valley-coded against Era −1, didone as too formal. Strategy B, held constant on era, both drawing on early-20th-century industrial lettering. The quirk check passes: "Halyard" contains `a` and `y`, which carry the display face's distinctive bowl and tail. Measured x-height delta 6.1%, under the 8% gate, so no optical correction is needed.

**Geometry.** Sharp grotesque terminals give `--r-base: 4px`. Shadow color becomes `oklch(0.32 0.06 39.4)`, the brand hue at low chroma, rather than black.

```css
:root {
  --brand-h: 39.4;
  --brand-6:     oklch(0.860 0.074 var(--brand-h)); /* subtle border */
  --brand-8:     oklch(0.740 0.125 var(--brand-h)); /* focus ring */
  --brand-9:     oklch(0.680 0.190 var(--brand-h)); /* decorative solid */
  --brand-solid: oklch(0.586 0.175 var(--brand-h)); /* white-text solid, 4.52:1 */
  --brand-11:    oklch(0.570 0.163 var(--brand-h));
  --brand-12:    oklch(0.335 0.082 var(--brand-h));
  --n-6:  oklch(0.914 0.007 var(--brand-h));
  --n-11: oklch(0.540 0.015 var(--brand-h));
  --n-12: oklch(0.204 0.010 var(--brand-h));
  --shadow-color: 30deg 22% 24%;
  --r-base: 4px;
}
@media (color-gamut: p3) {
  :root { --brand-9: oklch(0.680 0.225 var(--brand-h)); }
}
@media (prefers-color-scheme: dark) {
  :root {
    --brand-1:  oklch(0.190 0.019 var(--brand-h));
    --brand-11: oklch(0.800 0.111 var(--brand-h));
    --brand-12: oklch(0.920 0.027 var(--brand-h));
  }
}
```

Lint gate: `stylelint-gamut` with `gamut/color-no-out-gamut-range`, plus `function-disallowed-list: ["rgb","rgba","hsl","hsla"]`.

---

# Sources

evilmartians.com on OKLCH · radix-ui.com/colors on scale composition · git.apcacontrast.com · lea.verou.me on LCH and contrast-color · bottosson.github.io on Oklab and color pickers · material-foundation color utilities · culorijs.org · joshwcomeau.com on designing shadows · cloudfour.com on nesting rounded corners · atlassian.design on elevation · smashingmagazine.com on type classification and fluid scales · practicaltypography.com · typotheque.com on size-specific spacing · css-tricks.com on letter-spacing · utopia.fyi on clamp and space calculators · carbondesignsystem.com on spacing · developer.chrome.com on font fallback · MDN on `ascent-override` · uxpin.com on optimal line length · adobe.design on font pairing

**On the numbers:** every OKLCH value, hex, WCAG ratio and APCA figure in the worked example was computed rather than estimated, using Ottosson's matrices, 40-iteration gamut bisection, and the APCA 0.1.9 constants. The lightness and chroma ladders come from reverse-converting Radix's hand-tuned scales to OKLCH and averaging. The neutral formula reproduces Radix slate exactly at H 250.
