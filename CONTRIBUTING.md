# Contributing

The catalog only stays useful if it evolves as fast as the generators do. Three kinds of contributions are welcome:

## 1. New tells

One tell per PR. Before adding, check all seven catalog files **and their cross-references** — many patterns already exist from a different angle (layout vs. color vs. copy), and near-duplicates get closed. A new tell must be:

- **Specific.** "Pill-shaped announcement badge with a sparkle emoji above the hero H1" passes; "generic hero" fails.
- **Observed.** Cite where it's documented or widely discussed (link), or mark it `expert` if it's practitioner knowledge.
- **Fixable without collateral damage.** The fix replaces or adjusts — it never deletes functionality, reduces accessibility, or tells someone to "redesign everything."

Use the entry format, appended to the END of the matching catalog file (numbering is append-only — never renumber existing entries, they're cited by number elsewhere):

```markdown
**N. Name of the tell** (instant|strong|mild)
Tell: what it looks like, concretely.
Why: why it reads as AI-generated.
Fix: the surgical replacement.
```

Severity rubric: **instant** = triggers "AI made this" within 5 seconds on its own · **strong** = a clear signal during one normal scroll · **mild** = only counts in aggregate with other tells. If your tell is greppable, add the strings to that file's VOCAB block too, and bump the totals in `SKILL.md` and `README.md`.

## 2. False positives

If the skill flagged something that's genuinely good design (or a real brand asset), open an issue with a screenshot/link and the entry number. Guardrail bugs — a fix that reduced contrast, deleted something functional, or made a site worse — are the highest-priority issues in this repo.

## 3. Better fixes

Fixes that are more surgical, more specific, or better-sourced than the current ones. PRs that only sharpen `Fix:` lines are very welcome.

## Style

Match the existing voice: dry, concrete, no hype. It would be embarrassing for this particular repo to merge a PR full of "seamlessly elevate your workflow" — the copy catalog (#184–251) applies to our own prose.
