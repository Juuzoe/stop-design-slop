<div align="center">

# stop-design-slop

**An agent skill that removes the "AI made this" look from your website.**

284 researched tells, ranked by severity, each with a surgical fix. Audits an existing site or keeps a new one clean from the first commit.

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude_Code-ready-6b4bff.svg)](#install)
[![Codex](https://img.shields.io/badge/Codex-ready-0b7285.svg)](#install)
[![Catalog](https://img.shields.io/badge/tells-284-orange.svg)](#what-it-catches)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

</div>

---

Open five new startup sites and you will meet the same page. A pill badge with a sparkle floats above a centered hero whose headline has exactly one gradient word. Three feature cards sit below it, each holding a Lucide icon in a small indigo square. The trust bar claims 10,000+ teams on a domain someone registered last Tuesday, and the whole thing glows purple over `#0a0a0a` in Inter.

Your visitors recognize that page in about five seconds. They think "AI made this," and they stop believing anything below the fold.

This skill checks your site against a catalog of **284 documented tells**, drawn from detection guides, design-community teardowns, a 1,590-page Show HN audit, and Wikipedia's research on signs of AI writing. It then applies the smallest set of changes that flips the first impression. Your functional, useful and conversion-critical parts stay on the page.

## Install

The skill is an open-standard `SKILL.md` folder, so it drops into any agent that reads skills: Claude Code, Codex, Cursor, Gemini CLI. Pick your host.

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

For one project only, clone into `<project>/.claude/skills/stop-design-slop`. Invoke with `/stop-design-slop`.
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

Restart Codex, then run `/skills` or type `$stop-design-slop`. To share it with your team, clone into `.agents/skills/stop-design-slop` at the repository root instead. Codex reads skills from repository, user, admin and system locations.
</details>

<details>
<summary><b>Cursor, Gemini CLI, other agents</b></summary>

Clone into that agent's skills directory, or clone anywhere and point the agent at `SKILL.md`:

```bash
git clone https://github.com/Juuzoe/stop-design-slop
```

No tool is a hard requirement. See [Agent compatibility](SKILL.md#agent-compatibility) for how the capture step adapts to the browser, fetch and shell tools your agent happens to have.
</details>

Run `git pull` to update.

## Use

```text
/stop-design-slop https://yoursite.com    audit a live site (screenshots + code sweep)
/stop-design-slop                         audit the current project's UI
/stop-design-slop quick                   first-impression pass only (the 63 instant tells)
/stop-design-slop audit-only              scored report + fix plan, changes nothing
/stop-design-slop build                   prevention mode: bans the defaults BEFORE code is written
/stop-design-slop copy                    scope to copywriting (also: visual, code)
```

In Codex, swap the leading `/` for `$`, as in `$stop-design-slop https://yoursite.com`. In any agent you can also say "this looks AI-generated, fix it" and the description will trigger it.

Every audit returns a report: a one-sentence 5-second verdict, a **Slop Score** (`3×instant + 2×strong + 1×mild`), findings cited by catalog number with a fix each, a do-not-touch list of what already works, and a four-pass plan that ends by adding something distinctive.

| Score | Verdict |
|---|---|
| 0–8 | Clean. The first glance reads human. |
| 9–20 | Pattern-y. Designers side-eye it. |
| 21–45 | Recognizably AI. The 5-second test fails. |
| 46+ | Full slop. The site is the template. |

## What it catches

Seven catalogs, numbered in one continuous sequence. A taste of each:

| Catalog | Tells | For example |
|---|---|---|
| [Structure & layout](references/structure-layout.md) | #1–63 | #1 the "✨ Announcing" pill badge · #10 the hero→logos→features→pricing→FAQ conveyor belt · #26 icon-tile feature card grid |
| [Color & effects](references/color-effects.md) | #64–93 | #64 untouched indigo-500 · #72 blue→purple→pink hero gradient · #77 blurred glow orbs |
| [Typography](references/typography.md) | #94–121 | #94 Inter as the only typeface · #107 gradient keyword via `bg-clip-text` · #113 ALL-CAPS eyebrow labels |
| [Imagery & icons](references/imagery-icons.md) | #122–153 | #123 six-fingered hero art · #133 Corporate Memphis blob people · #144 emoji as feature icons |
| [Motion & interaction](references/motion-interaction.md) | #154–183 | #154 fade-up on every section · #170 particle backgrounds · #178 count-ups of invented numbers |
| [Copy & content](references/copy-content.md) | #184–251 | #184 "Supercharge Your Workflow" · #193 "It's not just X, it's Y" · #228 "Trusted by 10,000+ teams" |
| [Code & meta](references/code-meta-tells.md) | #252–284 | #252 the Lovable badge · #259 "Create Next App" tab title · #271 contact forms wired to nothing |

The [de-slop playbook](references/deslop-playbook.md) carries the fix method, the tests (5-second, lineup, squint, read-aloud), constraints for building with AI tools, and 18 **Identity Injection** principles covering what to add once the slop is gone.

Every entry follows one shape:

> **1. Announcement pill badge above the hero H1** (instant)
> Tell: rounded-full pill chip sitting above the headline, reading "✨ Announcing our Series A" or "New: v2.0 is live →", with a sparkle emoji or colored dot, thin border, tinted background.
> Why: v0 and shadcn put this block at the top of every hero template they ship. Companies with real news date it and link it somewhere.
> Fix: delete the chip when you have no news. With news, point it at a dated changelog or blog post and restyle it as a small text link near the nav.

Each catalog closes with a **VOCAB block**: exact strings, Tailwind classes, hex values and library names to grep for (`from-purple-500`, `data-aos`, `i.pravatar.cc`, `lovable-uploads`, "Trusted by 10,000+"). The audit therefore works on source code before anything renders.

## What it will not do

Most "make it pretty" prompts fail here, so the skill enforces these as hard guardrails.

- **Every removal gets a replacement.** Name the job an element does (orient, persuade, prove, convert) and keep that job covered. A fake logo bar becomes one real proof point or honest silence. Your pricing table stays.
- **Conventions stay.** Nav bars, pricing grids, FAQs and footers are what visitors rely on to navigate. The slop lives in their styling and content, and that is what gets fixed.
- **Accessibility outranks aesthetics.** No fix may reduce contrast, remove focus states, shrink tap targets or ignore `prefers-reduced-motion`.
- **Your brand stays yours.** When the purple is the company's actual brand color, it stays, used with more intention.
- **Restraint over reinvention.** Anti-slop is a direction, not a style. Swinging to brutalism because "AI can't do that" produces a different template. One or two deliberate moves, and the rest stays calm.
- **Invented content gets replaced or removed.** Fabricated testimonials, stats and logos never get re-skinned into prettier fabrications.

## Two modes

**AUDIT**, for existing sites and redesigns. Capture the page (desktop and mobile screenshots, code grep), detect against the catalog, score, report, then fix in four passes: instant tells on the first viewport, strong tells, mild tells with the copy sweep, and identity injection. Re-screenshot, re-score, and check that contrast, focus, weight, functionality and mobile layout all survived.

**PREVENT**, for building from scratch and for building with AI tools. The instant and strong tells become banned defaults before the first line of UI code. You set theme tokens first so defaults cannot leak in. Placeholder content counts as a build-breaking bug. The first viewport has to score zero on instant tells before the build continues.

## How the catalog was built

Five parallel research passes over the live web surfaced roughly 330 candidate tells, which deduplicated to 284 distinct points. Sources included design essays, Hacker News, Reddit, detection guides such as slopdar and isthatvibecoded, NN/g, the avoid-ai-design corpus, and Wikipedia's *Signs of AI writing*. Cross-references such as "(Card layout: #26)" connect the angles on a single pattern. Each catalog file lists its sources at the bottom.

The catalog is a living document, since the defaults shift as the tools do. [PRs are how it keeps up.](CONTRIBUTING.md) This README goes through the repo's own copy catalog before every release, which is why it carries no rocket emoji.

## FAQ

**Will every de-slopped site end up looking the same?** No. The fixes are directions rather than prescriptions, and the identity-injection pass derives from your brand, product and audience. Sameness is the disease here.

**Does it work on apps or only landing pages?** Both. The catalog covers app shells (#62, the default dashboard scaffold), empty states, forms and motion systems.

**Does it need a browser?** Rendering helps, since some visual tells only appear on screen. Without one, the skill audits the code, runs the greppable VOCAB sweep, and tells you in the report which categories it could not verify.

**My site came out of v0, Lovable or Bolt. Is it doomed?** That is the main use case. Catalog 7 exists to strip builder fingerprints, and PREVENT mode keeps the next build clean.

**Is this anti-AI?** It is anti-default. Build with whatever you like. The skill checks that the result looks like somebody made a decision.

## Contributing

Found a tell the catalog misses, a fix that made something worse, or a false positive? [CONTRIBUTING.md](CONTRIBUTING.md) has the entry format, the severity rubric, and the one-tell-per-PR rule.

A ⭐ helps other people find this before they ship the pill badge.

## License

[MIT](LICENSE). Use it, fork it, ship it.
