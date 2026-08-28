# De-slop playbook: how to fix, what to add, how to prove it worked

The catalog files name what to *remove*. This one covers how to remove it without breaking the site, what to put in its place, and how to check that the first impression changed. Every principle below traces back to published design writing, listed at the end.

## 1. Fix method: surgical, never scorched-earth

1. **Start from the job the element does.** Before you touch a slop element, name what it does for the reader (orient / persuade / prove / convert / navigate). Your replacement has to keep doing that. A fake logo bar exists to prove someone uses the product → swap it for one real proof point a visitor can verify, or leave the space empty. A different fake fails the same way.
2. **Conventions earn their place.** Users depend on navbars, pricing tables, FAQs, footers, and "Sign up" buttons. The slop sits in their *styling, content, and sameness*. Keep the pattern and fix the execution.
3. **Subtract before you add.** Strip the stacked default effects first (alternating section backgrounds, glow blobs, glassmorphism, gradient buttons) down to flat color, real borders, and space. Then put back what this brand needs and leave the rest out. Two effects done well hold up better than six defaults piled on each other.
4. **One tell, one diff.** Give each catalog hit its own targeted change. Leave anything that is not on the findings list alone, since drive-by rewrites are how a de-slop turns into a redesign nobody asked for.
5. **Brand overrides catalog.** When the tell is the brand itself (the company's own purple, an Inter-based identity someone chose), keep it and use it with more conviction. Record it in the report's do-not-touch section so the next reader sees it was a decision.
6. **A11y overrides everything.** No fix may reduce contrast (≥4.5:1 body, 3:1 large text), remove focus states, shrink tap targets, or ignore `prefers-reduced-motion`.

## 2. Identity Injection: what to ADD once slop is gone

Strip a site and add nothing back and you get quieter slop. Commit to items 1–5 at minimum. Treat the rest as options you pick to fit the brand, and skip the ones that do not.

1. **Typeface with a point of view.** Replace Inter or Geist everywhere with a display face that carries character (an editorial serif, an odd grotesque, a mono) over a quiet body font. Make the size jumps between levels large enough to see, and pull tracking to about -0.02em on the big headings. Readers register the type before they read a word of it.
2. **Derive an ownable palette.** Pull one saturated primary from something this brand owns: the product, a material, the place it works, the subject matter. Pair it with a neutral ramp that leans warm or cool, and leave slate and zinc behind. A model averaging its training data cannot land on a color you derived from a specific object. Give that color one place on the page where it does something people remember.
3. **Commit to a geometry opinion.** Pick ONE radius (0 sharp / ~1rem soft / full pill) and one border and shadow treatment, then apply it everywhere without exception. Hedging in the middle, 8px on every corner and a soft shadow under every card, is what a framework does when nobody chose.
4. **One signature layout move.** Break the symmetric center-stacked default in a single place: a wall-of-type hero, an asymmetric split, sticky marginalia, an oversized left-aligned headline. Keep nav, forms, and checkout boring. One strange layout over a predictable UX backbone costs the user nothing and gives them something to remember.
5. **Real content everywhere.** Source every number, attach every quote to a person who said it, and choose every image for a reason. A model can produce plausible detail. It cannot produce the detail that belongs to this company alone.
6. **One signature interaction (max).** Build one branded moment worth remembering: a hover with physics, a custom 404, a loading line with a voice. Keep everything else calm and on a single custom easing curve. People remember one good micro-interaction and tune out a page where everything moves.
7. **One texture token.** Add a single tactile layer (grain, a paper tint, hairline 1px rules, hard offset shadows), encode it as a token, and apply it across the whole site. No framework ships that layer, which is why it reads as someone's choice.
8. **Show the actual product.** Use real screenshots, live embeds, and recordings of the thing working, in place of abstract 3D renders and mock gradients. (The Loom and Notion move.)
9. **Art-direct ONE imagery system.** Pick a single image language your team can produce on schedule: product shots, commissioned illustration, founder photography. Hold it together with one treatment (grain, duotone, a fixed crop). Nobody can copy a library of images you made yourself.
10. **Write like the founder talks.** Lead with the problem and name the user and the job: "Track every subcontractor invoice" beats "Elevate your workflow". Test each line by asking whether the CEO would say it out loud to a customer.
11. **CTAs that name the job.** "Get a quote", "Calculate your budget", "Book a 15-min teardown". Retire "Get Started" and "Learn More", and cap each section at two buttons. A concrete verb shows that someone thought about what this visitor came to do, and it converts better.
12. **Voice in the microcopy.** Put the personality in the smallest text first: button labels, form errors, tooltips, empty states, the footer line. Those lines take an afternoon to write, and generators reach for them last.
13. **Design the neglected states.** Give the 404, the empty states, the loading view, and the form errors the same voice and craft as the hero. Generators skip these screens, so a visitor who lands on one finds out whether a person worked here.
14. **Vary the section rhythm.** Run a single-column editorial passage into a 2-col split into a plain list. Drop the heading + paragraph + 3-cards loop. When every section has the same shape, readers recognize the template underneath.
15. **Editorial type confidence.** Jump the hero type several steps past the body size. Set heading leading at 1.1–1.3 against body at 1.6–1.8, and let text carry a section where you would otherwise reach for decoration. Audiences trust a page that treats its words as the main event.
16. **Ship human evidence.** Keep a dated changelog, sign posts with real names and faces, and publish an opinion or a teardown somewhere. Dated history stacking up behind a site answers the "too new and too clean" signal that the rest of the audit measures.
17. **Turn one thing interactive.** Take one core piece of the domain and make it something the visitor operates: a working calculator, an explorable dataset, a choose-your-path FAQ. Nobody templates that from a prompt about your industry.
18. **Encode taste as tokens.** Once you have picked fonts, colors, radius, shadow, and easing, write them into CSS variables or theme config. Every later edit, whether a person or a model makes it, then inherits the choices instead of drifting back to defaults.

## 3. The tests: how to prove the first impression flipped

- **5-second test.** Look at the desktop screenshot cold and write ONE sentence describing your first impression, before any analysis. Fail words: "generic", "template", "SaaS landing page", any tool name. Run it before the fixes and again after.
- **The lineup test.** Screenshot the site beside 4–5 competitors with every logo removed. Could a stranger pick this one out? If not, you have more identity to inject.
- **The squint test.** Blur or squint at the page: does anything have a distinct silhouette, or is it a centered column of rounded rectangles?
- **The text-strip test.** Imagine the page with all the text removed. Does anything left on screen say whose site this is?
- **The read-aloud test.** Read the hero headline and one feature blurb out loud. Would a human say this to another human?
- **Regression gates.** After fixes: contrast ≥ 4.5:1 body / 3:1 large; focus visible on tab; page weight not increased; nav/pricing/CTA/contact all still present and working; mobile layout intact. Any regression means the de-slop failed, so revert that change.

## 4. Building WITH AI tools without slop (PREVENT mode)

When you or a tool (v0, Lovable, Bolt, Cursor) will generate the UI, constrain the generator *before* it runs:

- **Reference-driven prompting.** Give the model 3–5 named visual references with one line on why each one works, a one-word brand feel, and a list of bans. Constraints push it off its statistical mean.
- **Standing negative constraints** (paste into the build context): *no Inter/default font, no indigo-violet or blue→purple→pink gradients, no glassmorphism, no emoji icons, no pill announcement badge, no centered-stack hero unless argued for, no 3-col feature card grid by default, no fake testimonials/stats/logos, no `href="#"`, no lorem ipsum, no scroll-fade-in on every section, no "Get Started + Learn More" pair, no untouched shadcn/Tailwind theme tokens.*
- **Tokens first.** Set the theme tokens (fonts, palette, radius, shadow, easing) before you generate a single component, so the defaults have nowhere to leak in.
- **Placeholder = build-breaking bug.** Keep fake content out of the repo even as a stopgap, because stopgaps ship. When the real content does not exist, build the section to work without it, or cut the section until it does.
- **Checkpoint audits.** Run a `quick` sweep once the first viewport renders, and a full audit before you call it done. The first viewport has to score 0 on instant tells.

## 5. Report template

```markdown
# Slop audit: <site/project>
**5-second verdict:** <one-sentence first impression, desktop>
**Slop Score:** <N> = 3×<instant> + 2×<strong> + 1×<mild> → <Clean / Pattern-y / Recognizably AI / Full slop>
**Top 5 tells (fix these first):** #N name, #N name, ...

## Findings
### <Category> (<file>)
- **#N <name>** (<sev>), <where it appears on THIS site> → **Fix:** <specific change for THIS site>
...

## Kept deliberately (do-not-touch)
- <element>: <why it stays: brand asset / real content / working convention>

## De-slop plan
1. Pass 1, instant tells, first viewport: <list>
2. Pass 2, strong tells through the scroll: <list>
3. Pass 3, mild tells + copy sweep: <list>
4. Pass 4, identity injection: <the 1-2 additions chosen, with reasoning>

## After (fill on verify)
**5-second verdict:** ...   **Slop Score:** ... → ...
**Regression gates:** contrast ✓/✗ · focus ✓/✗ · weight ✓/✗ · functionality ✓/✗ · mobile ✓/✗
```

## Sources (principles)
925studios.co "AI slop web design guide" · freedesignmd.com "Why shadcn looks generic" · overpass.studio "Why SaaS websites look the same" · prg.sh "Why your AI keeps building the same purple gradient website" · aitoolpick.org "AI generated website checklist" · intothenexus.substack.com "Why do all websites look the same" · unpromptable.substack.com "5 AI website design tips" · justinmind.com on micro-interactions · fireart.studio web design trends · slopdar.com "How to tell if a website is AI generated"
