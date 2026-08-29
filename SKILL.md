---
name: stop-design-slop
description: Make a website stop looking AI-generated, by committing to a specific art direction and rebuilding from tokens rather than by deleting tells. Use when the user says a site looks AI-generated, generic, template-y, or "like every other SaaS page"; asks to de-slop, de-AI, humanize, or "make it not look AI"; wants an AI-slop audit or slop score; is redesigning an existing site; or is starting a new site, landing page or app and wants it distinctive from the first commit. Pairs a 284-tell diagnostic catalog with 13 fully-specified art directions, executable color and type derivation math, and 64 craft details, producing a filled DESIGN.md spec for the project.
---

# stop-design-slop

## Read this before anything else

**Removing tells does not produce good design. It produces bland design, which reads as AI-generated too.**

Earlier versions of this skill prescribed fixing tells one at a time. That approach makes pages worse, for reasons documented in `references/method.md`:

- A 284-item ban list constrains 284 decisions out of the thousands a page makes. Every unconstrained decision reverts to the model's default.
- Banning the most common option promotes the second most common one. Everyone lands on the same runner-up, so anti-slop output ends up more uniform than the slop it replaced.
- Thirty tells fixed as thirty independent edits produce thirty unrelated decisions. The generic original was at least coherent, and incoherence reads as broken.
- Optimizing for the fewest tells converges on a flat gray page with a system font. Zero tells, zero decisions.

**So the tells never drive the fix.** They appear twice, as diagnosis before the work and as lint assertions after it. Between those two points you commit to a direction and rebuild from the token layer.

If you are here to repair a page a previous de-slop pass damaged, read the recovery section of `references/method.md` first. Reverting usually beats repairing forward.

## Modes

| Invocation | Mode |
|---|---|
| `/stop-design-slop <url>` | **AUDIT + REBUILD** a live site |
| `/stop-design-slop` in a project with UI code | **AUDIT + REBUILD** the codebase |
| `/stop-design-slop build`, or invoked while creating new UI | **PREVENT**: write the spec before any code exists |
| `audit-only` / `report` in args | Diagnose and score, produce the spec and plan, change no files |
| `quick` in args | The 63 `instant` tells only, for a fast diagnosis |
| `copy` / `visual` / `code` in args | Scope the diagnosis to those catalogs |

Infer the mode rather than asking. Existing UI goes to AUDIT, a blank slate goes to PREVENT.

## Files

Read `method.md` first, always. Then read what your phase needs.

| File | Purpose |
|---|---|
| `references/method.md` | Why removal fails, the corrected model, the workflow, the `DESIGN.md` template, dual scoring |
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
| `references/code-meta-tells.md` | Tells #252–284: builder watermarks, framework leftovers, dead wiring, a11y |

284 tells (63 instant, 154 strong, 67 mild) and 64 craft details.

## Workflow

```
DIAGNOSE  →  BRIEF  →  SPEC  →  REBUILD  →  LINT  →  JUDGE
```

### 1. DIAGNOSE

Capture the current state, then walk the tell catalogs against it. Record each hit as `#N, where it appears, severity`, and record what already works as a do-not-touch list.

Capture with whatever the host provides. For a live URL: screenshot full-height at desktop width and again at ~375px, extract page text, check the tab title and favicon. With no browser: fetch the HTML and CSS, audit those, ask the user for screenshots, and state which visual tells you could not verify. For a codebase: read entry pages, global CSS and theme config, layout components, then run the VOCAB grep sweep at the end of each catalog. Judge the rendered page whenever you can.

Run the **5-second test** explicitly: describe your first impression of the desktop screenshot in one sentence, before analysis. If it contains "generic", "template" or a tool name, that sentence is the headline of the report.

Stop here in `audit-only` mode after producing the spec and plan.

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

Ship gate needs both: Slop Score 0 to 8, Commitment Score 5 or more, every mandatory positive from `method.md` present, and no regression in contrast, focus visibility, page weight, functionality or mobile layout.

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
