<div align="center">

# stop-design-slop

**A Claude Code skill that removes the "AI made this" look from your website.**

284 researched tells · severity-ranked · each with a surgical fix · audits existing sites or builds slop-free from scratch

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude_Code-ready-6b4bff.svg)](#install)
[![Codex](https://img.shields.io/badge/Codex-ready-0b7285.svg)](#install)
[![Catalog](https://img.shields.io/badge/tells-284-orange.svg)](#what-it-catches)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

</div>

---

You know the site. Pill badge with a sparkle. Centered hero, one gradient word. Three feature cards with Lucide icons in little indigo squares. "Trusted by 10,000+ teams" on a domain registered last Tuesday. Purple glow on `#0a0a0a`. Inter everywhere.

Visitors pattern-match it in five seconds, think *"AI made this,"* and stop trusting everything below the fold.

This skill fixes that. It walks your site against a catalog of **284 documented tells** — compiled from detection guides, design-community teardowns, a 1,590-page Show HN audit, and Wikipedia's signs-of-AI-writing research — and applies the smallest set of changes that flips the first impression. **Less slop, not less website:** nothing functional, useful, or conversion-critical gets deleted.

## Install

It's an open-standard `SKILL.md` folder, so it drops into any agent that reads skills — **Claude Code**, **Codex**, Cursor, Gemini CLI. Pick your host:

<details open>
<summary><b>Claude Code</b></summary>

```bash
# macOS / Linux
git clone https://github.com/Juuzoe/stop-design-slop ~/.claude/skills/stop-design-slop
```

```powershell
# Windows
git clone https://github.com/Juuzoe/stop-design-slop "$env:USERPROFILE\.claude\skills\stop-design-slop"
```

Per-project instead: clone into `<project>/.claude/skills/stop-design-slop`. Invoke with `/stop-design-slop`.
</details>

<details open>
<summary><b>Codex</b></summary>

```bash
# macOS / Linux
git clone https://github.com/Juuzoe/stop-design-slop ~/.codex/skills/stop-design-slop
```

```powershell
# Windows
git clone https://github.com/Juuzoe/stop-design-slop "$env:USERPROFILE\.codex\skills\stop-design-slop"
```

Restart Codex, then run `/skills` or type `$stop-design-slop`. For a repo-scoped install (shared with your team, and the cross-agent convention), clone into `.agents/skills/stop-design-slop` at the repository root instead — Codex reads skills from repository, user, admin, and system locations.
</details>

<details>
<summary><b>Cursor, Gemini CLI, other agents</b></summary>

Clone into that agent's skills directory — or anywhere, and point the agent at `SKILL.md`:

```bash
git clone https://github.com/Juuzoe/stop-design-slop
```

The skill names no tool as a hard requirement; see [Agent compatibility](SKILL.md#agent-compatibility) for how the capture step adapts to whatever browser/fetch/shell tools your agent has.
</details>

Update anytime with `git pull`.

## Use

```text
/stop-design-slop https://yoursite.com    audit a live site (screenshots + code sweep)
/stop-design-slop                         audit the current project's UI
/stop-design-slop quick                   first-impression pass only (the 63 instant tells)
/stop-design-slop audit-only              scored report + fix plan, changes nothing
/stop-design-slop build                   prevention mode: bans the defaults BEFORE code is written
/stop-design-slop copy                    scope to copywriting (also: visual, code)
```

In Codex, swap the leading `/` for `$` (`$stop-design-slop https://yoursite.com`). Or just say *"this looks AI-generated, fix it"* in any agent — the description triggers it.

Every audit produces a report: a one-sentence 5-second verdict, a **Slop Score** (`3×instant + 2×strong + 1×mild`), findings cited by catalog number with a fix each, a do-not-touch list of what already works, and a four-pass fix plan that ends with adding something distinctive — because a de-slopped site with nothing added is just quieter slop.

| Score | Verdict |
|---|---|
| 0–8 | Clean — first glance reads human |
| 9–20 | Pattern-y — designers side-eye it |
| 21–45 | Recognizably AI — the 5-second test fails |
| 46+ | Full slop — the site *is* the template |

## What it catches

Seven consecutively numbered catalogs. A taste of each:

| Catalog | Tells | For example |
|---|---|---|
| [Structure & layout](references/structure-layout.md) | #1–63 | #1 the "✨ Announcing" pill badge · #10 the hero→logos→features→pricing→FAQ conveyor belt · #26 icon-tile feature card grid |
| [Color & effects](references/color-effects.md) | #64–93 | #64 untouched indigo-500 · #72 blue→purple→pink hero gradient · #77 blurred glow orbs |
| [Typography](references/typography.md) | #94–121 | #94 Inter as the only typeface · #107 gradient keyword via `bg-clip-text` · #113 ALL-CAPS eyebrow labels |
| [Imagery & icons](references/imagery-icons.md) | #122–153 | #123 six-fingered hero art · #133 Corporate Memphis blob people · #144 emoji as feature icons |
| [Motion & interaction](references/motion-interaction.md) | #154–183 | #154 fade-up on every section · #170 particle backgrounds · #178 animated count-ups of invented numbers |
| [Copy & content](references/copy-content.md) | #184–251 | #184 "Supercharge Your Workflow" · #193 "It's not just X — it's Y" · #228 "Trusted by 10,000+ teams" |
| [Code & meta](references/code-meta-tells.md) | #252–284 | #252 the Lovable badge · #259 "Create Next App" tab title · #271 contact forms wired to nothing |

Plus the [de-slop playbook](references/deslop-playbook.md): fix method, the tests (5-second, lineup, squint, read-aloud), PREVENT-mode constraints for building with AI tools, and 18 **Identity Injection** principles for what to add once the slop is gone.

Every entry looks like this:

> **1. Announcement pill badge above the hero H1** (instant)
> Tell: rounded-full pill chip floating directly above the headline — "✨ Announcing our Series A" — with sparkle emoji, colored dot, or chevron.
> Why: it is the literal top block of every v0/shadcn hero template; real companies only run announcement chips when there is dated news that links somewhere.
> Fix: delete unless there is actual news; if real, link it to a dated changelog post and restyle as a small text link near the nav.

Each catalog ends with a **VOCAB block** — exact strings, Tailwind classes, hex values, and library names to grep for (`from-purple-500`, `data-aos`, `i.pravatar.cc`, `lovable-uploads`, "Trusted by 10,000+", …), so the audit works on code even before anything renders.

## What it will NOT do

This is the part most "make it pretty" prompts get wrong, so it's built into the skill as hard guardrails:

- **Replace, don't delete.** Every removed element's job (orient, persuade, prove, convert) must be re-covered. A fake logo bar becomes one real proof point or honest silence — never a deleted pricing table.
- **Standard ≠ slop.** Navbars, pricing grids, FAQs, and footers are conventions users rely on. The slop is in their styling and content, and that's what gets fixed.
- **Accessibility wins every conflict.** No fix may reduce contrast, remove focus states, shrink tap targets, or ignore `prefers-reduced-motion`.
- **Your brand is never slop.** If the purple genuinely is your brand color, it stays — used with more intention.
- **No overcorrecting.** Anti-slop is not a style; swinging to brutalism because "AI can't do that" is just a different template. One or two deliberate moves, everything else calm.
- **Fabrication is treated as a bug, not a style choice.** Invented testimonials, stats, and logos get replaced with honest content or removed — never re-skinned.

## Two modes

**AUDIT** — for existing sites and redesigns. Capture (browser screenshots desktop + mobile, code grep) → detect against the catalog → score → report → fix in four passes (instant tells on the first viewport, then strong, then mild + copy, then identity injection) → re-screenshot, re-score, and verify nothing regressed (contrast, focus, weight, functionality, mobile).

**PREVENT** — for building from scratch, especially with AI tools. The catalog's instant and strong tells become banned defaults before the first line of UI code; theme tokens are set first so defaults can't leak in; placeholder content is a build-breaking bug; the first viewport must score zero on instant tells before the build continues.

## How the catalog was built

Five parallel research passes over the live web (design essays, Hacker News, Reddit, detection guides like slopdar and isthatvibecoded, NN/g, the avoid-ai-design corpus, Wikipedia's *Signs of AI writing*) surfaced ~330 candidate tells, deduplicated to 284 distinct points — cross-references like "(Card layout: #26)" connect the different angles on one pattern instead of repeating it. Source lists sit at the bottom of every catalog file. It's a living catalog: the defaults will shift as the tools do, and [PRs are how it keeps up](CONTRIBUTING.md).

And yes — this README was audited with its own copy catalog. Zero rocket emoji were harmed or used.

## FAQ

**Will it make every site look the same "non-AI" way?** No — the fixes are directions, not prescriptions, and the identity-injection pass is explicitly derived from *your* brand, product, and audience. Sameness is the disease here, not the cure.

**Does it work on apps, or just landing pages?** Both. There are dedicated tells for app shells (#62, the default dashboard scaffold), empty states, forms, and motion systems.

**Does it need a browser to work?** No. Rendering is better — some visual tells can only be seen — but without it the skill audits the code, runs the greppable VOCAB sweep, and tells you in the report which categories it couldn't verify instead of guessing.

**My site was built with v0/Lovable/Bolt. Is it doomed?** No — that's the primary use case. Catalog 7 exists specifically to strip builder fingerprints, and PREVENT mode keeps the next build clean.

**Is this anti-AI?** It's anti-*default*. Build with whatever you want — the skill just makes sure the result looks like someone made a decision.

## Contributing

Found a tell that's not in the catalog? A fix that made something worse? A false positive? See [CONTRIBUTING.md](CONTRIBUTING.md) — one tell per PR, in the entry format, with a severity and a fix that doesn't degrade the site.

If this saved your landing page from the purple-gradient fate, a ⭐ helps other people find it before they ship the pill badge.

## License

[MIT](LICENSE) — use it, fork it, ship it.
