# Changelog

## v1.1.0 — 2026-08-28

Multi-agent support. The catalog is unchanged — this makes the skill run properly outside Claude Code.

- **Codex support:** install instructions for `~/.codex/skills/` and the repo-level `.agents/skills/` convention, `$stop-design-slop` invocation, and an `agents/openai.yaml` metadata file.
- **Agent compatibility section** in `SKILL.md`: a per-host capture table (Claude Code / Codex / any other agent) and an explicit no-browser fallback path.
- **Tool-agnostic capture step** — no tool is required by name anymore; the audit degrades honestly and labels categories it couldn't verify instead of guessing.
- README: per-host install tabs, Claude Code + Codex badges, and a "does it need a browser?" FAQ entry.

## v1.0.0 — 2026-08-28

Initial release.

- **284 catalogued tells** (63 instant · 154 strong · 67 mild) across 7 consecutively numbered catalogs:
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
- **Guardrails:** replace-don't-delete, standard ≠ slop, accessibility wins every conflict, brand assets are never slop, no overcorrection, fabricated content is a bug.
- Compiled from ~330 research candidates across 50+ sources (detection guides, HN/Reddit teardowns, NN/g, the 1,590-page Show HN audit, Wikipedia's *Signs of AI writing*), deduplicated with cross-references.
