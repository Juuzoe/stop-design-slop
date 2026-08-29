# CLEAN pass: strip the AI artifacts, keep the design

The default mode. It removes what is objectively wrong, rewrites what is local, adds what is safe, and **reports** everything that would need an art direction to fix properly.

It does not restyle your site. If you want the redesign, run `redesign` and follow `method.md`.

## The scope rule

Every tell falls into one of three classes. CLEAN acts on A and B, and only reports C.

| Class | Definition | CLEAN |
|---|---|---|
| **A. Artifact** | Objectively wrong whatever the design direction: a builder watermark, placeholder text, a fabricated testimonial, a dead link, a six-fingered hero image. Nobody would defend it. | Fix |
| **B. Local** | Fixable in place without touching a system-level token: copy rewrites, alt text, deleting an ambient animation, adding a focus ring, capping line length. The change does not propagate. | Fix |
| **C. Systemic** | Cannot be fixed coherently without a direction: the typeface, the palette, the radius and shadow scale, hero composition, section order, grid. | Report only |

**The hard constraint that keeps CLEAN safe:** it may not edit theme tokens, `font-family` declarations, the color palette, the radius or shadow scale, or page layout structure. A fix requiring any of those is class C by definition.

This is what prevents the patchwork failure. Incoherence comes from changing one system property in isolation, so CLEAN changes none of them. It only removes things that were added on top and rewrites content in place, which leaves the site's existing design language exactly as it found it.

## Why CLEAN still improves the page

Removal alone trends toward bland. CLEAN avoids that by pairing every removal with a local addition, none of which needs a direction:

- Delete an ambient animation, then give the interactive elements real hover, focus and active states (C52).
- Delete a fabricated stat, then state the true number with its source, or say nothing.
- Delete the emoji from a heading, then make the heading say something specific.
- Delete nothing at all in the type system, but add real punctuation (C1), `text-wrap: balance` (C11), tracking tuned by size (C14), a brand focus ring (C39) and tabular figures (C7).

Those additions raise the Commitment Score without touching a token, which is the whole trick. A site can gain human signal while keeping its existing look.

## Classification by catalog

Approximate, and the class of an individual entry can shift with context. When unsure, treat it as C and report it. Reporting is never wrong; a surprise restyle is.

### Structure and layout (#1–63): mostly C
**Fix:** fabricated proof (#14 placeholder company logos, #17 impossible social proof on a pre-launch site, #24 decorative integration grid with no integrations behind it), dead wiring (#49 dead footer links, #51 unwired newsletter), placeholder sections (#55 placeholder blog), thin reality (#54 contact page that is only a form, so add a real address), filler (#33 cards that exist to close a row, #23 the all-green comparison table), and motion-carried sections (#13 infinite logo marquee, #19 testimonial marquees, which become static).
**Report:** hero composition, grid structure, section order, spacing rhythm, symmetry, container widths, nav and footer architecture. All of it needs a direction.

### Color and effects (#64–93): mostly C
**Fix:** #68 body text failing contrast on dark, since raising the text lightness is an accessibility repair rather than a palette change. #80 a glow clipped flat by `overflow: hidden`, which is a bug. #83 a noise overlay sitting on top of content, which harms legibility. #77 free-floating decorative glow orbs, which are added elements rather than system properties.
**Report:** the palette itself, gradients, glassmorphism, radius scale, shadow system, dark-mode strategy. Changing any of these means changing all of them.

### Typography (#94–121): mostly C
**Fix:** #107 a gradient keyword, which reverts to the existing text color. #120 unmanaged line length, capped at 66ch. #116 Title Case, switched to sentence case. #113 eyebrow labels that duplicate the heading below, deleted rather than restyled.
**Report:** typeface choice, pairing, the type scale, weight system, tracking policy. These are the direction.

### Imagery and icons (#122–153): mixed, lots of A
**Fix:** every AI-image artifact (#122 garbled pseudo-text, #123 hand anatomy, #124 waxy skin, #126 impossible geometry), fake product imagery (#139 meaningless dashboard, #140 invented UI, #141 fake terminal), fabricated people (#143 stock and generated testimonial faces), placeholder assets (#151 letter-in-gradient-square favicon, #258 placeholder.svg), emoji as icons (#144), mixed icon styles unified to one set (#147), and cliché stock subjects (#128, #130, #132).
**Report:** the icon treatment system and the imagery art direction, which are style decisions.

### Motion and interaction (#154–183): almost all B
Motion excess is added noise, so deleting it is safe and touches no system property.
**Fix:** scroll reveals on every section (#154–158), the hero load cascade (#159), preloaders (#160), scroll-jacking and smooth-scroll hijack (#162, #163), particles and ambient loops (#170–175), typewriter and rotating headlines (#176, #177), count-ups (#178), `hover:scale-105` on non-clickable elements (#166), tilt and cursor effects (#167–169). Add `prefers-reduced-motion` handling (#182) and real interaction states (#183).
**Report:** only the motion *system* (#181, a single global easing), which wants a house curve from the direction.

### Copy and content (#184–251): almost all A or B, and the highest value in CLEAN
Copy fixes are local by nature, and readers detect slop through language faster than through layout. A visually untouched page with rewritten copy often reads dramatically more human.
**Fix:** every fabrication (#228 round-number herd claims, #229 implausible logo bars, #230 press bars with no coverage, #231 unsourced ratings, #232 invented percentages, #233 stage-contradicting claims, #234 security theater, #235–237 synthetic testimonials), every hygiene failure (#246 raw LLM artifacts, #247 markdown bleed-through, #248 placeholder leftovers, #249 product name drift, #250 stale copyright, #251 template-tainted legal pages), and every formula and blacklist hit rewritten with specifics.
**Report:** nothing. Copy needs no direction, only facts.

### Code and meta (#252–284): almost all A
**Fix:** all of it. Builder watermarks and subdomains, framework leftovers, default titles and favicons, missing OG tags and meta descriptions, dead links, decorative social icons, ghost contact forms, console errors, hydration warnings, missing focus states and alt text, broken heading hierarchy, unoptimized hero images, exposed secrets.
**Report:** #272, the default framework palette in the compiled CSS, which is the palette question in disguise.

## Workflow

### 1. Diagnose and classify
Run the catalogs as usual. Record each hit as `#N, where, severity, class`.

### 2. Fix class A
No judgment required. Every one of these is wrong on its own terms. When a fabrication is removed, either replace it with the true fact or leave honest silence. Never substitute a different fabrication.

### 3. Fix class B
Work through them in place. Copy first, since it carries the most signal per edit. Then motion noise, then the local visual fixes.

### 4. Add safe craft
From `craft-details.md`, the entries that need no direction: C1 real punctuation, C4 `font-synthesis: none`, C7 tabular figures, C11 `text-wrap: balance`, C12 `text-wrap: pretty`, C14 tracking by size, C20 a measured measure, C38 styled `::selection`, C39 a focus ring in an existing brand color, C45 underline craft, C52 five distinct control states, C63 and C64 empty and error states, plus content specificity (real dates, a working "last updated", credits, honest limitations).

These raise the Commitment Score while leaving the design language untouched.

### 5. Report class C
Group by what a direction would decide, and estimate the work. The report is the deliverable here, not a diff.

```markdown
## Needs a direction (not changed)

**Type** (#94 Inter throughout, #101 no pairing, #103 flat scale)
A direction would set a display face, a pairing and a scale ratio.
Fixing #94 alone would swap one default for another.

**Color** (#64 indigo-500, #72 blue-to-purple gradient, #90 shadcn defaults)
A direction would derive an owned hue and a 12-step ramp.
Changing the accent alone leaves the neutrals and semantics mismatched.

**Composition** (#2 centered hero stack, #26 icon-tile grid, #38 total symmetry)
A direction would set a grid, a focal point and one tension move.

Run `/stop-design-slop redesign` to do this properly. Estimated: <scope>.
```

### 6. Verify
Confirm the constraint held: **no diff touching theme tokens, `font-family`, the palette, the radius or shadow scale, or layout structure.** If one appears, it escaped scope, so revert it and move the entry to the C report.

Then check regressions as usual: contrast, focus visibility, page weight, functionality, mobile layout. Re-score both axes. In CLEAN, the Slop Score falls while the Commitment Score rises a little from the craft additions. It will not reach the ship gate of the redesign path, and that is expected.

## When CLEAN is the right call

- The site's design is fine and you want the AI fingerprints gone.
- Somebody else owns the design system and you may not change it.
- You are shipping soon and a redesign is out of scope.
- The site came out of a builder and needs de-watermarking before launch.
- You want the cheap high-signal wins first, then to decide about a redesign afterward.

## When to escalate

Escalate to `redesign` when the C report is where the actual problem lives: the 5-second test still says "generic" after a clean pass, the Commitment Score sits below 3, or the lineup test cannot pick your site out of five competitors. CLEAN removes the evidence that a machine made the page. Only a direction makes it look like a person chose it.
