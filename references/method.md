# Method: why removing tells makes pages worse, and what to do instead

Read this before running any audit. It replaces the tell-by-tell repair loop that earlier versions of this skill prescribed.

## What goes wrong

Six mechanisms, each documented. Together they explain how a page gets *more* AI-looking after a de-slop pass.

**1. Coverage. The largest cause.**
A 284-item ban list constrains 284 decisions. A page makes thousands: line-height, measure, hover easing, focus ring, empty state, section rhythm, caption style, table rules. Every decision the list does not name reverts to the model prior. Silence in a design system equals defaults. A subtractive audit can never reach coverage of the decision space, no matter how long it grows. Only a positive specification can.

**2. Negation promotes the runner-up.**
Models follow positive instructions more reliably than prohibitions, and banning the mode of a distribution does not flatten the distribution. It promotes second place. Every agent running the same ban list lands on the same second choice, so anti-slop output ends up *more* uniform than the slop it replaced. Space Grotesk over Inter is now a catalogued pairing. The 2026 editorial-serif escape route has a published spec: wide light-weight display serif, 0.05em to 0.15em tracking, small caps, monochrome palette. The escape hatch has a spec sheet.

**3. Unverifiable rules cause over-correction.**
Guardrail research finds that when a mitigation instruction creates a goal the model cannot check against its own output, the model treats it as a competing objective and over-corrects rather than complying. Well-intentioned interventions raise failure rates. An agent cannot see the render, so "make the hierarchy feel intentional" is unverifiable and backfires. "No hex value outside this allowlist" is checkable and holds.

**4. Stripping signifiers breaks the page.**
Shadow, radius, and fill are slop tells *and* the primary clickability signifiers. Remove all three and interactive elements lose their affordance. Weak signifiers measurably slow users down and force them to test what is clickable. The page now reads as unfinished as well as bland, which is worse than generic. Flat 2.0 exists because pure flat failed.

**5. Long constraint documents collapse diversity.**
Format and constraint scaffolding measurably reduces output diversity. A 284-item prohibition document is itself a diversity-collapsing structure. Length is a cost here, not a virtue. The artifact the agent works from should be short, positive, and complete rather than long and prohibitive.

**6. Incoherent patchwork.**
Thirty tells fixed as thirty independent edits produce thirty unrelated decisions. The original page was generic but internally consistent: one font, one radius, one accent, applied everywhere. After scattered repair you get a different font, three radii, a flat section beside a rounded one, motion stripped here but not there. Consistency is the floor a template clears and patchwork does not.

### Two traps that survive a careful audit

**Competent defaults.** The AI look is not incompetence. Spacing is reasonable, colors do not clash, type is legible. An audit that hunts defects finds little to fix and leaves the genericness untouched. The pass criterion cannot be absence of defect. It has to be presence of commitment.

**Evasion has its own signature.** Classifiers trained on human, AI, and humanized-AI text identify the humanized class with about 97% accuracy. Optimizing to dodge a detector produces a third category rather than the human category. Restate the goal: express a specific brief, rather than avoid detection.

## The corrected model

Three properties, all required.

**Coverage.** Fill every decision slot the model would otherwise default on. A short complete spec beats a long partial blocklist.

**Commitment.** Distinctiveness rides on a few high-salience decisions propagated everywhere, not on broad tasteful adjustment. The specific choice is often under-determined by the brief, and that is fine. Propagation across every surface converts a choice into an identity. Pick fast, anchor the pick to something real, then stop revisiting it.

**Verifiability.** Every rule the agent must obey should be checkable against its own output: a hex allowlist, a banned class list, a computed contrast ratio, a string match. Judge the render separately, with a rubric, because a checklist cannot govern generation.

Generic does not mean too many tells. Generic means too few commitments and too many unfilled slots.

## Workflow

```
BRIEF  →  SPEC  →  BUILD/REBUILD  →  LINT  →  JUDGE
```

The 284 tells appear twice, and never as instructions: as **diagnosis** in the brief phase (what is wrong now) and as **lint assertions** after the build (did we fall back into a default).

### 1. BRIEF
Run `art-direction.md`. It ends with a one-sentence concept, a named audience, 3 to 5 disambiguated attributes, an exclusion list, and a chosen direction.

Refuse to proceed without a concept and an audience. Art direction is the framework that makes a thousand small choices agree. With no concept, agreement happens by defaulting. If the user will not supply one, generate three candidate directions and force a pick.

### 2. SPEC
Write `DESIGN.md` into the project: 20 to 50 lines, exact values, no adjectives. Template below. This artifact is the deliverable, and the user edits it. Never ship an audit without it.

### 3. BUILD or REBUILD
Token layer first, as one atomic change, then components, then content, then craft. Never scatter edits across components before the tokens agree.

**Make defaults unreachable rather than discouraged.** In Tailwind, define `colors:` rather than `extend:` so `indigo-600` and the rest cannot be referenced. Renaming `indigo` to `primary` changes nothing perceptual. Remove the value from the reachable space.

### 4. LINT
Machine-checkable assertions in CI: hex allowlist, banned utility classes, off-scale spacing, banned copy openers, contrast computation. Warnings first, then errors.

### 5. JUDGE
Write a rubric for this brief describing what good looks like, then evaluate the rendered page against it. Nondeterministic generation cannot be governed by exhaustive specification. Critique defines quality without demanding exactness, and it evaluates the render rather than the source.

## Recovering from a bad de-slop

If a previous pass left the page worse, do not repair it forward. Thirty scattered edits are harder to reconcile than the generic original, because you now have to reverse-engineer intent that was never there.

1. **Revert to the pre-audit commit.** The generic version is a better starting point: it is at least internally consistent, so a token change propagates predictably. Patchwork has no consistent base to propagate from.
2. **Keep the diagnosis.** The tell list from the failed run is still accurate and still useful. It was the repair strategy that failed, not the detection.
3. **Write `DESIGN.md` before touching code.** Every slot filled.
4. **Rebuild from tokens** in one atomic change, then repair components.
5. **Compare against the reverted original, not against the patchwork.** The patchwork is not a baseline.

When reverting is impossible, treat the current state as the input to a fresh rebuild rather than as work in progress. Write the spec, apply it at the token layer, and let it overwrite the scattered decisions.

## The spec

Fill every line with a value. An empty line is a decision handed back to the model.

```markdown
# DESIGN.md

CONCEPT: <one sentence: the idea every choice agrees with>
AUDIENCE: <who, specifically>
REMEMBERED-FOR: <the one thing>
DIRECTION: <named direction from directions.md>
NEVER: <3-6 exclusions from the anti-mood board>

## Type
display: <family, weight, source>        e.g. Fraunces 600, self-hosted
text:    <family, weights>               e.g. IBM Plex Sans 400/500
mono:    <family or none>
scale:   <ratio + base>                  e.g. 1.333 from 16px
tracking: display <value>, body <value>, caps <value>
leading: display <value>, body <value>
measure: <ch>                            e.g. 68ch

## Color
Delete the framework default palette from config first.
bg:        <hex, named>                  e.g. #F4F1EA warm paper
surface:   <hex>
text:      <hex>   secondary: <hex>   muted: <hex>
accent:    <hex, derived from what>
border:    <hex>
success / error / warning: <hex each>
accent appears only in: <list the exact roles>
body contrast: <computed ratio, >= 4.5:1>

## Geometry
radius:  <one value, or 0>               applied to buttons, cards, inputs, images alike
border:  <width + color>
shadow:  <one value, or none>
Rule: an interactive element keeps at least two of {border, fill, hover/focus delta}.

## Space
scale: 8 / 16 / 24 / 40 / 64 / 96
within-group gaps <= 16, between-section gaps >= 64
grid: <columns + the numeric asymmetry>
  e.g. minmax(2rem,1fr) minmax(0,38rem) minmax(0,1fr), content left, art bleeding right

## Motion
easing: <one house curve>                e.g. cubic-bezier(0.25,0.46,0.45,0.94)
durations: fast <ms> / normal <ms> / slow <ms>
applies to: feedback on action
never: entrance-on-scroll for every section
prefers-reduced-motion: honored

## Imagery
style: <editorial | documentary | technical | architectural | none>
rules: <lighting, treatment, crop, background, subject placement, ratio>

## Copy
voice: <one sentence>
required: at least one claim with a real number and a source
banned openers: Empower, Unlock, Transform, Elevate, Supercharge, Seamless
feature titles: name a thing, never pair two abstract nouns

## Commitments (the non-negotiables)
1. FOCAL POINT: <the single element carrying the most weight>
2. TENSION: <the one element that touches, bleeds, or breaks the container>
3. SIGNATURE ASSET: <one device>, appearing in <role A>, <role B>, <role C>
4. THE DECISION COMPETITORS WOULD NOT MAKE: <what it is>
5. NAMED EXCEPTION: <the one place the system is broken on purpose>
```

## Mandatory positives

A page that passes the tell audit and fails these is the bland failure. Each is checkable.

- **One dominant focal point.** One element carries the largest visual weight, and everything else is subordinate. Three elements at similar weight means the eye lands nowhere.
- **Asymmetry with numbers.** Specify a weight ratio and an offset grid. "Do not center the hero" gets satisfied by a 50/50 split, which is still symmetrical and therefore still predictable by construction.
- **One tension move.** At least one element touches the container edge, bleeds past it, overlaps a neighbor, or breaks the baseline grid. Name which one. Tension comes from proximity to edges and broken alignment; without it a composition stays inert however clean it is.
- **A decisive scale jump.** A named ratio between display and body, with the largest size reserved for the single main message. Incremental steps produce "bigger text equals header," which is the canonical AI hierarchy.
- **Differentiated spacing.** Tight gaps bind related pairs, large gaps separate sections, so grouping is legible from squint distance. One uniform gap everywhere reads as cold and ungrouped.
- **A repeated signature asset.** One ownable device appearing at least three times in different roles. Distinctive assets become recognition cues through repetition. Unrepeated novelty reads as arbitrary.
- **A named exception.** A system applied without exception produces that system's fingerprint, and uniformity is the machine signal. Break the grid or invert the palette in exactly one named place, so the system has an authored edge.
- **Complete state coverage.** Hover, focus, disabled, loading, empty, error, validation. Only-the-happy-path is the most reliable evidence nobody used the thing they built.
- **Material.** Grain, paper texture, a drawn mark, a print artifact. Pure flat fill is the state a renderer produces by default.
- **Visible editing.** Three specific testimonials rather than nine generic ones. One supported claim rather than a repeated unsupported one. Cut sections that exist to fill the template.

## Anti-convergence

If every user of this skill produces the same non-slop, the skill has manufactured a new default inside one cycle. Four guards:

1. **Parameterize per project.** Require brand inputs and refuse to run on defaults. Emit the filled `DESIGN.md` as an editable artifact.
2. **Seed the direction from outside the model.** Mode collapse is inter-model as well as intra-model, so asking any model to "be different" lands in the same basin. Pick from mutually exclusive named directions and record the pick.
3. **Derive the palette from the project's own source material.** Two sites in one direction should differ in color. `derivation.md` has the procedure.
4. **Invent the signature move per project.** It comes from the brief, never from a recipe.

## Scoring

The Slop Score alone rewards removal, and its optimum is a flat gray page with a system font and no motion: zero tells, zero decisions. Score both axes.

```
Slop Score        = 3×instant + 2×strong + 1×mild      (lower is better)
Commitment Score  = count of filled, propagated, nameable decisions
                    from the Commitments block and Mandatory positives
```

| Slop | Commitment | Verdict |
|---|---|---|
| high | low | Generic template. The starting point. |
| high | high | Loud but derivative. Fix the tells. |
| **low** | **low** | **Bland. The failure this file exists to prevent.** |
| low | high | Ship it. |

Ship gate needs both: Slop Score in 0 to 8 **and** Commitment Score of 5 or more, with every Mandatory positive present.

## Sources

eval.16x.engineer on negative instructions in LLMs · mindstudio.ai on design systems for Claude · arxiv 2508.10033 on guardrail backfire · arxiv 2510.22954 on LLM mode collapse · arxiv 2505.18949 "The Price of Format: Diversity Collapse" · nngroup.com on flat design, clickability signifiers, and critique in the AI era · dev.to/alanwest on fixing the AI-generated look · vanseodesign.com on visual tension · smashingmagazine.com on compositional balance · alistapart.com on art direction for the web · umbrex.com on Ehrenberg-Bass distinctive brand assets · marchbranding.com on blanding · bitskingdom.com on minimalism going too far · toptal.com on design constraints · 925studios.co · prg.sh · sophisticatedcloud.com · clearwhitespace.com · pageperfect.studio on optical margin alignment
