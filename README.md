<div align="center">

# stop-design-slop

**An agent skill that makes a website stop looking AI-generated.**

Strips the AI fingerprints without restyling your site. Rebuilds around a committed art direction only if you ask.

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude_Code-ready-6b4bff.svg)](#install)
[![Codex](https://img.shields.io/badge/Codex-ready-0b7285.svg)](#install)
[![Catalog](https://img.shields.io/badge/tells-284-orange.svg)](#the-diagnostic-half)
[![Directions](https://img.shields.io/badge/directions-13-blue.svg)](#the-generative-half)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

</div>

---

Open five new startup sites and you meet the same page. A pill badge with a sparkle floats above a centered hero whose headline has exactly one gradient word. Three feature cards sit below, each holding a Lucide icon in a small indigo square. The trust bar claims 10,000+ teams on a domain registered last Tuesday, and the whole thing glows purple over `#0a0a0a` in Inter.

Your visitors recognize that page in about five seconds and stop believing anything below the fold.

## Two jobs, and only one of them is safe piecemeal

"This looks AI-generated" hides two different requests, and mixing them is what breaks pages.

**Artifacts are always safe to remove.** A Lovable badge, a "Create Next App" tab title, lorem ipsum, a fabricated testimonial, a dead `href="#"`, a six-fingered hero image. These are wrong whatever your design direction, so deleting them can only help. That is the **CLEAN pass**, and it runs by default.

**Style defaults are not.** Inter, indigo-500, the centered hero, `rounded-xl` on everything. Each is a *choice* that happens to be the statistical average, and changing one in isolation produces incoherence, which reads worse than consistent genericness. These need an art direction, so CLEAN reports them and leaves them alone.

```text
/stop-design-slop            → CLEAN. Strips artifacts. Never touches your design system.
/stop-design-slop redesign   → Commits to a direction and rebuilds from tokens.
```

CLEAN may not edit theme tokens, `font-family`, the palette, the radius or shadow scale, or layout structure. That single constraint is what makes it safe to run on a site somebody else designed, or an hour before launch.

## Why deleting the style tells makes it worse

v1 of this skill was a 284-item catalog of AI design tells, and it told the agent to fix them all one at a time, style defaults included. A user ran it and reported the result looked **more** AI-generated than the original. They were right, for four reasons now documented in [method.md](references/method.md).

**Coverage.** A 284-item ban list constrains 284 decisions. A page makes thousands: line-height, measure, hover easing, focus ring, caption style, table rules, empty states. Every decision the list does not name reverts to the model's default. Silence in a design system *is* the default, so a subtractive audit can never win however long it grows.

**Negation promotes the runner-up.** Banning the most common option does not flatten the distribution, it promotes second place. Everyone running the same ban list lands on the same second choice. "Don't use Inter" arrives at Space Grotesk, which is tell #95. "Don't center the hero" arrives at the 50/50 split, which is tell #7 and still symmetrical. The escape hatch has a spec sheet.

**Patchwork.** Thirty tells fixed as thirty independent edits produce thirty unrelated decisions. The generic original was at least coherent: one font, one radius, one accent, applied everywhere. Afterward you have a different font, three radii, and a flat section beside a rounded one. Incoherence reads as broken, and broken is worse than generic.

**The metric was wrong.** A score that only counts tells has its optimum at a flat gray page with a system font and no motion. Zero tells, zero decisions. Absence of decisions is itself the AI signature.

So style tells stopped driving the fix. In CLEAN they are reported rather than applied. In REDESIGN they appear as diagnosis before the work and as lint assertions after it, while a committed direction sits in between.

## What CLEAN does

```
DIAGNOSE + CLASSIFY  →  FIX A  →  FIX B  →  ADD CRAFT  →  REPORT C  →  VERIFY
```

Every tell is classified. **A** is an artifact, wrong whatever the design. **B** is local, fixable in place without touching a system token: copy rewrites, alt text, deleting an ambient animation, capping line length. **C** is systemic and needs a direction.

CLEAN fixes A and B, then adds the craft details that need no direction (real punctuation, `text-wrap: balance`, tracking tuned by size, a focus ring in your existing brand color, tabular figures, real empty and error states), then hands back a report of C.

That last part matters: pairing every removal with a local addition is what stops a clean pass trending toward bland. The site gains human signal while keeping the look it already had. Roughly 60% of the catalog is actionable this way, and it is the highest-trust 60%: artifacts, fabrications, copy, motion noise and accessibility. Copy alone often moves a page further than any visual change, since readers detect slop through language faster than through layout.

Full classification per catalog is in [clean-pass.md](references/clean-pass.md).

## What REDESIGN does

```
DIAGNOSE  →  BRIEF  →  SPEC  →  REBUILD  →  LINT  →  JUDGE
```

The deliverable is a **`DESIGN.md`** written into your project: 20 to 50 lines, every slot filled with an exact value, no adjectives. Type, color, geometry, space, motion, imagery, copy, plus five named commitments (the focal point, the one element that breaks the container, a signature device repeated in three roles, the decision competitors would never make, and one deliberate exception to your own system).

An empty line in that spec is a decision handed back to the model, which is how genericness gets in.

Then the rebuild happens at the token layer as one atomic change, because coherence cannot be assembled from scattered component edits. Defaults are made **unreachable** rather than discouraged: you define Tailwind's `colors:` rather than `extend:` so the framework palette cannot be referenced at all. Renaming `indigo` to `primary` changes nothing anybody can see.

## Install

An open-standard `SKILL.md` folder, so it drops into any agent that reads skills.

<details open>
<summary><b>Claude Code</b></summary>

```bash
git clone https://github.com/Juuzoe/stop-design-slop ~/.claude/skills/stop-design-slop
```
```powershell
git clone https://github.com/Juuzoe/stop-design-slop "$env:USERPROFILE\.claude\skills\stop-design-slop"
```
Invoke with `/stop-design-slop`.
</details>

<details open>
<summary><b>Codex</b></summary>

```bash
git clone https://github.com/Juuzoe/stop-design-slop ~/.codex/skills/stop-design-slop
```
```powershell
git clone https://github.com/Juuzoe/stop-design-slop "$env:USERPROFILE\.codex\skills\stop-design-slop"
```
Restart Codex, then run `/skills` or type `$stop-design-slop`. For a team-shared install, clone into `.agents/skills/stop-design-slop` at the repo root.
</details>

<details>
<summary><b>Cursor, Gemini CLI, other agents</b></summary>

Clone anywhere and point the agent at `SKILL.md`. No tool is a hard requirement; see [Agent compatibility](SKILL.md#agent-compatibility).
</details>

## Use

```text
/stop-design-slop https://yoursite.com    CLEAN: strip artifacts, keep the design
/stop-design-slop                         CLEAN, on the current project
/stop-design-slop redesign                commit to a direction and rebuild from tokens
/stop-design-slop audit-only              diagnosis + plan, changes nothing
/stop-design-slop build                   prevention mode: spec before any code exists
/stop-design-slop quick                   the 63 instant tells, fast diagnosis only
```

The skill will not escalate to a redesign on its own. It finishes the clean pass, reports what a direction would fix, and leaves the decision to you.

In Codex, swap the leading `/` for `$`. In any agent you can also just say "this looks AI-generated, fix it."

## The generative half

**[13 art directions](references/directions.md)**, each specified far enough to build from: display and body typefaces by real name (with free, self-hostable options), tracking and leading conventions, palette strategy with hex values, radius stance, spacing rhythm, the layout signature that identifies the direction, imagery rules, motion policy, copy voice, real example sites, and the specific way each one fails.

Swiss International · Editorial/Magazine · Technical Documentation · Terminal/Code Brutalism · Brutalist/Raw HTML · Neo-Vintage/Print Revival · Warm Organic · High-Contrast Fashion · Utilitarian Tool · Neubrutalist/Toy · Archival Index · Scientific/Data-Forward · Cinematic Dark · Libre/Experimental

Directions are chosen through three filters so different projects land in different places: your brand attributes, what your competitors already occupy, and **what your content can actually support**. That third filter kills the most candidates. Fashion editorial dies without excellent photography; data-forward dies without real data. Picking a direction your content cannot feed produces an empty template.

**[Derivation math](references/derivation.md)** for everything a direction leaves open, executable without taste:

- Source a hue from the brand's own artifact or material, keeping only the hue angle and re-deriving lightness and chroma. Includes a competitive hue audit that tells you mechanically whether your color is invisible.
- Compute the hue's physical chroma ceiling, which decides whether your brand color can carry white text at all. Yellow and green peak at L 0.88 and cannot. Violet peaks at 0.485 and cannot carry black.
- Build a 12-step OKLCH ramp where each step has a stated job, using lightness and chroma ladders reverse-derived from hand-tuned production scales.
- Solve contrast rather than eyeballing it, targeting APCA and asserting WCAG as a hard gate, since the two disagree and you need both.
- Hold saturation while fixing contrast by bisecting lightness at the chroma ceiling. In the worked example that costs 8% of chroma where desaturating would cost 40%.
- Pick and pair typefaces against measured gates: x-height ratio, aperture, stroke contrast, disambiguation of `Il1`, plus the pairing strategies and the one prohibited combination.
- Derive spacing from the type scale rather than inventing values, and radius from the typeface's own geometry.
- Build layered, hue-matched shadows instead of `rgba(0,0,0,.1)`.

**[64 craft details](references/craft-details.md)** (C1–C64) that signal a human hand, each implementable, most in one line. Real punctuation, hanging punctuation, true small caps, tabular figures, `text-wrap: balance` and `pretty`, tracking tuned by size, optical alignment, subgrid card alignment, brand focus rings, styled `::selection`, underline craft, five genuinely distinct control states, empty and error states, grain and material, and the deliberate irregularities that prove somebody chose. Ranked by signal per hour at the end.

**[The art-direction process](references/art-direction.md)**: perception brief, competitor mapping, attribute disambiguation (the step that decides whether you diverge or converge), element-decomposed competitive audit, white-space plot, anti-mood board, cross-category reference import, and three-tier token propagation.

## The diagnostic half

Seven catalogs, 284 numbered tells, used for diagnosis and lint rather than as a repair list.

| Catalog | Tells | For example |
|---|---|---|
| [Structure & layout](references/structure-layout.md) | #1–63 | #1 the "✨ Announcing" pill badge · #10 the hero→logos→features→pricing→FAQ conveyor belt |
| [Color & effects](references/color-effects.md) | #64–93 | #64 untouched indigo-500 · #77 blurred glow orbs |
| [Typography](references/typography.md) | #94–121 | #94 Inter as the only typeface · #107 gradient keyword via `bg-clip-text` |
| [Imagery & icons](references/imagery-icons.md) | #122–153 | #123 six-fingered hero art · #144 emoji as feature icons |
| [Motion & interaction](references/motion-interaction.md) | #154–183 | #154 fade-up on every section · #170 particle backgrounds |
| [Copy & content](references/copy-content.md) | #184–251 | #184 "Supercharge Your Workflow" · #228 "Trusted by 10,000+ teams" |
| [Code & meta](references/code-meta-tells.md) | #252–284 | #252 the Lovable badge · #271 contact forms wired to nothing |

Each catalog ends with a **VOCAB block** of exact greppable strings, so diagnosis works on source before anything renders.

## Scoring, on two axes

A single slop score rewards deletion, so the skill scores commitment too.

```
Slop Score       = 3×instant + 2×strong + 1×mild
Commitment Score = filled, propagated, nameable decisions
```

| Slop | Commitment | Verdict |
|---|---|---|
| high | low | Generic template. The starting point. |
| high | high | Loud but derivative. Fix the tells. |
| **low** | **low** | **Bland. The failure this skill exists to prevent.** |
| low | high | Ship it. |

## What it will not do

- **Every removal gets a replacement.** Name the job an element does and keep that job covered.
- **Never strip all three interaction signifiers.** Shadow, radius and fill are slop tells *and* the primary clickability cues. Remove all three and the page reads unfinished on top of bland, so an interactive element keeps at least two of border, fill, and a hover or focus delta.
- **Conventions stay.** Nav, forms, hierarchy and checkout are load-bearing. Divergence goes into type, color, section order, imagery, microcopy and motion.
- **Accessibility outranks aesthetics**, in every conflict.
- **Your brand stays yours.** If the purple is the actual brand color, it stays, used with more intention.
- **Restraint over reinvention.** Swinging to brutalism because "AI can't do that" produces a different template.

## Already ran a de-slop that made things worse?

Revert to the pre-audit commit rather than repairing forward. The generic original is a better base because it is internally consistent, so token changes propagate predictably through it. Patchwork has no consistent base to propagate from. Keep the diagnosis from the failed run, since detection was never the problem, then write the spec and rebuild. Full recovery steps are in [method.md](references/method.md).

## FAQ

**Will every site using this end up looking the same?** That is the real risk, and four guards exist for it: direction is selected by brand inputs rather than preference, the palette derives from your own source material, the signature move is invented per project, and the skill refuses to run on defaults. If a skill produces one non-slop for everybody, it has manufactured a new default inside one cycle.

**Does it need a browser?** Rendering helps. Without one the skill audits the code, runs the greppable sweep, and states which categories it could not verify rather than guessing.

**My site came out of v0, Lovable or Bolt.** That is the main use case. Catalog 7 strips builder fingerprints and the spec keeps the next build clean.

**Is this anti-AI?** It is anti-default. Build with whatever you like; the skill checks that the result looks like somebody made a decision.

**Can I run it on a site I don't own the design of?** Yes, that is what CLEAN is for. It cannot edit theme tokens, fonts, the palette, the radius scale or layout, so the design system you inherited comes out unchanged.

**Which mode do I want?** CLEAN if the design is fine and the AI fingerprints are the problem, or if you ship soon. REDESIGN when the clean pass finishes and the 5-second test still says "generic", the Commitment Score is under 3, or the lineup test cannot pick your site out of five competitors.

## Contributing

New tells, false positives, better fixes, and additional directions are all welcome. [CONTRIBUTING.md](CONTRIBUTING.md) has the entry format and the severity rubric.

A ⭐ helps other people find this before they ship the pill badge.

## License

[MIT](LICENSE). Use it, fork it, ship it.
