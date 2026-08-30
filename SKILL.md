---
name: stop-design-slop
description: Strip the AI fingerprints from a website without restyling it, and optionally rebuild it around a committed art direction. Use when the user says a site looks AI-generated, generic, template-y, or "like every other SaaS page"; asks to de-slop, de-AI, humanize, clean up, or "make it not look AI"; wants an AI-slop audit or slop score; needs builder watermarks, placeholder text or fabricated testimonials removed; is redesigning an existing site; or is starting a new site, landing page or app and wants it distinctive from the first commit. Defaults to a safe clean pass that never touches the design system; a redesign takes an explicit word. Carries a 286-tell diagnostic catalog, 13 specified art directions, color and type derivation math, and 64 craft details.
---

# stop-design-slop

## Read this before anything else

Two different jobs hide behind "this looks AI-generated", and mixing them is what breaks pages.

**Removing artifacts is always safe.** A builder watermark, lorem ipsum, a fabricated testimonial, a dead link, a six-fingered hero image: these are wrong whatever the design direction, and deleting them can only improve the site. This is the CLEAN pass, and it is the default.

**Restyling is not safe piecemeal.** The typeface, the palette, the radius scale, the hero composition: each is a *choice* that happens to be modal. Change one in isolation and you get incoherence, which reads worse than consistent genericness. These need a direction, so CLEAN reports them and leaves them alone.

**Removing style defaults one at a time does not produce good design. It produces bland design, which reads as AI-generated too.**

An earlier version of this skill prescribed exactly that, and it made pages worse for reasons documented in `references/method.md`:

- A 284-item ban list constrains 284 decisions out of the thousands a page makes. Every unconstrained decision reverts to the model's default.
- Banning the most common option promotes the second most common one. Everyone lands on the same runner-up, so anti-slop output ends up more uniform than the slop it replaced.
- Thirty tells fixed as thirty independent edits produce thirty unrelated decisions. The generic original was at least coherent, and incoherence reads as broken.
- Optimizing for the fewest tells converges on a flat gray page with a system font. Zero tells, zero decisions.

**So in REDESIGN, the tells never drive the fix.** They appear as diagnosis before the work and as lint assertions after it, while a committed direction and a token-layer rebuild sit in between. In CLEAN, the tells drive only the artifact and content fixes, which carry no such risk because they change nothing system-wide.

If you are here to repair a page a previous de-slop pass damaged, read the recovery section of `references/method.md` first. Reverting usually beats repairing forward.

## Modes

**The default is CLEAN, which does not restyle the site.** A redesign is a bigger commitment than most people want when they say a page looks AI-generated, so it takes an explicit word.

| Invocation | Mode |
|---|---|
| `/stop-design-slop <url>` or bare | **CLEAN**, tiers 1 to 4 (default) |
| `essential` in args | **Tier 1 only.** Cannot make the site worse under any taste. |
| `tier N` in args | Tiers 1 through N |
| `redesign` / `rebuild` / `direction` in args | Tiers 1 to 4, then commit to a direction and rebuild from tokens |
| `build` in args, or invoked while creating new UI | **PREVENT**: write the spec before any code exists |
| `audit-only` / `report` in args | Diagnose and score only, change no files |
| `quick` in args | The 63 `instant` tells, fast diagnosis |
| `copy` / `visual` / `code` in args | Scope the diagnosis to those catalogs |

Infer between CLEAN and PREVENT rather than asking: existing UI goes to CLEAN, a blank slate goes to PREVENT. **Never escalate to a redesign on your own.** Finish the clean pass, report what a direction would fix, and let the user decide.

### The tiers

Read `references/clean-pass.md` for the per-tell breakdown.

| Tier | Name | What it does | Can it make the site worse? |
|---|---|---|---|
| **1** | **ESSENTIAL** | Fixes what is broken, leftover or missing: builder badges, default titles, placeholder text, dead links, ghost forms, console errors, missing focus and alt text, failing contrast, absent meta | **No.** Under any taste, any direction. |
| **2** | **HONEST** | Removes false content: fabricated testimonials, invented stats, placeholder logo bars, unsourced ratings, AI-image artifacts | No, but it needs facts from you |
| **3** | **QUIET** | Removes decorative additions: ambient motion, particles, glow orbs, marquees, count-ups, hover-scale, gradient keywords, emoji icons | Only if you liked the decoration |
| **4** | **CRAFT** | Adds human detail: real punctuation, `text-wrap`, tracking by size, focus ring in the existing accent, tabular figures, real states, specific copy | No, though it changes appearance a little |
| **5** | **DIRECTION** | Typeface, palette, radius scale, hero composition, section order | Yes, piecemeal. Reported, never applied. |

Tier 4 is what stops a clean pass trending toward bland: removal lowers the Slop Score, and craft raises the Commitment Score.

**The constraint that keeps tiers 1 to 4 safe: no tier below 5 may edit theme tokens, `font-family`, the palette, the radius or shadow scale, or layout structure.** Incoherence comes from changing one system property in isolation, so CLEAN changes none of them. Verify the diff contains no such change before finishing.

## Files

Read `method.md` first, always. Then read what your phase needs.

| File | Purpose |
|---|---|
| `references/clean-pass.md` | **The default mode.** Five tiers of removal, per-tell breakdown, what CLEAN may not touch, the tier-5 report |
| `references/method.md` | Why removal-only fails, the corrected model, the REDESIGN workflow, the `DESIGN.md` template, dual scoring |
| `references/redesign.md` | **Tier 5 execution.** The design read, three dials, the category-reflex check, the build-against-bans list, and the pre-flight checklist |
| `references/art-direction.md` | The process that produces a commitment: brief, attribute disambiguation, competitive audit, divergence, propagation |
| `references/directions.md` | 13 fully-specified directions with real typefaces and example sites, plus the attribute map and a free type shelf |
| `references/derivation.md` | Executable math: hue sourcing, OKLCH ramps, APCA contrast solving, type selection and pairing, scale and spacing, radius and shadow systems |
| `references/craft-details.md` | 64 implementable details (C1–C64) that signal a human hand |
| `references/structure-layout.md` | Tells #1–63: architecture, heroes, sections, grids, spacing, nav, footer, IA, mobile |
| `references/color-effects.md` | Tells #64–93: palettes, gradients, glow, glass, borders, radius, shadows |
| `references/typography.md` | Tells #94–121: font choice, pairing, hierarchy, headline styling, casing |
| `references/imagery-icons.md` | Tells #122–153: AI-image artifacts, stock illustration, icons, logos |
| `references/motion-interaction.md` | Tells #154–183: scroll reveals, hover effects, ambient loops, motion systems |
| `references/copy-content.md` | Tells #184–251: headline formulas, word blacklist, trust claims, testimonials |
| `references/code-meta-tells.md` | Tells #252–284, #286: builder watermarks, framework leftovers, dead wiring, a11y |

286 tells (64 instant, 154 strong, 68 mild) and 64 craft details.

## CLEAN workflow (default)

```
DIAGNOSE + TIER  →  T1 ESSENTIAL  →  T2 HONEST  →  T3 QUIET  →  T4 CRAFT  →  REPORT T5  →  VERIFY
```

Full detail in `references/clean-pass.md`. Diagnose as below, assigning each hit a tier. Work the tiers in order and stop at whichever the user asked for. Report tier 5 rather than applying it, then verify no diff touched a system token.

A worked example lives in `examples/`: `hero-before.html` and `hero-clean.html` are the same page before and after tiers 1 to 4, with typeface, background, accent, radius and layout identical between them.

## REDESIGN workflow (only when asked)

```
DIAGNOSE  →  BRIEF  →  SPEC  →  REBUILD  →  LINT  →  JUDGE
```

**Read `references/redesign.md` before building.** It carries the design read, the three dials, the two-altitude category-reflex check, and the ban list that catches what survives a clean pass: three equal feature cards, div-based fake product UI, gradient text, eyebrows on every section, side-stripe borders, ghost cards, over-rounded corners. `examples/hero-redesign.html` is a worked result.

### 1. DIAGNOSE (both modes)

Capture the current state, then walk the tell catalogs against it. Record each hit as `#N, where it appears, severity`, plus its tier in CLEAN mode. Record what already works as a do-not-touch list.

Capture with whatever the host provides. For a live URL: screenshot full-height at desktop width and again at ~375px, extract page text, check the tab title and favicon. With no browser: fetch the HTML and CSS, audit those, ask the user for screenshots, and state which visual tells you could not verify. For a codebase: read entry pages, global CSS and theme config, layout components, then run the VOCAB grep sweep at the end of each catalog. Judge the rendered page whenever you can.

Run the **5-second test** explicitly: describe your first impression of the desktop screenshot in one sentence, before analysis. If it contains "generic", "template" or a tool name, that sentence is the headline of the report.

Stop here in `audit-only` mode, after the findings and the plan.

**In CLEAN mode, stop reading here and follow `clean-pass.md`.** The steps below restyle the site and belong to REDESIGN.

### 2. BRIEF

Run `art-direction.md`. It ends with a one-sentence concept, a named audience, three to five disambiguated attributes, an exclusion list, and a chosen direction from `directions.md`.

**Refuse to proceed without a concept and an audience.** Art direction is what makes a thousand small choices agree. With no concept, they agree by defaulting. If the user will not supply one, generate three candidate directions and force a pick.

Select the direction through the three filters in `directions.md`: your attributes, what competitors already occupy, and what your content can actually support. The third filter kills the most candidates, and ignoring it produces an empty template.

### 3. SPEC

Write `DESIGN.md` into the project using the template in `method.md`. Twenty to fifty lines, exact values, no adjectives. Derive the values that must be project-specific using `derivation.md`: source the hue from the brand's own material, solve contrast rather than eyeballing it, pick type against the measured gates.

**An empty line in the spec is a decision handed back to the model.** Fill every one.

The spec includes five named commitments: the focal point, the one tension move, a signature asset appearing in three roles, the decision competitors would not make, and one deliberate exception to your own system.

This file is a deliverable. The user edits it, and it governs every future change.

### 4. REBUILD

Token layer first, as one atomic change, then components, then content, then craft.

**Make defaults unreachable rather than discouraged.** In Tailwind, define `colors:` rather than `extend:` so the framework palette cannot be referenced. Renaming `indigo` to `primary` changes nothing perceptual.

Order: type tokens → color tokens → geometry tokens → space and scale → motion tokens → components → content and copy → craft details from `craft-details.md`.

Never scatter edits across components before the tokens agree. That is the patchwork failure.

### 5. LINT

Machine-checkable assertions, run in CI. Warnings first, then errors.

Hex values outside the allowlist. Banned utility classes. Off-scale spacing. Banned copy openers. Computed contrast below 4.5:1. Raw elements where a system component exists.

Rules must be checkable by the agent against its own output. An instruction the agent cannot verify produces over-correction rather than compliance, so anything requiring "look at the render" belongs in the JUDGE phase instead.

### 6. JUDGE

Write a rubric for this brief describing what good looks like, then evaluate the rendered page against it. A checklist cannot govern generation; critique defines quality without demanding exactness, and it evaluates the render rather than the source.

Re-screenshot desktop and mobile, rerun the 5-second test, and score both axes.

## Scoring

```
Slop Score       = 3×instant + 2×strong + 1×mild        (lower is better)
Commitment Score = filled, propagated, nameable decisions (higher is better)
```

| Slop | Commitment | Verdict |
|---|---|---|
| high | low | Generic template. The starting point. |
| high | high | Loud but derivative. Fix the tells. |
| **low** | **low** | **Bland. The failure this skill exists to prevent.** |
| low | high | Ship it. |

**REDESIGN ship gate** needs both: Slop Score 0 to 8, Commitment Score 5 or more, every mandatory positive from `method.md` present, and no regression in contrast, focus visibility, page weight, functionality or mobile layout.

**CLEAN expects a different result.** The Slop Score falls a long way while the Commitment Score rises only a little, from the craft additions. It will not reach the redesign gate, and that is correct: CLEAN removes the evidence that a machine made the page, while a direction is what makes it look like a person chose it. Report both numbers and say which gap a redesign would close.

## Guardrails

- **Every removal gets a replacement.** Name the job an element does (orient, persuade, prove, convert) and keep that job covered.
- **Never strip all three interaction signifiers.** Shadow, radius and fill are slop tells and also the primary clickability cues. An interactive element keeps at least two of border, fill, and a hover or focus delta. Removing all three makes the page read unfinished as well as bland.
- **Conventions stay.** Nav, forms, hierarchy and checkout are load-bearing. Diverge on type, color, section order, imagery, microcopy and motion instead.
- **Accessibility outranks aesthetics.** No fix may reduce contrast, remove focus states, shrink tap targets, or ignore `prefers-reduced-motion`.
- **The brand stays the brand.** If the purple is the company's actual color, it stays, used with more intention.
- **Restraint over reinvention.** Anti-slop is a direction, not a style. Swinging to brutalism because "AI can't do that" produces a different template.
- **Parameterize per project.** If every user of this skill produces the same non-slop, the skill has manufactured a new default. Derive the palette from the project's own material and invent the signature move per project.
- **Keep receipts.** List what you kept and why, so a reviewer sees the restraint was deliberate.

## Agent compatibility

Plain Markdown against the open `SKILL.md` standard, requiring no tool by name. Runs in Claude Code, Codex, Cursor and Gemini CLI.

| Host | Capture with |
|---|---|
| **Claude Code** | Browser pane (`preview_start`/`navigate`, `computer` screenshot, `resize_window`, `get_page_text`), plus Glob, Read and Grep |
| **Codex** | Its browser and web tools where enabled, otherwise fetch the HTML and request screenshots. Shell tools cover the VOCAB sweep |
| **Any other agent** | Whatever fetch, screenshot and search tools exist, falling back to the no-browser path |

Degrade honestly. Run the catalog against what you can see and label the untested categories rather than guessing.

## Related skills

Use when the host provides them, skip silently otherwise.
- `design-taste` / `frontend-design`: additional positive design direction.
- `stop-slop` (Anthropic): de-AI-ing long-form prose. Use it on the site's blog and docs. UI copy is covered in `copy-content.md`.
