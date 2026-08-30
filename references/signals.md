# Computable signals

The catalogs describe tells in prose, which an agent has to recognize. This file holds the ones you can **measure**, which matters because a rule an agent can check against its own output produces compliance, while a rule it cannot check produces over-correction (see `method.md`).

Run these in DIAGNOSE to focus the audit, and in LINT to stop a regression.

**None of these classify a page.** They point at where to look. A page can pass every number here and still be slop, and a good page can fail several on purpose. Treat a failing signal as a question, not a verdict.

---

## 1. Layout and system signals

Computable from the DOM and computed styles. These are the strongest of the lot, because a design decision leaves a numeric fingerprint.

| Signal | How to measure | Slop reading |
|---|---|---|
| Font families | `new Set([...els].map(e => getComputedStyle(e).fontFamily)).size` | 1 across display and body (#94, #101) |
| Font weights in use | same, on `fontWeight` | exactly 2 (usually 400 and 700) despite a variable font loaded (#104) |
| Type scale ratio | H1 size ÷ body size | under 1.25 is a flat scale (#103) |
| Heading alignment | share of headings with `text-align: center` | 100% (#39) |
| Section padding variance | standard deviation of `paddingBlock` across `<section>` | 0, a metronome (#35) |
| Distinct radii | `new Set(radii).size` across buttons, cards, inputs, images | 1 value on every component role (#87) |
| Grid columns | distinct `gridTemplateColumns` counts | every grid is 3 (#25, #26) |
| Item counts | children ÷ columns, per grid | always a whole number, so content was padded or trimmed to fill (#32) |
| Boundary crossings | elements with negative margin or transform crossing a section edge | 0, slab stacking with no tension (#40) |
| Accent surface area | screenshot pixels within ΔE 10 of the accent ÷ total | under 4% invisible, over 12% no longer a signal |
| Max-width values | distinct `maxWidth` on section wrappers | 1 for the whole page (#34) |
| Scroll-reveal count | elements with `data-aos`, `whileInView`, or initial `opacity: 0` | more than 3 sections (#154) |
| Reduced-motion guard | `@media (prefers-reduced-motion)` present in CSS | absent while animations exist (#182) |
| Focus styles | rules matching `:focus-visible` | absent while `outline: none` present (#279) |
| Off-scale spacing | padding and margin values not on the declared scale | any (lint error) |
| Hex allowlist | hex literals not in `DESIGN.md` | any (lint error) |

### Contrast, computed rather than eyeballed
For every text node, compute the ratio against its effective background. Flag body under 4.5:1 and large text under 3:1. Also compute APCA Lc, since WCAG 2 overstates contrast near black and cannot derive a dark mode. Where they disagree, solve for APCA and gate on WCAG. Full procedure in `derivation.md`.

### Hue clustering, for the redesign
Convert your accent and your six closest competitors' accents to OKLCH and compare hue angles. Three or more competitors within ±20° of yours means the color is invisible in context. This turns "everyone uses blue" into a number and makes a palette proposal defensible.

---

## 2. Copy signals

Peer tools weight phrase density heaviest, and it is the most reliable of the text measures.

| Signal | How to measure | Slop reading |
|---|---|---|
| Blacklist phrase density | hits from the `copy-content.md` VOCAB list ÷ 100 words | any hit in a headline; over 3 per 500 words in body |
| Headline word count | words in the H1 | over 8, or wrapping past two rendered lines |
| Subhead sentences | sentence count | more than 1 |
| Feature blurb length | words per blurb | over 15 |
| Total hero words | H1 + subhead + note | compare before and after a rewrite; a rise means the rewrite failed |
| Em dash density | `—` per 100 words | over 2 |
| Rule-of-three density | polished triplets per 200 words | over 1 |
| Unsourced numerals | figures with no adjacent source, link or date | any |
| Exclamation marks | count | more than 1 per page |
| Emoji in headings | count in h1 to h3 | any |

### Invisible characters
A signal peers check and this catalog missed. Grep the rendered text for `U+200B` zero-width space, `U+200C`, `U+200D`, `U+FEFF` byte-order mark, and `U+00A0` where a plain space belongs. Model output and copy-paste pipelines leave these behind. They are invisible on screen and unambiguous in the source.

```bash
grep -Pn '[\x{200B}\x{200C}\x{200D}\x{FEFF}]' index.html
```

### Burstiness and type-token ratio, with the caveat stated
**Burstiness** is the variance in sentence length. **Type-token ratio** is distinct words divided by total words. Both run lower in generated prose.

They are useful as *editing prompts* and unreliable as *detectors*. Burstiness converges toward human levels as models get larger, and perplexity-based detectors misclassify famous human documents because those sit in the training data. Peer-reviewed work exists specifically on why these two fail at classification.

So use them this way: low burstiness means go vary your sentence lengths, which is good editing advice whoever wrote the text. Never report either as evidence that a page was generated.

---

## 3. Build and origin signals

Cheap, exact, and high-confidence. Run first.

```bash
# builder fingerprints and scaffold leftovers
grep -rniE 'lovable|gpteng|bolt\.new|v0\.dev|base44|Create Next App|vite\.svg|my-v0-project' dist/

# placeholder residue and dead wiring
grep -rniE 'lorem|ipsum|example\.com|\[insert|\{\{|your company|href="#"' dist/

# chat transcript leakage
grep -rniE "certainly[!,]? here|as an AI language model|I hope this helps" dist/

# secrets in the client bundle
grep -rnE '\b(sk-[A-Za-z0-9]{20,}|service_role)' dist/
```

Also check, since none of these show up in a screenshot: console errors on first paint, hydration warnings, `<title>`, favicon, meta description, Open Graph tags, robots.txt, sitemap.xml, and whether every `href` resolves.

---

## 4. The Slop Index

The raw Slop Score is unbounded, which makes it hard to compare two pages or to report progress. Normalize it.

```
raw   = 3×instant + 2×strong + 1×mild
index = round(100 × raw / (raw + 40))      # 0 to 100, never saturates
```

| Index | Reading |
|---|---|
| 0-15 | Clean. The first glance reads human. |
| 16-35 | Pattern-y. Designers side-eye it. |
| 36-60 | Recognizably AI. The 5-second test fails. |
| 61+ | Full slop. The site is the template. |

**Always report the per-category breakdown alongside it,** because the single number hides which half is broken:

```
Slop Index 47

  copy        23   ████████████
  layout      11   ██████
  color        7   ███
  code         4   ██
  motion       2   █
  imagery      0
  typography   0

Commitment 2 / 10
```

That page needs a copy pass, not a redesign. The aggregate alone would not have told you.

---

## 5. What to automate

In rough order of value per hour:

1. The **build and origin greps**. Exact, instant, no false positives.
2. The **hex allowlist and off-scale spacing** lint, once `DESIGN.md` exists.
3. **Computed contrast** on every text node.
4. **Blacklist phrase density** on rendered text.
5. **Layout counters**: font families, weights, radii, grid columns, scroll reveals.
6. **Invisible characters**.

Emit results as warnings before escalating to errors, so a team can absorb the change.

Leave to human judgment: whether the direction is right, whether an exception is deliberate, and whether the page looks designed. No counter measures those, and pretending otherwise is how a checklist starts governing generation, which `method.md` explains does not work.

## Sources

slopdetector.me on normalized scoring and weighted dimensions · the avoid-slop directory of open-source anti-slop tooling · GPTZero on perplexity and burstiness · Pangram on why perplexity and burstiness fail to detect AI · arXiv work on linguistic diversity under LLMs and on detection-method generalization · plus `derivation.md` and `copy-content.md` in this repo.
