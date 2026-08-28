# Catalog 5/7: Motion & interaction (#154–183)

Scroll reveals, scroll behavior, hover/cursor effects, ambient loops, text/number theatrics, motion-system tells. Severity: **instant** / **strong** / **mild** (see SKILL.md).

Master rule for this file: **one signature motion, everything else calm.** Every fix has to respect `prefers-reduced-motion` and hold performance where it was.

## Scroll reveals

**154. Fade-up on every section** (instant)
Tell: every section enters with `opacity:0; translateY(20px)` on scroll, driven by `data-aos="fade-up"` or a framer-motion `whileInView` cloned down the page at one timing.
Why: the recipe runs on most AI-generated landing pages, and users read the wait as a slow page load.
Fix: pick one signature reveal, most often the hero, and delete the animation wrapper from every other section. Whatever survives triggers once, travels ≤12px, runs ≤400ms, and sits behind a reduced-motion guard.

**155. Identical linear stagger on card grids** (strong)
Tell: every grid's children cascade in at fixed 0.1s intervals (`staggerChildren: 0.1`, `data-aos-delay="100/200/300"`).
Why: the metronome stagger is framer-motion boilerplate, and by the third grid a reader has learned the pattern.
Fix: keep stagger on one flagship grid at most, cut the delays to 40–60ms so the whole cascade finishes under 300ms, and render the other grids with no animation at all.

**156. Alternating fade-left/fade-right sections** (strong)
Tell: zig-zag feature rows where the image slides in from one side and the text from the other, flipping every section.
Why: the paired directional slides come straight off the AOS demo page, so nobody designed the choreography.
Fix: remove the directional slides. The zig-zag layout can stay static, with the single signature reveal on the first row at most.

**157. Content invisible until scroll JS fires** (strong)
Tell: sections default to `opacity:0` in CSS, so the page flashes blank when JS is slow and stays blank when JS fails; text below the fold is unreadable at the moment a reader reaches it.
Why: users can't separate an animation wait from a broken load, so they blame the site's performance.
Fix: author the content visible by default and add the hidden class once the observer initializes (progressive enhancement). Leave no primary text at opacity 0 in the stylesheet.

**158. Reveals that re-trigger on every scroll pass** (strong)
Tell: scrolling back up and down replays every fade (AOS `once:false`, `viewport:{once:false}`), so the page keeps re-loading itself.
Why: repeat animation punishes anyone rereading a section, and it is the implementation default nobody tuned.
Fix: set every scroll reveal to fire once (`once:true`) so revisited content is there when a reader comes back.

**159. Hero load-in cascade** (instant)
Tell: on page load, badge → headline → subhead → buttons → screenshot animate in sequence over 1–2s before anything is usable.
Why: the staged entrance is template boilerplate; it pushes back LCP and the value proposition, and readers recognize the sequence on sight.
Fix: cap the entrance at one grouped fade of ≤400ms, or drop it. The headline has to be readable in the first paint, and the screenshot arrives without choreography.

**160. Preloader splash on a brochure site** (strong)
Tell: fullscreen overlay with a logo animation or a percentage counter, held in front of a static marketing page.
Why: kit authors copied this from agency portfolios; it stalls content the browser already downloaded, and every second of stall costs you visitors.
Fix: delete the preloader and fix the real load feel with `loading="lazy"`, sized media, and font preloads.

**161. Word-by-word scroll-linked text reveal** (strong)
Tell: a manifesto paragraph where each word fades from grey to white as you scroll (GSAP or framer scroll-progress text).
Why: everyone copied the Apple keynote scroll, and it ties a reader's pace to the scroll wheel.
Fix: keep body text readable on arrival. If the brand moment matters, put the effect on one short sentence and stop there.

## Scroll behavior

**162. Scroll-jacking / full-page snap sections** (strong)
Tell: wheel input runs through a handler that advances one full-screen slide per scroll (fullPage.js, scroll-snap on 100vh sections), with no native momentum left.
Why: researchers have documented what it costs: users lose control of the page, can't skim, and some get motion-sick.
Fix: remove the snap handler and restore native scrolling, keeping the same sections as stacked blocks with anchor links.

**163. Smooth-scroll momentum hijack** (strong)
Tell: scrolling feels floaty across the site because Lenis or Locomotive re-implements inertia, and the page glides past where you stopped.
Why: overriding OS scroll physics is the template idea of "premium feel", and users notice the wrongness on the first flick and call it jank.
Fix: remove the smooth-scroll library from content pages. If one effect depended on it, rebuild that effect with native CSS `scroll-behavior` or scroll-driven animations.

**164. Parallax gradient-blob layers** (strong)
Tell: decorative blobs and shapes translating at different speeds against the scroll (`useTransform(scrollY, ...)` on background layers).
Why: stock kits bolt depth theater onto flat content; it janks on mid-range phones and carries no meaning.
Fix: fix the backgrounds in place. If depth matters, keep one subtle hero layer at ≤10% differential and disable it under reduced motion.

**165. Bouncing scroll-down chevron** (mild)
Tell: `animate-bounce` ChevronDown centered at the hero's bottom edge, looping forever.
Why: scaffolds pair the default Tailwind bounce with the default Lucide chevron, on the assumption that visitors need telling that a page scrolls.
Fix: remove it when any content peeks above the fold, which covers most pages. If the hero is a true 100vh, use a static affordance.

## Hover & cursor

**166. hover:scale-105 on every card** (instant)
Tell: cards, images, and buttons all grow 5–10% on hover (`hover:scale-105 transition-transform`), the non-clickable ones included.
Why: Tailwind tutorials teach scale-on-hover, models apply it to every element in reach, and elements that do nothing on click end up promising that they will.
Fix: strip scale from everything you can't click. For real links and cards, pick one restrained treatment (a border-color shift, or 2px translate-y with a shadow step, around 150ms ease-out) and use it everywhere.

**167. 3D tilt cards tracking the mouse** (strong)
Tell: cards rotate in perspective as the cursor moves (vanilla-tilt, react-parallax-tilt), sometimes with a specular glare sliding across them.
Why: the tilt-card codepen has been a portfolio-demo flourish for years, so visitors place it as kit shopping, and it jitters on low-end devices.
Fix: delete the tilt handler and keep a static elevated card. Reserve dimensional play for one hero object where it fits the brand.

**168. Cursor-tracking spotlight/glow on cards** (strong)
Tell: a radial-gradient hotspot follows the pointer inside cards or the hero (the Aceternity "spotlight" and "card glow" pattern), indigo more often than not.
Why: every AI component kit of 2024–25 shipped this effect, so it now marks a page as generated faster than a plain card would.
Fix: remove the mousemove listener and set a static border or top-edge highlight. Spend the novelty budget on making the cards say different things.

**169. Custom cursor follower** (strong)
Tell: a lagging dot or ring stands in for the native cursor, inverting over links and sometimes dragging a trail.
Why: AI templates cargo-cult it from agency sites; it adds input latency and does nothing at all on touch.
Fix: restore the native cursor and put the interactivity into hover and focus states on the elements themselves.

## Ambient loops

**170. Particle/starfield background** (instant)
Tell: a canvas of drifting dots joined by lines (particles.js, tsParticles), or a starfield or matrix rain behind the hero.
Why: the particles hero dates to 2016, AI builders still emit it, and it burns CPU on decoration.
Fix: delete the canvas. If the hero needs texture, use a static grain layer at around 5% opacity or one fixed decorative graphic, with no per-frame work.

**171. Animated aurora / morphing gradient blobs** (strong)
Tell: giant blurred color blobs (`blur-3xl` divs or an SVG goo filter) drifting and hue-shifting behind content at a crawl, edges breathing.
Why: AI kits ship lava-lamp motion as the standard "premium" backdrop; it carries no information and costs the reader focus and battery. (Static version: #74.)
Fix: freeze it into one static radial gradient accent in a corner. If any drift stays, hold it to one element on a ≥20s cycle, paused under reduced motion.

**172. Floating/bobbing decorative shapes** (strong)
Tell: badges, coins, avatars, or geometric shards levitating around the hero on infinite `translateY` ease-in-out loops, each on its own phase offset.
Why: the "floating UI chips around a screenshot" collage is template DNA, and endless bobbing carries no message.
Fix: pin the elements into the composition, or delete the orbiters and enlarge the screenshot. If one floats, hold it to one, stopped under reduced motion.

**173. Border beam / spinning conic border** (strong)
Tell: a bright gradient segment orbiting card or button edges without pause (a conic-gradient mask animation, the "BorderBeam" kit component).
Why: 2024 AI component libraries shipped it verbatim, so anyone who has met those kits recognizes the orbit. (Static gradient ring: #86.)
Fix: use a static 1px border that steps up in contrast on hover and focus. When a card needs emphasis, get it from spacing and type weight.

**174. Shimmer sweep on text/buttons** (strong)
Tell: a diagonal white sheen wipes across the CTA or gradient headline on a timer (`animate-shimmer` background-position loop).
Why: the "shiny button" is a stock kit component, and a button that glints with no input from the user borrows the manners of ad tech.
Fix: delete the loop. Make the CTA prominent through size and contrast, and save any sheen for a one-time hover response.

**175. Pulsing CTA or badge** (strong)
Tell: `animate-pulse` on the "Most popular" pricing card or the CTA, or an `animate-ping` halo dot on the "We're live" badge, looping forever.
Why: AI scaffolds add it by reflex, and an animation that begs for attention forever wears a reader out in seconds.
Fix: remove the loop class and let size, contrast, and copy carry the CTA, keeping a hover transition as its one piece of motion.

## Text & number theatrics

**176. Typewriter hero headline** (instant)
Tell: the H1 types itself character by character behind a blinking block cursor (typed.js), often on a loop.
Why: AI drafts reach for the 90s-terminal cliché again and again, and it holds back the value proposition while the letters arrive.
Fix: print the strongest single headline as static text. If you want the terminal flavor, style a static caret glyph and leave it still.

**177. Rotating word in the headline** (strong)
Tell: "Build **faster** / **smarter** / **better**", with one gradient word flip-swapping every 2s in the H1.
Why: it is a stock template trick, and it shows a copywriter who could not commit to one claim.
Fix: commit to the word that's true, delete the rotator, and move the secondary claims into the subhead.

**178. Animated number count-ups** (instant)
Tell: a stats band where "10,000+ users / 99.9% uptime / 4.9★" spins up from 0 via CountUp.js each time it scrolls into view.
Why: odometer stats are the canonical template flourish, and readers treat a number that performs as decoration, which gets worse when the metrics are invented (#16).
Fix: set real, defensible numbers in static type with the source and date in small print. If you can't defend a number, cut it instead of animating it.

**179. Generic Lottie animations** (strong)
Tell: LottieFiles free-tier clips (rocket launch, checklist ticking, blob-person at a desk) dropped into feature sections, all in the same recognizable house style.
Why: everyone pulls from the same free library, so these clips carry the recognition problem of stock photos, and a slop page stacks 5–20 of them.
Fix: replace each Lottie with a static SVG in your icon style, or a short screen capture of the real product (muted, ≤5s, with a poster frame). Keep the motion that demonstrates the product and cut the rest.

## Motion-system tells

**180. Springy overshoot on everything** (mild)
Tell: modals, dropdowns, cards, and toasts all bounce past their target and wobble back (the default framer spring, low damping).
Why: someone read "animation equals personality" and applied one physics setting across every component.
Fix: switch UI transitions to 150–250ms ease-out tweens, and allow a spring on one playful moment that suits the brand, such as a success state.

**181. One global 300ms ease-in-out for everything** (mild)
Tell: color, transform, layout, and modal transitions all run the same `transition: all 300ms ease-in-out` (or `duration-300`).
Why: one motion token for everything is generated-code smell; designers vary duration and easing by how far a thing travels and how much it matters.
Fix: define 2–3 duration tokens (around 120ms for micro-feedback, 240ms standard, 400ms for large surfaces), use ease-out for entrances, and replace `transition: all` with named properties.

**182. No prefers-reduced-motion handling** (mild)
Tell: marquees, parallax, and reveals run at full strength with OS "reduce motion" enabled, and `@media (prefers-reduced-motion)` appears nowhere in the CSS.
Why: accessibility guards are the first thing template assembly drops, so their absence is a good proxy for code nobody reviewed.
Fix: add a global reduced-motion block that turns off loops and reveals (the AOS `disable` option, framer `useReducedMotion`) while leaving all content visible.

**183. Dead or missing interactive feedback** (mild)
Tell: decorative sections animate at length while the buttons and links carry no hover, focus, or pressed states, or hover changes nothing but the cursor.
Why: the priorities are inverted, with motion on the decoration and none on the controls people click.
Fix: give every interactive element one consistent state treatment (a ≤100ms color or underline shift, a visible focus ring, a 1px pressed offset) *before* touching any decorative motion.

## VOCAB: greppable signals for this file

- Libraries: `framer-motion` `motion/react` `whileInView` `whileHover` `staggerChildren` `AOS` `data-aos` `aos.css` `animate.css` `animate__animated` `wow.js` `gsap` `ScrollTrigger` `lenis` `@studio-freight/lenis` `locomotive-scroll` `fullpage.js` `react-scroll-parallax`
- Ambient: `particles.js` `tsparticles` `react-tsparticles` `vanta` `animate-blob` `aurora`
- Lottie: `lottie-web` `lottie-react` `@dotlottie` `lottiefiles` `.lottie`
- Counters/type: `countup` `react-countup` `odometer` `typed.js` `typewriter-effect` `react-type-animation`
- Tilt/cursor: `vanilla-tilt` `react-parallax-tilt` `cursor: none` `mousemove` (glow/spotlight handlers) `custom-cursor`
- Tailwind classes: `hover:scale-105|110` `hover:-translate-y` `transition-transform` `transition-all` `duration-300` `animate-pulse` `animate-ping` `animate-bounce` `animate-spin` `animate-marquee` `animate-shimmer` `group-hover:scale`
- Kit components: `magicui` `aceternity` `border-beam` `animated-beam` `shimmer-button` `sparkles-text` `orbiting-circles` `spotlight` `card-hover-effect`
- Checks: count elements with scroll-reveal attributes (>3 sections = tell) · search CSS for `prefers-reduced-motion` (absence = tell) · watch 10s with hands off the mouse, and anything still moving is an ambient loop

Sources: sailop.com "AI slop definitive guide 2026" · nngroup.com "Scroll animations" + "AI sparkles icon problem" · medium.com "Scrolljacking: the usability nightmare" · beamtic.com on scrolljacking · smashingmagazine.com on infinite logo scrollers · speckyboy.com particle snippets · css-tricks.com typewriter effect · moonb.io on free Lotties · 925studios.co · growthguys.tech
