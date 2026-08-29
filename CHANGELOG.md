# Changelog

## v2.0.0, 2026-08-29

A user ran v1 on their project and the result looked more AI-generated than the original. They were right, and the diagnosis reshaped the skill: removing tells produces bland design, and bland reads as machine-made. The catalog is intact, but it no longer drives the fix.

**Why v1 failed** (documented with sources in `references/method.md`):

- **Coverage.** 284 rules constrain 284 decisions out of the thousands a page makes. Every unconstrained decision reverts to the model default, so a subtractive audit can never win.
- **Negation promotes the runner-up.** Banning the mode promotes second place, and everyone running the list lands on the same second choice. The escape hatch has a spec sheet.
- **Patchwork.** Thirty independent edits produce thirty unrelated decisions, and incoherence reads worse than consistent genericness.
- **The metric was wrong.** A tells-only score has its optimum at a flat gray page. Zero tells, zero decisions.
- Two more mechanisms: unverifiable rules cause over-correction rather than compliance, and long prohibition documents measurably collapse output diversity.

**New workflow:** `DIAGNOSE → BRIEF → SPEC → REBUILD → LINT → JUDGE`. The tells now appear as diagnosis and as lint assertions, never as repair instructions.

**New files:**

- `references/method.md`: the failure analysis, the corrected model, the `DESIGN.md` template, recovery steps for a damaged page, dual scoring, and the mandatory positives.
- `references/art-direction.md`: the studio process from perception brief through attribute disambiguation, competitive audit, divergence techniques and three-tier token propagation.
- `references/directions.md`: 13 fully-specified art directions with real typefaces and example sites, a three-filter selection procedure, an eight-attribute map, and a free type shelf that excludes the overused names.
- `references/derivation.md`: executable math for hue sourcing, OKLCH ramps, APCA and WCAG contrast solving, typeface selection and pairing gates, scale and spacing derivation, radius and layered shadow construction, with a computed end-to-end worked example.
- `references/craft-details.md`: 64 implementable craft details (C1–C64) with CSS, ranked by signal per hour.

**Also:** a second metric, the Commitment Score, since low slop with low commitment is the bland failure this release exists to prevent. Ship gate now requires both.

## v1.2.0, 2026-08-28

Every word in the repo now passes the standard the repo enforces. The catalog keeps all 284 tells, their numbers, severities and technical strings; what changed is the prose around them.

- **Ran the whole repo through Anthropic's `stop-slop` skill.** Removed 331 em dashes from our own writing, along with the adverbs, passive constructions and false agency ("the tab confesses", "the metadata exposes") that came with them.
- **Cut the binary contrasts.** "Less slop, not less website" and "Standard ≠ slop" stated their point through negation. The README and SKILL.md now state it directly.
- **Rewrote the fragment-stacked README opening** as complete sentences, since stacking fragments for drama is itself a listed tell.
- **Fixed the report template**, which had been emitting em dashes into every audit report the skill writes.
- **Kept every quoted specimen intact.** The 8 remaining em dashes all sit inside evidence: entry #193, whose name is the em-dash pattern, the #199 density example, two slop specimens, a source quotation and an article title. The VOCAB blacklist is byte-identical.

## v1.1.0, 2026-08-28

Multi-agent support. The catalog is unchanged; this release makes the skill run outside Claude Code.

- **Codex support:** install instructions for `~/.codex/skills/` and the repo-level `.agents/skills/` convention, `$stop-design-slop` invocation, and an `agents/openai.yaml` metadata file.
- **Agent compatibility section** in `SKILL.md`: a per-host capture table (Claude Code / Codex / any other agent) and an explicit no-browser fallback path.
- **Tool-agnostic capture step:** the skill no longer requires any tool by name. When it cannot verify a category, the report says so instead of guessing.
- README: per-host install tabs, Claude Code + Codex badges, and a "does it need a browser?" FAQ entry.

## v1.0.0, 2026-08-28

Initial release.

- **284 catalogued tells** (63 instant · 154 strong · 67 mild) across 7 catalogs numbered in one continuous run:
  - Structure & layout (#1–63)
  - Color & effects (#64–93)
  - Typography (#94–121)
  - Imagery & icons (#122–153)
  - Motion & interaction (#154–183)
  - Copy & content (#184–251), including a ~200-phrase greppable blacklist
  - Code & meta / builder fingerprints (#252–284)
- **Two modes:** AUDIT (existing sites: capture → detect → score → report → 4-pass fix → verify) and PREVENT (from-scratch builds: banned defaults, tokens-first, checkpoint audits).
- **Slop Score** (3×instant + 2×strong + 1×mild) with verdict bands and an explicit 5-second first-impression test.
- **De-slop playbook:** fix method, the tests (5-second, lineup, squint, read-aloud), PREVENT-mode prompting constraints, report template, and 18 Identity Injection principles for what to add after removal.
- **Guardrails:** replace instead of deleting, keep the conventions users depend on, accessibility wins every conflict, brand assets are never slop, no overcorrection, fabricated content is a bug.
- We pulled ~330 research candidates from 50+ sources (detection guides, HN/Reddit teardowns, NN/g, the 1,590-page Show HN audit, Wikipedia's *Signs of AI writing*), then deduplicated them and wired in cross-references.
