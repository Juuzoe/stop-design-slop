# Contributing

The catalog stays useful as long as it keeps pace with the generators. Three kinds of contributions help:

## 1. New tells

One tell per PR. Read all seven catalog files **and their cross-references** first, because many patterns are already in there from another angle (layout, color, copy). We close near-duplicates. A new tell must be:

- **Specific.** "Pill-shaped announcement badge with a sparkle emoji above the hero H1" passes; "generic hero" fails.
- **Observed.** Link to where someone documented or discussed it, or mark it `expert` when it comes out of your own practice.
- **Fixable without collateral damage.** The fix replaces or adjusts. It never deletes functionality, reduces accessibility, or tells someone to "redesign everything."

Append the entry to the END of the matching catalog file in this format. Numbering is append-only: never renumber an existing entry, since other files cite it by number.

```markdown
**N. Name of the tell** (instant|strong|mild)
Tell: what it looks like, concretely.
Why: why it reads as AI-generated.
Fix: the surgical replacement.
```

Severity rubric: **instant** = triggers "AI made this" within 5 seconds on its own · **strong** = a clear signal during one normal scroll · **mild** = only counts in aggregate with other tells. When your tell is greppable, add the strings to that file's VOCAB block, and bump the totals in `SKILL.md` and `README.md`.

## 2. False positives

When the skill flags real design work or a real brand asset, open an issue with a screenshot or link and the entry number. Guardrail bugs sit at the top of the queue here: a fix that reduced contrast, deleted something functional, or made the site worse.

## 3. Better fixes

Send fixes that are more surgical or better-sourced than the ones we have. A PR that sharpens nothing but `Fix:` lines is welcome.

## Style

Match the voice already here: dry and concrete, no hype. The copy catalog (#184–251) applies to our own prose, so merging a PR full of "seamlessly elevate your workflow" would embarrass this repo in particular.
