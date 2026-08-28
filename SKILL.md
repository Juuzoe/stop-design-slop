---
name: stop-design-slop
description: Audit and remove "AI slop" from websites/webapps so the first glance never says "AI made this", and prevent it when building UI from scratch. Use when the user says a site looks AI-generated, generic, template-y, or "like every other SaaS page"; asks to de-slop, de-AI, humanize, or "make it not look AI"; wants an AI-slop audit or slop score; is redesigning an existing site; or is starting a new site/landing page/app and wants it slop-proof from the first commit. Covers 284 catalogued tells across layout, color, typography, copy, imagery, motion, and code/meta, each with a surgical fix that keeps the site's function, content, and conversion intact.
---

# stop-design-slop

**Prime directive:** a stranger who glances at the site for 5 seconds should not think "AI made this." That is the success metric. You reach it by removing tells while keeping the site whole: every fix swaps slop for something specific, and nothing functional or conversion-critical leaves the page.

**Second directive:** removing slop does not by itself produce design. Strip a site down and add nothing, and you get quieter slop. Every engagement ends with the Identity Injection pass.

## Modes, picked by how you were invoked

| Invocation | Mode |
|---|---|
| `/stop-design-slop <url>` | **AUDIT** a live site (browser capture, catalog sweep, fix plan) |
| `/stop-design-slop` inside a project with UI code | **AUDIT** the codebase (code sweep, plus a render if a dev server exists) |
| `/stop-design-slop build`, or invoked while creating new UI | **PREVENT**: apply the catalog as negative constraints before writing code |
| `quick` anywhere in args | Sweep the 63 `instant` tells only, for a fast first-impression fix |
| `copy` / `visual` / `code` in args | Scope the sweep to those catalog files |
| `audit-only` / `report` in args | Produce the scored report and plan. Change no files. |

When args are ambiguous, default by what exists: existing UI goes to AUDIT, a blank slate goes to PREVENT. Never ask which mode when you can infer it.

## The catalog

The tells live in `references/`, numbered in one continuous sequence so you can cite a finding as "#N". Read the files your scope covers. A full audit reads all of them.

| File | Points | Domain |
|---|---|---|
| `references/structure-layout.md` | 1–63 | Page architecture, hero formulas, section order, grids, spacing, nav, footer, IA, mobile, app shells |
| `references/color-effects.md` | 64–93 | Palettes, gradients, glow, glass, backgrounds, borders, radius, shadows, theme defaults |
| `references/typography.md` | 94–121 | Font choices, pairing, hierarchy, headline styling, labels, casing, micro-typography |
| `references/imagery-icons.md` | 122–153 | AI-image artifacts, cliché subjects, stock illustration, product imagery, icons, logos |
| `references/motion-interaction.md` | 154–183 | Scroll reveals, scroll behavior, hover and cursor effects, ambient loops, motion systems |
| `references/copy-content.md` | 184–251 | Headline formulas, AI constructions, word blacklist, CTAs, trust claims, testimonials, microcopy |
| `references/code-meta-tells.md` | 252–284 | Builder watermarks, framework leftovers, head/SEO, dead wiring, bundle smells, a11y and perf |
| `references/deslop-playbook.md` | | Fix method, Identity Injection, the tests, PREVENT constraints, report template |

That comes to **284 tells** (63 instant, 154 strong, 67 mild), deduplicated across domains. Cross-references such as "(Card layout: #26)" connect the angles on a single pattern instead of repeating it.

Each entry reads: **#N. Name** (severity), the tell, why it signals AI, then **Fix**. Severities: **instant** (visible in the first 5 seconds and strongly AI-coded), **strong** (obvious during one scroll), **mild** (counts only in aggregate).

## AUDIT workflow

### 1. Capture
Use whatever capture tools the host agent provides. See **Agent compatibility** below. The catalog stays the same either way.
- **Live URL:** load the page, screenshot it full-height at desktop width, then screenshot again at roughly 375px. Extract the page text for the copy sweep. Check the tab title and favicon. Open the pricing and about pages if they exist.
- **No browser available:** fetch the raw HTML and CSS, audit those, then ask the user for two screenshots. State plainly which visual tells you could not check without rendering.
- **Codebase:** find the UI source, read the entry pages, global CSS or theme config, and layout components. Run the grep sweep, since each catalog file ends with a `VOCAB` block of greppable strings. If a dev server exists, run it and capture the rendered page. Judge the rendered site whenever you can, because code alone hides visual tells.
- Note what the site is for and who it serves. Your fixes have to fit this brand rather than a generic taste.

### 2. Detect
Walk the catalog against the capture. Record each hit as `#N, where it appears, severity`. Record what already works too: distinctive choices, real content, good moves. That list becomes the do-not-touch list.

### 3. Score
```
Slop Score = 3×(instant hits) + 2×(strong hits) + 1×(mild hits)
```
| Score | Verdict |
|---|---|
| 0–8 | Clean. The first glance reads human. Polish only. |
| 9–20 | Pattern-y. A designer would side-eye it; civilians might not. |
| 21–45 | Recognizably AI. The first-glance test fails. |
| 46+ | Full slop. The site is the template. |

Run the **5-second test** on its own: describe your literal first impression of the desktop screenshot in one sentence, before any analysis. If that sentence contains "generic", "SaaS template", or the name of a builder tool, say so. It becomes the headline of the report.

### 4. Report
Follow the template in `references/deslop-playbook.md`. Group findings by category, cite each by #N, and pair each with its fix. Lead with the 5-second verdict and the five highest-impact tells.

### 5. Triage
Fix in impact order rather than catalog order:
1. **Pass 1, instant tells on the first viewport**: hero, headline, palette, type, badge, imagery. This alone usually flips the first impression.
2. **Pass 2, strong tells through the scroll**: sections, components, testimonials, footer.
3. **Pass 3, mild tells and the copy sweep**: microcopy, casing, motion, meta.
4. **Pass 4, Identity Injection**: add one distinctive type voice, one ownable color decision, one signature layout move, at most one signature motion, and real content wherever you removed fake content.

In `audit-only` mode, stop after the report and plan.

### 6. Verify
- Re-screenshot desktop and mobile, rerun the 5-second test, and re-score. You want zero `instant` hits, a score inside 0–8, and a first-impression sentence that no longer mentions AI or templates.
- Regression gates. The de-slop failed if any of these got worse: text contrast (keep body at 4.5:1 or better, large text at 3:1), keyboard focus visibility, page weight, the presence of nav, pricing, CTA and contact functionality, or mobile layout integrity.
- List what you changed and what you kept on purpose.

## PREVENT workflow (building from scratch)

1. **Before the first line of UI code**, read `references/deslop-playbook.md` plus the catalog files covering what you are about to build. Write a five-line **design commitment** into the plan: the typefaces and why, how you derived the palette from the brand or subject rather than defaulting to indigo-on-slate, one signature layout move, one signature motion or none, and where real content comes from.
2. Treat every `instant` and `strong` entry as a **banned default**. When you catch yourself reaching for one (centered hero, pill badge, gradient keyword, three feature cards), stop and start from that entry's Fix instead.
3. Placeholder content is a build-breaking bug rather than a TODO. Ship no lorem ipsum, no fake testimonials, stats or logos, no `#` links, no example.com addresses, even in temporary commits. When real content does not exist yet, design the section to work honestly without it, or cut the section until it does.
4. **Checkpoint audits:** run a `quick` audit on the rendered page once the first viewport is built, and again before you call it done. The first viewport has to score zero on instant tells.
5. Ship gate: run the full audit, steps 2 through 6 above, on the finished build.

## Guardrails

- **Every removal gets a replacement.** Before you touch a slop element, name the job it does (orient, persuade, prove, convert) and keep that job covered. A fake logo bar becomes one real proof point or honest silence. A pricing table stays, because "template-y" is not a reason to delete pricing. Conventions like nav bars, pricing grids, FAQs and footers are what users rely on to navigate; the slop sits in their styling and content, which is what you fix.
- **One tell, one fix.** Keep diffs surgical. Leave alone anything absent from the findings list.
- **Accessibility outranks aesthetics.** No fix may reduce contrast, remove focus states, shrink tap targets, or ignore `prefers-reduced-motion`. When a slop fix collides with accessibility, accessibility wins.
- **Restraint over reinvention.** Anti-slop is a direction, not a style. Swinging to brutalism because "AI can't do that" produces a different template and usually breaks the brand. Aim at what suits this site, spend the weirdness budget in one or two places, and keep the rest calm.
- **The brand stays the brand.** When that purple gradient is the company's actual brand color, the fix is to use it with more intention. Real brand assets are not slop.
- **Keep receipts.** List the kept-as-is items and your reasons, so a reviewer can see the restraint was deliberate.

## Identity Injection

De-slopping subtracts. This pass adds what makes the site belong to someone. Full principles sit in `references/deslop-playbook.md`. The minimum bar:

1. **Type with a point of view.** Choose at least the display face for this brand, and state the reason.
2. **An ownable color decision.** Derive it from the product, subject or brand, apply it consistently, and give it one place where it does something memorable.
3. **One signature layout move.** Break the symmetric center-stacked default once, on purpose.
4. **At most one signature motion**, doing a job such as revealing, confirming or guiding. Everything else stays calm.
5. **Real content everywhere.** Source every number, attribute every quote, and choose every image. Specificity is the strongest anti-AI signal you have.

## Agent compatibility

This skill is plain Markdown against the open `SKILL.md` standard and requires no tool by name. It runs in Claude Code, Codex, Cursor, and Gemini CLI. Adapt the capture step:

| Host | Capture with |
|---|---|
| **Claude Code** | Browser pane (`preview_start`/`navigate`, `computer` screenshot, `resize_window` for mobile, `get_page_text`), plus Glob, Read and Grep for code |
| **Codex** | Its browser and web tools where enabled. Otherwise fetch the HTML, audit the code, and ask the user for screenshots. Shell tools such as `curl` and `rg` cover the VOCAB sweep |
| **Any other agent** | Whatever fetch, screenshot and search tools it has, falling back to the no-browser path above |

Degrade honestly. When you cannot run a mode for lack of rendering or shell access, run the catalog against what you can see and label the untested categories in the report rather than guessing.

## Related skills

Use these when the host provides them, and skip them without comment otherwise.
- `design-taste` / `frontend-design`: positive design direction once the slop is gone. This skill detects tells; those two supply taste.
- `stop-slop` (Anthropic): de-AI-ing long-form prose. Use it on the site's blog posts and docs. UI copy is covered here in `copy-content.md`.
