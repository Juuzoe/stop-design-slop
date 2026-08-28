---
name: stop-design-slop
description: Audit and remove "AI slop" from websites/webapps so the first glance never says "AI made this" — and prevent it when building UI from scratch. Use when the user says a site looks AI-generated, generic, template-y, or "like every other SaaS page"; asks to de-slop, de-AI, humanize, or "make it not look AI"; wants an AI-slop audit or slop score; is redesigning an existing site; or is starting a new site/landing page/app and wants it slop-proof from the first commit. Covers 284 catalogued tells across layout, color, typography, copy, imagery, motion, and code/meta, each with a surgical fix that keeps the site's function, content, and conversion intact.
---

# stop-design-slop

**Prime directive:** a stranger glancing at the site for 5 seconds should NOT think "AI made this." That is the only success metric. You get there by removing *tells*, not by removing *website* — every fix replaces slop with something specific; nothing functional, useful, or conversion-critical gets deleted.

**Second directive:** absence of slop ≠ presence of design. A de-slopped site with nothing distinctive added is just quieter slop. Every engagement ends with the Identity Injection pass (see below).

## Modes — pick by how you were invoked

| Invocation | Mode |
|---|---|
| `/stop-design-slop <url>` | **AUDIT** a live site (browser capture + catalog sweep + fix plan) |
| `/stop-design-slop` inside a project with UI code | **AUDIT** the codebase (code sweep + render if a dev server is available) |
| `/stop-design-slop build` — or invoked while creating new UI from scratch | **PREVENT** — apply the catalog as negative constraints *before* writing code |
| `quick` anywhere in args | Sweep only the 63 `instant`-severity tells — fast first-impression fix |
| `copy` / `visual` / `code` in args | Scope the sweep to those catalog files only |
| `audit-only` / `report` in args | Produce the scored report and plan; do NOT change files |

If args are ambiguous, default: existing UI → AUDIT, no UI yet → PREVENT. Never ask which mode when it's inferable.

## The catalog

The tells live in `references/`, consecutively numbered so findings can be cited as "#N". Read the files relevant to your scope — for a full audit, read all of them.

| File | Points | Domain |
|---|---|---|
| `references/structure-layout.md` | 1–63 | Page architecture, hero formulas, section order, grids/cards, spacing, nav, footer, IA, mobile, app shells |
| `references/color-effects.md` | 64–93 | Palettes, gradients, glow, glass, backgrounds, borders, radius, shadows, theme defaults |
| `references/typography.md` | 94–121 | Font choices, pairing, hierarchy, headline styling, labels, casing, micro-typography |
| `references/imagery-icons.md` | 122–153 | AI-image artifacts, cliché subjects, stock illustration systems, product imagery, icons, logos |
| `references/motion-interaction.md` | 154–183 | Scroll reveals, scroll behavior, hover/cursor effects, ambient loops, theatrics, motion system |
| `references/copy-content.md` | 184–251 | Headline formulas, AI constructions, word blacklist, CTAs, trust claims, testimonials, FAQ, about, blog, hygiene |
| `references/code-meta-tells.md` | 252–284 | Builder watermarks, framework leftovers, head/SEO, dead wiring, bundle smells, a11y/perf |
| `references/deslop-playbook.md` | — | Fix method, Identity Injection principles, the tests, PREVENT-mode constraints, report template |

Total: **284 tells** (63 instant · 154 strong · 67 mild), deduplicated across domains — cross-references like "(Card layout: #26)" link the different angles on one pattern instead of repeating it.

Each entry: **#N. Name** (severity) — the tell → **Fix**. Severities: **instant** (first 5 seconds, strongly AI-coded), **strong** (obvious on one scroll), **mild** (only counts in aggregate).

## AUDIT workflow

### 1. Capture
Use whatever capture tools the host agent actually has (see **Agent compatibility** below) — the catalog is the same either way.
- **Live URL:** load the page and screenshot the full page at desktop width, then at a ~375px mobile width. Extract the page text for the copy sweep. Check the tab title + favicon. Open 1–2 secondary pages (pricing, about) if they exist.
- **No browser available:** fetch the raw HTML/CSS instead and audit it, then ask the user for two screenshots (desktop + mobile). Say plainly which visual tells you could not check without rendering.
- **Codebase:** find the UI source; read entry pages, global CSS/theme config, and layout components. Run the grep sweep (each catalog file ends with a `VOCAB` block of greppable strings). If a dev server exists, run it and capture the rendered page — judge the *rendered* site whenever possible; code alone misses visual tells.
- Note what the site is FOR and who it serves — fixes must fit the brand, not a generic taste.

### 2. Detect
Walk the catalog against the capture. Record every hit as `#N — where it appears — severity`. Also record **what already works** (distinctive choices, real content, good moves) — this becomes the do-not-touch list.

### 3. Score
```
Slop Score = 3×(instant hits) + 2×(strong hits) + 1×(mild hits)
```
| Score | Verdict |
|---|---|
| 0–8 | Clean — first glance reads human. Polish only. |
| 9–20 | Pattern-y — a designer would side-eye it; civilians might not. |
| 21–45 | Recognizably AI — the first-glance test fails. |
| 46+ | Full slop — the site IS the template. |

Also run the **5-second test** explicitly: describe the literal first impression of the desktop screenshot in one sentence, before any analysis. If that sentence contains "generic", "SaaS template", or names a tool, say so — it's the headline of the report.

### 4. Report
Use the template in `references/deslop-playbook.md`. Findings grouped by category, cited by #N, each with its fix. Lead with the 5-second verdict and the top 5 highest-impact tells.

### 5. Triage — order of operations
Fix in impact order, not catalog order:
1. **Pass 1 — instant tells** on the first viewport (hero, headline, palette, type, badge, imagery). This alone usually flips the first impression.
2. **Pass 2 — strong tells** through the scroll (sections, components, testimonials, footer).
3. **Pass 3 — mild tells + copy sweep** (microcopy, casing, motion, meta).
4. **Pass 4 — Identity Injection** (playbook): add 1 distinctive type voice, 1 ownable color decision, 1 signature layout move, ≤1 signature motion, real content wherever fake content was removed.
- In `audit-only` mode, stop after the report + plan.

### 6. Verify
- Re-screenshot desktop + mobile; re-run the 5-second test and re-score. Target: no `instant` hits remain, score drops into 0–8, and the first-impression sentence no longer mentions AI/template/generic.
- Regression gates — the de-slop FAILED if any of these got worse: text contrast (keep ≥ 4.5:1 body / 3:1 large), keyboard focus visibility, page weight/perf, presence of nav/pricing/CTA/contact functionality, mobile layout integrity.
- List what changed and what was deliberately kept.

## PREVENT workflow (building from scratch)

1. **Before the first line of UI code**, read `references/deslop-playbook.md` plus the catalog files for whatever you're about to build, and write a 5-line **design commitment** into the plan: typeface(s) with a reason, palette derivation (from brand/subject — never default indigo-on-slate), one signature layout move, one signature motion (or none), and where real content will come from.
2. Treat every `instant` and `strong` catalog entry as a **banned default** — when you catch yourself reaching for one (centered hero + pill badge + gradient keyword + 3-col feature cards…), stop and use the entry's Fix as the starting point instead.
3. Placeholder content is a build-breaking bug, not a TODO: no lorem ipsum, no fake testimonials/stats/logos, no `#` links, no example.com emails — ever, even in "temporary" commits. If real content doesn't exist yet, design the section to work honestly without it (or cut the section until it does).
4. **Checkpoint audits:** after the first viewport is built, and again before "done", run a `quick` audit on the rendered page. Budget: first viewport must score 0 on instant tells.
5. Ship gate: full audit (steps 2–6 above) on the finished build.

## Guardrails — never make the site worse

- **Replace, don't delete.** Every removed element's *job* (orient, persuade, prove, convert) must be re-covered. Removing a fake logo bar → replace with one real proof point, or honest silence — but never delete the pricing table because pricing tables are "template-y". Standard ≠ slop: nav bars, pricing grids, FAQs, footers are conventions users rely on; the slop is in their *styling and content*, which is what you fix.
- **One tell, one fix.** Surgical diffs. No drive-by rewrites of things not on the findings list.
- **Accessibility is non-negotiable:** fixes may never reduce contrast, remove focus states, shrink tap targets, or ignore `prefers-reduced-motion`. If a slop fix and a11y conflict, a11y wins.
- **Don't overcorrect.** Anti-slop is not a style. Swinging to brutalism/neo-ugly because "AI can't do that" is just a different template — and off-brand for most sites. The target is *specific to this site*, not maximally weird. Spend the weirdness budget in 1–2 places, keep the rest calm.
- **Respect the brand.** If the purple gradient IS the company's actual brand color, the fix is to use it with more intention, not to ban it. Real brand assets are never slop.
- **Keep receipts.** In the report, list kept-as-is items with reasons, so a reviewer sees restraint was deliberate.

## Identity Injection (mandatory final pass)

De-slopping subtracts; this pass adds the thing that makes the site *someone's*. Full principles in `references/deslop-playbook.md` — minimum bar:
1. **Type with a point of view** — at least the display face chosen *for this brand*, with a stated reason.
2. **An ownable color decision** — derived from the product/subject/brand, used consistently, with one place it does something memorable.
3. **One signature layout move** — a single deliberate break from the symmetric center-stacked default.
4. **At most one signature motion** — doing a job (revealing, confirming, guiding), everything else calm.
5. **Real content everywhere** — every number sourced, every quote attributable, every image intentional. Specificity is the single strongest anti-AI signal.

## Agent compatibility

This skill is plain Markdown against the open `SKILL.md` standard — no tool is required by name. It runs in Claude Code, Codex, Cursor, Gemini CLI, and anything else that reads skill folders. Adapt only the capture step:

| Host | Capture with |
|---|---|
| **Claude Code** | Browser pane (`preview_start`/`navigate`, `computer` screenshot, `resize_window` for mobile, `get_page_text`), plus Glob/Read/Grep for code |
| **Codex** | Its browser/web tools where enabled; otherwise fetch the HTML, audit the code, and request screenshots from the user. Shell (`curl`, `rg`) covers the VOCAB grep sweep |
| **Any other agent** | Any fetch/screenshot/search tools available; fall back to the "no browser available" path above |

Degrade honestly: if a mode can't be run (no rendering, no shell), still run the catalog against what you *can* see and label the untested categories in the report rather than guessing.

## Related skills
Optional — use if the host provides them; skip silently otherwise.
- `design-taste` / `frontend-design` — positive design direction once slop is gone; this skill is the tell-detector, those are the taste.
- `stop-slop` (Anthropic) — long-form prose de-AI-ing; use it for blog posts/docs on the site. UI copy is covered here in `copy-content.md`.
