# De-slop playbook — how to fix, what to add, how to prove it worked

The catalog files tell you what to *remove*. This file tells you how to remove it safely, what to *add* in its place, and how to verify the first impression actually flipped. Sources are real design writing on distinctiveness, not invented rules.

## 1. Fix method — surgical, never scorched-earth

1. **Fix the job, not the element.** Before touching a slop element, name the job it does (orient / persuade / prove / convert / navigate). The fix must keep doing that job. A fake logo bar's job is "prove someone uses this" → replace with one real, verifiable proof point, or honest silence — never with a different fake.
2. **Standard ≠ slop.** Navbars, pricing tables, FAQs, footers, "Sign up" buttons are conventions users depend on. The slop lives in their *styling, content, and sameness*. Keep the pattern, fix the execution.
3. **Subtract before adding.** Strip stacked default effects first — alternating section backgrounds, glow blobs, glassmorphism, gradient buttons — down to flat color, real borders, and space. Then add back only what serves this brand. Fewer effects executed well reads *crafted*; stacked defaults read *generated*.
4. **One tell, one diff.** Each catalog hit gets its own targeted change. No drive-by rewrites of things not on the findings list — that's how de-slopping turns into an accidental (worse) redesign.
5. **Brand overrides catalog.** If the "tell" is genuinely the brand (the company's actual purple, an intentional Inter-based identity), it is not slop — the fix is to use it with more intention, not to ban it. Note it in the report as kept-deliberately.
6. **A11y overrides everything.** No fix may reduce contrast (≥4.5:1 body, 3:1 large text), remove focus states, shrink tap targets, or ignore `prefers-reduced-motion`.

## 2. Identity Injection — what to ADD once slop is gone

A de-slopped site with nothing added is just quieter slop. Minimum: commit to items 1–5. The rest are options, chosen to fit the brand — not a checklist to max out.

1. **Typeface with a point of view.** Replace the default (Inter/Geist for everything) with a display face that carries character — editorial serif, quirky grotesque, or mono — paired with a quiet body font. Real size jumps between levels; ~-0.02em tracking on large headings. Type is the fastest identity carrier and the first thing pattern-matching eyes check.
2. **Derive an ownable palette.** One saturated primary derived from something only this brand owns (the product, a material, a place, the subject matter) plus a warm-or-cool neutral ramp — not slate/zinc. Color owned by *derivation* can't be reproduced by a model's statistical average. Give it one place where it does something memorable.
3. **Commit to a geometry opinion.** Pick ONE radius (0 sharp / ~1rem soft / full pill) and one border+shadow treatment; apply everywhere without exception. Committed geometry reads designed; the rounded-everything middle reads default.
4. **One signature layout move.** A single deliberate break from the symmetric center-stacked default — wall-of-type hero, asymmetric split, sticky marginalia, oversized left-aligned headline. Keep nav, forms, and checkout boring: distinctiveness with a stable UX backbone is memorable at zero usability cost.
5. **Real content everywhere.** Every number sourced, every quote attributable to a real person, every image intentional. Specificity is the single strongest anti-AI signal — reality is specific.
6. **One signature interaction (max).** One memorable branded moment — a hover physic, a custom 404, a loading line with voice — everything else calm, on one custom easing curve. Signature micro-interactions become brand memory; ambient motion noise reads generated.
7. **One texture token.** A single tactile layer — grain, paper tint, hairline 1px rules, hard offset shadows — encoded as a token and applied consistently. A signature the framework doesn't ship is exactly what defaults can't produce.
8. **Show the actual product.** Real screenshots, live embeds, actual recordings — instead of abstract 3D renders and mock gradients. (The Loom/Notion move.)
9. **Art-direct ONE imagery system.** Pick a single image language you can actually produce — product shots, commissioned illustration, founder photography — unified by one treatment (grain, duotone, consistent crop). Consistent self-produced imagery is unfakeable.
10. **Write like the founder talks.** Problem-led headlines that name the user and the job ("Track every subcontractor invoice", not "Elevate your workflow"). Test each line: would the CEO say this out loud to a customer?
11. **CTAs that name the job.** "Get a quote", "Calculate your budget", "Book a 15-min teardown" — not "Get Started"/"Learn More". Max two buttons per section. Concrete verbs prove a human thought about this user's task, and they convert better.
12. **Voice in the microcopy.** Personality in the smallest text first — button labels, form errors, tooltips, empty states, the footer line. Microcopy is the cheapest, highest-signal surface for humanity and the last place generators look.
13. **Design the neglected states.** 404, empty states, loading, form errors get the same voice and craft as the hero. AI never touches these screens, so they're where human care is most visible.
14. **Vary the section rhythm.** Single-column editorial passage → 2-col split → plain list. Never heading+paragraph+3-cards on repeat. Uniform card-grid cadence is the template's fingerprint.
15. **Editorial type confidence.** Hero type dramatically larger (not incrementally); heading leading 1.1–1.3 vs body 1.6–1.8; let text lead sections instead of decoration. Audiences trust typographic honesty more than gradient polish.
16. **Ship human evidence.** Dated changelog, signed posts with real names and faces, a public opinion or teardown somewhere. Accumulated, dated history defeats the "too new and too clean" aggregate signal.
17. **Turn one thing interactive.** One core piece of the domain as an experience — a real calculator, an explorable dataset, a choose-your-path FAQ. A domain-specific interactive artifact is impossible to template.
18. **Encode taste as tokens.** Once fonts/colors/radius/shadow/easing are chosen, write them as CSS variables / theme config, so every future edit — human or AI — inherits them instead of silently reverting to defaults.

## 3. The tests — how to prove the first impression flipped

- **5-second test.** Look at the desktop screenshot cold and write ONE sentence describing the literal first impression, before any analysis. Fail words: "generic", "template", "SaaS landing page", any tool name. Run before AND after.
- **The lineup test.** Screenshot the site next to 4–5 competitors with logos removed. Could a stranger pick this one out? If not, identity injection isn't done.
- **The squint test.** Blur/squint at the page: does anything have a distinct silhouette, or is it a centered column of rounded rectangles?
- **The text-strip test.** Imagine the page with all text removed — does anything visual remain that says who this is?
- **The read-aloud test.** Read the hero headline and one feature blurb out loud. Would a human say this to another human?
- **Regression gates.** After fixes: contrast ≥ 4.5:1 body / 3:1 large; focus visible on tab; page weight not increased; nav/pricing/CTA/contact all still present and working; mobile layout intact. Any regression = the de-slop failed, revert that change.

## 4. Building WITH AI tools without slop (PREVENT mode)

When the UI will be generated (by you or a tool like v0/Lovable/Bolt/Cursor), constrain the generator *before* it runs:

- **Reference-driven prompting.** Supply 3–5 named visual references with one line on what makes each work, a one-word brand feel, and explicit bans. Constraints force the model off its statistical mean.
- **Standing negative constraints** (paste into the build context): *no Inter/default font, no indigo-violet or blue→purple→pink gradients, no glassmorphism, no emoji icons, no pill announcement badge, no centered-stack hero unless argued for, no 3-col feature card grid by default, no fake testimonials/stats/logos, no `href="#"`, no lorem ipsum, no scroll-fade-in on every section, no "Get Started + Learn More" pair, no untouched shadcn/Tailwind theme tokens.*
- **Tokens first.** Set the theme tokens (fonts, palette, radius, shadow, easing) before generating components, so defaults can't leak in.
- **Placeholder = build-breaking bug.** Fake content never enters the repo, even "temporarily" — it has a way of shipping. If real content doesn't exist, design the section to work honestly without it, or cut the section until it does.
- **Checkpoint audits.** `quick` sweep after the first viewport renders; full audit before "done". First viewport must score 0 on instant tells.

## 5. Report template

```markdown
# Slop audit — <site/project>
**5-second verdict:** <one-sentence first impression, desktop>
**Slop Score:** <N> = 3×<instant> + 2×<strong> + 1×<mild> → <Clean / Pattern-y / Recognizably AI / Full slop>
**Top 5 tells (fix these first):** #N name, #N name, ...

## Findings
### <Category> (<file>)
- **#N <name>** (<sev>) — <where it appears on THIS site> → **Fix:** <specific change for THIS site>
...

## Kept deliberately (do-not-touch)
- <element> — <why it stays: brand asset / real content / working convention>

## De-slop plan
1. Pass 1 — instant tells, first viewport: <list>
2. Pass 2 — strong tells through the scroll: <list>
3. Pass 3 — mild tells + copy sweep: <list>
4. Pass 4 — identity injection: <the 1-2 additions chosen, with reasoning>

## After (fill on verify)
**5-second verdict:** ...   **Slop Score:** ... → ...
**Regression gates:** contrast ✓/✗ · focus ✓/✗ · weight ✓/✗ · functionality ✓/✗ · mobile ✓/✗
```

## Sources (principles)
925studios.co "AI slop web design guide" · freedesignmd.com "Why shadcn looks generic" · overpass.studio "Why SaaS websites look the same" · prg.sh "Why your AI keeps building the same purple gradient website" · aitoolpick.org "AI generated website checklist" · intothenexus.substack.com "Why do all websites look the same" · unpromptable.substack.com "5 AI website design tips" · justinmind.com on micro-interactions · fireart.studio web design trends · slopdar.com "How to tell if a website is AI generated"
