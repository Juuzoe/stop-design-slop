# Catalog 5/7 — Motion & interaction (#154–183)

Scroll reveals, scroll behavior, hover/cursor effects, ambient loops, text/number theatrics, motion-system tells. Severity: **instant** / **strong** / **mild** (see SKILL.md).

Master rule for this file: **one signature motion, everything else calm.** Every fix must respect `prefers-reduced-motion` and never regress performance.

## Scroll reveals

**154. Fade-up on every section** (instant)
Tell: each section enters with `opacity:0; translateY(20px)` on scroll — `data-aos="fade-up"` or framer-motion `whileInView` cloned down the page with identical timing.
Why: this exact recipe appears in the overwhelming majority of AI-generated landing pages; users experience it as artificial loading delay, not delight.
Fix: pick one signature reveal (usually the hero) and delete the animation wrapper from every other section; anything kept triggers once, travels ≤12px, runs ≤400ms, and sits behind a reduced-motion guard.

**155. Identical linear stagger on card grids** (strong)
Tell: every grid's children cascade in at fixed 0.1s intervals (`staggerChildren: 0.1`, `data-aos-delay="100/200/300"`).
Why: metronomic stagger is the framer-motion boilerplate fingerprint; by the third grid it reads as a template tic.
Fix: keep stagger on at most one flagship grid, cut delays to 40–60ms so it completes under 300ms total; render all other grids instantly.

**156. Alternating fade-left/fade-right sections** (strong)
Tell: zig-zag feature rows where the image slides in from one side and text from the other, alternating every section.
Why: directional slide pairs are the AOS demo page verbatim — choreography no one designed.
Fix: remove directional slides; the zig-zag layout itself can stay static, with at most the single signature reveal applied to the first row only.

**157. Content invisible until scroll JS fires** (strong)
Tell: sections default to `opacity:0` in CSS, flashing blank when JS is slow or failing entirely without it; text below the fold can't be read the instant it's reached.
Why: users can't tell animation waits from broken loading and blame the site's performance.
Fix: author content visible-by-default and add the hidden class only when the observer initializes (progressive enhancement); never leave primary text at opacity 0 in the stylesheet.

**158. Reveals that re-trigger on every scroll pass** (strong)
Tell: scrolling back up and down replays every fade (AOS `once:false`, `viewport:{once:false}`) so the page perpetually re-loads itself.
Why: repeat animation punishes re-reading — a pure implementation default no human tuned.
Fix: set every scroll reveal to fire once (`once:true`) so revisited content is simply present.

**159. Hero load-in cascade** (instant)
Tell: on page load, badge → headline → subhead → buttons → screenshot animate in sequence over 1–2s before anything is usable.
Why: staged entrances are template boilerplate that delays LCP and the value prop; the sequence itself is the recognized pattern.
Fix: cap the entrance at one grouped fade ≤400ms (or none); the headline must be readable in the first paint, and the screenshot loads without choreography.

**160. Preloader splash on a brochure site** (strong)
Tell: fullscreen overlay with logo animation or a percentage counter before revealing a static marketing page.
Why: fake loading for content that's already loaded — an agency-portfolio affectation kits reproduce; every second is pure bounce risk.
Fix: delete the preloader; solve actual load feel with `loading="lazy"`, sized media, and font preloads instead.

**161. Word-by-word scroll-linked text reveal** (strong)
Tell: a manifesto paragraph where each word fades from grey to white as you scroll (GSAP/framer scroll-progress text).
Why: the Apple-keynote-scroll imitation is the most copied recent hero trick; it hostage-takes reading speed.
Fix: keep body text instantly readable; if the brand moment matters, apply the effect to one short sentence max — never a full paragraph.

## Scroll behavior

**162. Scroll-jacking / full-page snap sections** (strong)
Tell: wheel input hijacked so each scroll advances one full-screen slide (fullPage.js, scroll-snap on 100vh sections), skipping native momentum.
Why: a documented usability nightmare — users feel loss of control, can't skim, and some get motion-sick.
Fix: remove the snap/hijack and restore native scrolling; keep the same sections as normal stacked blocks with anchor links.

**163. Smooth-scroll momentum hijack** (strong)
Tell: scrolling feels floaty/laggy sitewide — Lenis/Locomotive re-implementing inertia so the page glides past where you stopped.
Why: overriding OS scroll physics is a signature of template "premium feel"; users notice the wrongness immediately and blame jank.
Fix: remove the smooth-scroll library on content pages; if an effect depended on it, rebuild that one effect with native CSS `scroll-behavior` or scroll-driven animations.

**164. Parallax gradient-blob layers** (strong)
Tell: decorative blobs/shapes translating at different speeds against scroll (`useTransform(scrollY, ...)` on background layers).
Why: depth theater on flat content is a stock kit move; it costs jank on mid-range phones and adds zero meaning.
Fix: fix the backgrounds in place; if depth matters, one subtle hero-only layer at ≤10% differential, disabled under reduced motion.

**165. Bouncing scroll-down chevron** (mild)
Tell: `animate-bounce` ChevronDown centered at the hero's bottom edge, looping forever.
Why: the default Tailwind bounce on the default Lucide chevron — a scaffold tic that treats users as unable to scroll.
Fix: remove it if any content peeks above the fold (usually true); if the hero is truly 100vh, use a static, subtle affordance instead.

## Hover & cursor

**166. hover:scale-105 on every card** (instant)
Tell: all cards, images, and buttons grow 5–10% on hover (`hover:scale-105 transition-transform`), including non-clickable ones.
Why: uniform scale-on-hover is the Tailwind-tutorial default AI applies indiscriminately; motion on non-interactive elements lies about affordance.
Fix: remove scale from everything non-clickable; for true links/cards pick one restrained treatment (border-color shift or 2px translate-y + shadow step, ~150ms ease-out) and apply it consistently.

**167. 3D tilt cards tracking the mouse** (strong)
Tell: cards rotate in perspective following the cursor (vanilla-tilt/react-parallax-tilt), sometimes with a moving specular glare.
Why: the tilt-card codepen aesthetic is a portfolio-demo flourish that reads as template shopping, and it jitters on low-end devices.
Fix: delete the tilt handler; keep a static elevated card, and reserve dimensional play for at most one hero object if genuinely on-brand.

**168. Cursor-tracking spotlight/glow on cards** (strong)
Tell: a radial-gradient hotspot follows the pointer inside cards or the hero (the Aceternity "spotlight"/"card glow" pattern), usually indigo.
Why: this exact effect shipped in every 2024–25 AI component kit; it's now a stronger AI tell than a plain card.
Fix: remove the mousemove listener; set a static subtle border or top-edge highlight; invest the deleted novelty budget in real content differences between cards.

**169. Custom cursor follower** (strong)
Tell: native cursor replaced or shadowed by a lagging dot/ring/blob that inverts over links, sometimes with a trail.
Why: agency-site affectation that AI templates cargo-cult; it adds input latency, breaks expectations, and fails on touch.
Fix: restore the native cursor entirely; express interactivity through element hover/focus states instead.

## Ambient loops

**170. Particle/starfield background** (instant)
Tell: canvas of drifting dots with connecting lines (particles.js/tsParticles) or a starfield/matrix rain behind the hero.
Why: the 2016 particles hero is the most dated "tech" filler there is, and AI builders still emit it; it burns CPU to say nothing.
Fix: delete the canvas; if the hero needs texture, a static grain/noise layer at ~5% opacity or a single fixed decorative graphic — zero per-frame work.

**171. Animated aurora / morphing gradient blobs** (strong)
Tell: giant blurred color blobs (`blur-3xl` divs or an SVG goo filter) slowly drifting/hue-shifting behind content, edges breathing.
Why: ambient lava-lamp motion is the standard AI-kit "premium" backdrop — decorative motion with no informational job, hostile to reading and battery. (Static version: #74.)
Fix: freeze it — one static radial gradient accent in a corner; if any drift stays: one element, ≥20s cycle, paused under reduced motion.

**172. Floating/bobbing decorative shapes** (strong)
Tell: badges, coins, avatars, or geometric shards levitating around the hero on infinite `translateY` ease-in-out loops, each at slightly different phase.
Why: the "floating UI chips around a screenshot" collage is template DNA; perpetual bobbing is motion without message.
Fix: pin the elements statically into the composition (or delete the orbiters and enlarge the screenshot); if one floats, only one, stopped on reduced motion.

**173. Border beam / spinning conic border** (strong)
Tell: a bright gradient segment perpetually orbiting card or button edges (conic-gradient mask animation — the "BorderBeam" kit component).
Why: shipped verbatim from 2024 AI component libraries; the perpetual orbit screams kit assembly. (Static gradient ring: #86.)
Fix: a static 1px border that steps up in contrast on hover/focus; if emphasis is needed, use spacing and type weight, not orbiting light.

**174. Shimmer sweep on text/buttons** (strong)
Tell: diagonal white sheen periodically wiping across the CTA or gradient headline (`animate-shimmer` background-position loop).
Why: the "shiny button" is a stock kit component; unprompted glinting reads as ad-tech desperation.
Fix: delete the loop; make the CTA prominent through size/contrast, and reserve any sheen for a one-time hover response.

**175. Pulsing CTA or badge** (strong)
Tell: `animate-pulse` on the "Most popular" pricing card or CTA, or an `animate-ping` halo dot on the "We're live" badge, looping forever.
Why: a recurring AI-scaffold signature; infinite attention-begging animation fatigues users within seconds.
Fix: remove the loop class; a static high-contrast button with clear copy outperforms a throbbing one — at most a subtle transition on hover.

## Text & number theatrics

**176. Typewriter hero headline** (instant)
Tell: the H1 types itself character-by-character with a blinking block cursor (typed.js), often looping.
Why: a 90s-terminal cliché AI drafts reach for constantly; it delays the value proposition and reads as filler theater.
Fix: print the strongest single headline statically; if character flavor is wanted, style a static caret glyph without animation.

**177. Rotating word in the headline** (strong)
Tell: "Build **faster** / **smarter** / **better**" — one gradient word flip-swapping every 2s in the H1.
Why: a stock template trick that admits the copy couldn't commit to one claim.
Fix: commit to the one word that's true and delete the rotator; move secondary claims into the subhead.

**178. Animated number count-ups** (instant)
Tell: stats band where "10,000+ users / 99.9% uptime / 4.9★" spin from 0 via CountUp.js each time it scrolls into view.
Why: odometer stats are the canonical template flourish, and animating a number implies it's decorative rather than audited — doubly damning when the metrics are invented (#16).
Fix: set real, defensible numbers in static type (source/date in small text); if a number can't be defended, remove it rather than animate it.

**179. Generic Lottie animations** (strong)
Tell: LottieFiles free-tier clips — rocket launch, checklist ticking, blob-person at desk, floating charts — dropped into features (identifiable house style).
Why: everyone uses the same free animations, so they carry the same "stock motion" recognition as stock photos; a typical slop page stacks 5–20 of them.
Fix: replace each Lottie with either a static SVG in your icon style or a short real product screen-capture (muted, ≤5s, poster frame); keep only motion that demonstrates the product.

## Motion-system tells

**180. Springy overshoot on everything** (mild)
Tell: modals, dropdowns, cards, and toasts all bounce past their target and wobble back (default framer spring, low damping).
Why: uniform bounce is the "animations = personality" misread; physics applied globally with no per-component intent.
Fix: switch UI transitions to 150–250ms ease-out tweens; allow spring on at most one playful, brand-appropriate moment (e.g., a success state).

**181. One global 300ms ease-in-out for everything** (mild)
Tell: every transition — color, transform, layout, modal — uses the same `transition: all 300ms ease-in-out` (or `duration-300`).
Why: single-token motion is generated-code smell; human motion systems vary duration/easing by distance and importance.
Fix: define 2–3 duration tokens (~120ms micro-feedback, ~240ms standard, ~400ms large surfaces) with ease-out for entrances, and replace `transition: all` with named properties.

**182. No prefers-reduced-motion handling** (mild)
Tell: every marquee, parallax, and reveal runs identically with OS "reduce motion" enabled; no `@media (prefers-reduced-motion)` anywhere.
Why: accessibility guards are exactly what template assembly omits — absence correlates strongly with unreviewed generated code.
Fix: add a global reduced-motion block that disables loops and reveals (AOS `disable` option, framer `useReducedMotion`), keeping content fully visible.

**183. Dead or missing interactive feedback** (mild)
Tell: decorative sections animate lavishly while actual buttons/links have no hover, focus, or pressed states — or hover changes nothing but the cursor.
Why: inverted priorities are the AI signature — motion where nothing happens, nothing where interaction happens.
Fix: one consistent state treatment on every interactive element (≤100ms color/underline shift, visible focus ring, 1px pressed offset) *before* touching any decorative motion.

## VOCAB — greppable signals for this file

- Libraries: `framer-motion` `motion/react` `whileInView` `whileHover` `staggerChildren` `AOS` `data-aos` `aos.css` `animate.css` `animate__animated` `wow.js` `gsap` `ScrollTrigger` `lenis` `@studio-freight/lenis` `locomotive-scroll` `fullpage.js` `react-scroll-parallax`
- Ambient: `particles.js` `tsparticles` `react-tsparticles` `vanta` `animate-blob` `aurora`
- Lottie: `lottie-web` `lottie-react` `@dotlottie` `lottiefiles` `.lottie`
- Counters/type: `countup` `react-countup` `odometer` `typed.js` `typewriter-effect` `react-type-animation`
- Tilt/cursor: `vanilla-tilt` `react-parallax-tilt` `cursor: none` `mousemove` (glow/spotlight handlers) `custom-cursor`
- Tailwind classes: `hover:scale-105|110` `hover:-translate-y` `transition-transform` `transition-all` `duration-300` `animate-pulse` `animate-ping` `animate-bounce` `animate-spin` `animate-marquee` `animate-shimmer` `group-hover:scale`
- Kit components: `magicui` `aceternity` `border-beam` `animated-beam` `shimmer-button` `sparkles-text` `orbiting-circles` `spotlight` `card-hover-effect`
- Checks: count elements with scroll-reveal attributes (>3 sections = tell) · search CSS for `prefers-reduced-motion` (absence = tell) · watch 10s with hands off the mouse — anything still moving is an ambient loop

Sources: sailop.com "AI slop definitive guide 2026" · nngroup.com "Scroll animations" + "AI sparkles icon problem" · medium.com "Scrolljacking: the usability nightmare" · beamtic.com on scrolljacking · smashingmagazine.com on infinite logo scrollers · speckyboy.com particle snippets · css-tricks.com typewriter effect · moonb.io on free Lotties · 925studios.co · growthguys.tech
