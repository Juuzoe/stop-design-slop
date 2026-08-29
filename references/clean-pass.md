# CLEAN pass: five tiers of AI removal

The default mode. It works in tiers, ordered by how much judgment each one needs and how much it can change. Run as deep as you want, and stop wherever you like.

| Tier | Name | What it does | Can it make the site worse? |
|---|---|---|---|
| **1** | **ESSENTIAL** | Fixes what is broken, leftover or missing | **No.** Under any taste, any direction. |
| **2** | **HONEST** | Removes false and fabricated content | No, but it needs facts from you |
| **3** | **QUIET** | Removes decorative additions | Only if you liked the decoration |
| **4** | **CRAFT** | Adds human detail | No, though it changes appearance a little |
| **5** | **DIRECTION** | The design system itself | Yes, if done piecemeal. Needs a redesign. |

**Default is tiers 1 to 4.** Tier 5 is reported and never applied, because fixing one system property in isolation is what produces incoherence. Run `redesign` and follow `method.md` for that.

```
/stop-design-slop              tiers 1-4 (default)
/stop-design-slop essential    tier 1 only
/stop-design-slop tier 2       tiers 1-2
/stop-design-slop redesign     tiers 1-4, then commit to a direction
```

---

## Tier 1: ESSENTIAL

**The guarantee: nothing here can make your site worse.** Every item is broken, left over from a generator, or missing. No item requires taste, brand knowledge or a design opinion. Nothing you intentionally designed gets touched.

Run this tier on anything, including a site you did not build, an hour before launch.

**Builder and framework leftovers.** The Lovable, Bolt, v0 or Replit badge (#252, #253). A preview subdomain serving production traffic (#254). The editor runtime script still loading (#255). Generator meta tags (#256). Tool-shaped asset paths (#257). `placeholder.svg` stubs (#258). A default page title such as "Create Next App" (#259). A framework favicon (#260). Scaffold package names (#261). A stock or blank 404 route (#263).

**Placeholder and pipeline residue.** Lorem ipsum, "Your Company", `example.com`, `[Insert X]`, `{{ }}` (#248). Raw LLM artifacts such as "Certainly! Here's a compelling headline" (#246). Markdown bleed-through, where `**bold**` renders as literal asterisks (#247). HTML comments left in the served markup (#274). Product name drift between pages (#249). A frozen copyright year (#250).

**Dead wiring.** `href="#"` links and links to pages that 404 (#269, #49). Social icons pointing at platform homepages or nowhere (#270). A contact form that shows a success toast and sends nothing (#271). A newsletter box with no provider behind it (#51).

**Broken at runtime.** Console errors and failed asset fetches on first paint (#277). Hydration warnings (#278). API keys or service keys exposed in the client bundle (#276), which is a security incident before it is a design tell.

**Missing accessibility.** No visible focus state, usually `outline: none` with no replacement (#279). Missing or nonsense alt text (#280). Redundant ARIA that harms screen readers (#281). A broken heading hierarchy (#282). Body text failing 4.5:1, most often `text-gray-500` on a near-black ground (#68). All of these are repairs, and raising text lightness is not a palette change.

**Missing metadata.** No meta description, or a duplicated one (#266). Absent Open Graph and Twitter tags (#265). No robots.txt or sitemap (#267).

**Performance repairs.** Multi-megabyte hero images with no `srcset` and no lazy loading (#283).

**Verification for this tier:** the rendered page should look the same, apart from a focus ring appearing on tab and body text gaining contrast. If anything else moved, it belongs to a later tier.

---

## Tier 2: HONEST

Removes content that is not true. It cannot make the site less accurate, but it does change what the page claims, so it needs facts from you.

**The rule: replace a fabrication with the true fact, or with nothing. Never with a different fabrication.**

Fabricated proof (#228 round-number herd claims, #229 implausible logo bars, #230 press bars with no coverage behind them, #231 unsourced star ratings, #232 invented percentages, #234 security theater with no security page). Placeholder company logos such as Acme Corp and Globex (#14). Invented stat banners (#16). Claims that contradict the product's visible stage, such as "Join 50,000+ users" on a waitlist (#17, #233). Synthetic testimonials, including stock and generated faces (#143, #235, #236, #237). Fake product imagery: dashboards with meaningless numbers (#139), rendered UI that was never built (#140), staged terminals running commands that do not work (#141). AI-image artifacts that make the picture itself a lie: garbled pseudo-text (#122), hand anatomy failures (#123), impossible background geometry (#126). Decorative integration grids for integrations that do not exist (#24). Template-tainted legal pages naming the wrong company (#251).

**Where honest silence beats a replacement:** a pre-launch product with no customers should say so. "In private beta with 12 teams since May" outperforms an invented number, and it cannot be falsified by a visitor.

---

## Tier 3: QUIET

Removes decoration that was added on top. Subtractive only, so it never breaks coherence, but it does change how the page looks. Run it when the ambient motion and glow are the thing making the page feel generated.

**Ambient motion.** Scroll reveals on every section (#154 to #158). The hero load cascade (#159). Preloaders on a brochure site (#160). Word-by-word scroll-linked text (#161). Scroll-jacking and smooth-scroll hijack (#162, #163). Parallax layers (#164). The bouncing chevron (#165). Particles and starfields (#170). Animated aurora blobs (#171). Floating and bobbing shapes (#172). Border beams (#173). Shimmer sweeps (#174). Pulsing badges and CTAs (#175). Typewriter and rotating headlines (#176, #177). Animated count-ups (#178). Generic Lottie clips (#179). Infinite logo and testimonial marquees, which become static rows (#13, #19).

**Hover and cursor effects.** `hover:scale-105` on everything, especially non-clickable elements (#166). 3D tilt cards (#167). Cursor-tracking spotlights (#168). Custom cursor followers (#169).

**Decorative surface effects.** Free-floating blurred glow orbs (#77). Radial spotlight haze behind headings (#79). A glow clipped flat by `overflow: hidden`, which is a bug (#80). Noise overlays sitting on top of content and hurting legibility (#83).

**Decorative type and icon treatments.** The gradient keyword, which reverts to the heading's existing color (#107). Emoji used as feature icons (#144). Mixed icon styles unified into the set already most used (#147). Gradient-filled icons set back to `currentColor` (#149). Eyebrow labels that only repeat the heading below (#113).

**Always add back when you remove motion:** real hover, focus, active and disabled states (#183), plus `prefers-reduced-motion` handling (#182). Stripping animation without adding state feedback leaves the page feeling dead, which is its own failure.

---

## Tier 4: CRAFT

Adds the human detail. Purely additive, entirely local, and it needs no direction because every value comes from what the site already uses.

This tier is what stops a clean pass trending toward bland. Removal lowers the Slop Score; this is what raises the Commitment Score.

From `craft-details.md`: C1 real punctuation (curly quotes, true dashes, real ellipsis). C4 `font-synthesis: none`. C7 tabular figures on anything numeric. C11 `text-wrap: balance` on headings. C12 `text-wrap: pretty` on prose. C14 tracking tuned by size, using the face already loaded. C20 a measured measure at 66ch. C38 a styled `::selection` in the existing accent. C39 a focus ring in the existing brand color. C45 underline craft on links. C52 five genuinely distinct control states. C63 and C64 real empty and error states.

**Content specificity**, which is unfakeable and costs nothing: real dates in `<time>`, a "last updated" wired to git, a build stamp, image credits, alt text with voice, one honest limitation stated next to the feature it affects.

### Specific does not mean longer

The failure mode of this tier, and the easiest one to fall into. Chasing specificity, you replace a vague three-word headline with a precise eleven-word one, add a qualifying subhead, then pad each feature card with a full explanation. Every word is now true, and the hero is worse than the slop it replaced.

**A hero has a length budget, and truth does not exempt you from it.** Slop copy is short and empty. The fix is short and full, never long and full.

Rules for this tier:

- **Headline: 8 words or fewer**, holding to two rendered lines at display size. A headline wrapping to three lines has already lost.
- **Subhead: one sentence.** If it needs two, the headline is doing the wrong job.
- **Feature blurb: 15 words or fewer.** One mechanism each, not an explanation of it.
- **Count words before and after.** A rewrite that raises the total has failed even when every claim in it is verifiable.
- Reach for a concrete noun, a number or a name instead of a longer sentence. "Figma says #6366F1. Your CSS says #635BFF." carries more than a paragraph about token drift, in seven words.

This repo made the mistake on its own example. The first cleaned hero ran 42 words across headline, subhead and note, against 41 in the slop original: no reduction at all, and it read denser because the headline wrapped to three lines. The current version says more in 22. See `examples/README.md`.

**Copy rewrites** belong here, and they carry more signal per edit than anything else in the CLEAN pass, because readers detect slop through language faster than through layout. Work the blacklist in `copy-content.md`: headline formulas (#184 to #192), AI sentence constructions (#193 to #203), the word list (#204 to #215), generic CTAs rewritten to name the actual action (#216), exclamation saturation (#218), emoji in headings (#219), feature-card copy given specifics (#222), generic section headings made into assertions (#224), and default empty-state and 404 microcopy (#221).

---

## Tier 5: DIRECTION (reported, never applied)

Everything that cannot be fixed coherently one piece at a time.

Typeface, pairing, type scale, weight system (#94 to #106, #109 to #112). Palette, gradients, glass, glow as a system, radius scale, shadow system, dark-mode strategy (#64 to #67, #69 to #76, #81, #82, #84 to #93). Hero composition, grid structure, section order, spacing rhythm, symmetry, container widths, nav and footer architecture (#1 to #12, #15, #18, #20 to #23, #25 to #48, #50, #52 to #63). The icon treatment system (#145, #146) and imagery art direction (#128 to #138). The motion system as a whole, meaning one house easing curve (#181). The framework's default palette still reachable in config (#272).

Report these grouped by what a direction would decide:

```markdown
## Needs a direction (not changed)

**Type** (#94 Inter throughout, #101 no pairing, #103 flat scale)
A direction sets a display face, a pairing and a scale ratio.
Fixing #94 alone swaps one default for another.

**Color** (#64 indigo-500, #72 blue-to-purple gradient, #90 shadcn defaults)
A direction derives an owned hue and a 12-step ramp.
Changing the accent alone leaves neutrals and semantics mismatched.

**Composition** (#2 centered hero stack, #26 icon-tile grid, #38 total symmetry)
A direction sets a grid, a focal point and one tension move.

Run `/stop-design-slop redesign` to do this properly.
```

---

## The constraint that keeps tiers 1 to 4 safe

**No tier below 5 may edit theme tokens, `font-family`, the palette, the radius or shadow scale, or layout structure.**

Incoherence comes from changing one system property in isolation, so CLEAN changes none of them. This is what makes it safe on a site somebody else designed.

**Verify it held:** the diff should contain no change to any of those. If one appears, it escaped scope, so revert it and move the entry into the tier 5 report.

Then check regressions as usual: contrast, focus visibility, page weight, functionality, mobile layout.

## Expected scores

CLEAN drops the Slop Score a long way and raises the Commitment Score only a little, from tier 4. It will not reach the redesign ship gate, and that is correct. CLEAN removes the evidence that a machine made the page. A direction is what makes it look like a person chose it.

Report both numbers and name the gap a redesign would close.

## Worked example

`examples/hero-before.html` and `examples/hero-clean.html` in this repo are the same page before and after tiers 1 to 4. The typeface, background color, accent, border radius and layout are byte-identical between them. Every difference is an artifact removed, a falsehood corrected, decoration deleted or craft added.
