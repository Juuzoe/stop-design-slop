# Worked example: one hero at three depths

| Before | Tiers 1 to 2 | Tiers 1 to 4 |
|---|---|---|
| <img src="hero-before.png" alt="Slop hero with pulsing sparkle badge, gradient keyword, glow orbs and fabricated social proof"> | <img src="hero-tier2.png" alt="Same hero with the design untouched, minus the builder badge and the fabricated social proof"> | <img src="hero-clean.png" alt="Cleaned hero in the same visual language with a short concrete headline"> |

Three self-contained HTML files, plus the screenshots above.

- **`hero-before.html`** — a hero carrying about 25 catalogued tells, of the kind a builder emits from a one-line prompt.
- **`hero-tier2.html`** — the same page after tiers 1 and 2 only.
- **`hero-clean.html`** — the same page after tiers 1 to 4.

## Why the middle one matters

Tiers 1 and 2 leave the design alone completely. The glow orbs, the gradient keyword, the pulsing sparkle badge, the emoji icons, "Supercharge Your Workflow" and the all-in-one subhead all survive, because rewriting copy is tier 4 and removing decoration is tier 3.

What changed is only what was broken or untrue: the `Create Next App` title, the Lovable badge, `href="#"` links, lorem ipsum, a frozen copyright, body text that failed 4.5:1, a missing focus ring, and then the fabricated proof (five stock avatars claiming 10,000 developers, the Acme Corp logo bar, the invented stat row, a bank-level-security claim with no security page).

Put the first two screenshots side by side and they look almost the same. **That is the guarantee working.** The page is no longer lying to anyone or leaking its toolchain, and nobody's design got overruled.

## The mistake this example caught

The first version of `hero-clean.html` chased specificity into verbosity. Its headline ran eleven words across three rendered lines, the subhead ran two sentences, and every feature card carried a full paragraph.

| Version | Headline + subhead + note |
|---|---|
| Before (slop) | 41 words |
| First clean attempt | **42 words** |
| Current clean | 22 words |

The first attempt removed no words at all, and it read denser than the slop because of the three-line headline. Every claim in it was true, and it was still worse.

The fix was to reach for a concrete noun instead of a longer sentence. "Figma says #6366F1. Your CSS says #635BFF." states the entire problem in seven tokens, where the earlier version needed a paragraph. `references/clean-pass.md` now carries this as a tier 4 rule: **specific does not mean longer**, and a rewrite that raises the word count has failed even when every claim is verifiable.

## The point of the example

**The design system is unchanged between them.** Both use Inter, a `#0a0a0a` ground, an indigo accent, 12px and 16px radii, a centered single-column layout, and the same three-card grid. No typeface, no hue family, no radius and no layout structure changed.

One qualifier, so the claim stays honest: the button and logo fills went from the `linear-gradient(135deg, #667eea, #764ba2)` stock gradient to solid `#6366f1`. That is tier 3 flattening a decorative gradient (#73), not a palette decision. The hue family is the same, and a redesign would replace it outright.

Every difference is an artifact removed, a falsehood corrected, decoration deleted, or craft added. The after page is still recognizably the same product in the same visual language, and it no longer contains evidence that a machine assembled it.

That gap it does *not* close, namely that the typeface and palette are still framework defaults, is exactly what tier 5 and a redesign are for. This is the honest ceiling of a clean pass.

## Every change, by tier

### Tier 1, ESSENTIAL (cannot make the site worse)
- `<title>Create Next App</title>` becomes a real title (#259)
- `<link rel="icon" href="/vite.svg">` removed (#260)
- "Edit with Lovable" badge removed (#252)
- Every `href="#"` becomes a real route (#269)
- `hello@example.com` becomes a monitored address (#248)
- Lorem ipsum removed from the footer (#248)
- `© 2024` corrected (#250)
- Body text `#71717a` on `#0a0a0a` raised to `#a1a1aa`, which passes 4.5:1 (#68)
- `:focus-visible` ring added, since there was none (#279)
- Meta description and Open Graph tags added (#265, #266)

After tier 1 alone, the page still looks like the before screenshot. That is the guarantee.

### Tier 2, HONEST (needs facts from you)
- "Loved by 10,000+ developers" with five stock avatars and five stars, removed (#5, #228)
- Logo bar reading Acme Corp, TechFlow, Globex, Initech, removed (#14)
- Stat row `10,000+ · 99.9% · 4.9/5 · 24/7`, removed (#16)
- "Bank-level security and enterprise-grade encryption" with no security page behind it, removed (#234)
- Replaced by one honest line: free under 200 variables, no card.

### Tier 3, QUIET (subtractive, visual)
- Two blurred purple glow orbs removed (#77)
- `✨ Announcing our Series A 🎉` pill with `animate-pulse` removed (#1, #175)
- Gradient keyword on "Workflow" reverted to the heading's own color (#107)
- `transform: scale(1.05)` on card hover replaced with a border-color shift (#166)
- Emoji feature icons ⚡🔒📊 removed (#144)
- `ALL-CAPS` eyebrows that only repeated the heading below, removed (#113)
- Colored glow `box-shadow` on the CTA and screenshot removed (#78)

### Tier 4, CRAFT (additive)
- Headline from "Supercharge Your Workflow" (#184) to "Figma says #6366F1. Your CSS says #635BFF." Seven tokens, two lines, and the problem is stated rather than described.
- Subhead from the 38-word echo-and-hedge formula (#190, #191) to nine words naming the mechanism
- CTAs from "Get Started" and "Learn More" (#216) to "Connect a Figma file" and "See a 90-second demo"
- Feature cards from the Blazing Fast / Secure / Analytics triad (#146, #222) to three mechanisms at 15 words or fewer each
- `text-wrap: balance` on headings, `pretty` on prose (C11, C12)
- `font-variant-numeric: tabular-nums` (C7)
- Underline craft with `text-underline-offset` (C45)
- Styled `::selection` in the existing accent (C38)
- Asymmetric transition timing, faster in than out (C53)
- Non-breaking space in "60 seconds" (C19)
- A stated limitation, a build stamp, and a real updated date (content specificity)

### Tier 5, DIRECTION (reported, not applied)
Still present in `hero-clean.html`, and correctly so:
- Inter as the only typeface (#94), with no pairing (#101)
- Untouched indigo `#6366f1` (#64) on a `#0a0a0a` dark-by-default ground (#65)
- Uniform 12 and 16px radii (#87)
- Centered single-column hero stack (#2) and a three-column feature grid (#26)

Fixing any one of these alone swaps a default for the next default. Together they need a committed direction, which is what `references/directions.md` and `references/derivation.md` are for.

## Regenerating screenshots

```bash
python -m http.server 8747 --directory examples
```

Then open `http://localhost:8747/hero-before.html` and `http://localhost:8747/hero-clean.html`.
