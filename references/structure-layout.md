# Catalog 1/7 — Structure & layout (#1–63)

Page architecture, hero formulas, section patterns, grids, spacing, nav/footer skeletons, information architecture, mobile. Severity: **instant** = triggers "AI made this" in the first 5 seconds · **strong** = obvious on one scroll · **mild** = counts in aggregate.

## Hero construction

**1. Announcement pill badge above the hero H1** (instant)
Tell: rounded-full pill chip floating directly above the headline — "✨ Announcing our Series A", "New: v2.0 is live →" — with sparkle emoji, colored dot, or chevron, thin border, tinted background.
Why: it is the literal top block of every v0/shadcn hero template; real companies only run announcement chips when there is dated news that links somewhere.
Fix: delete unless there is actual news; if real, link it to a dated changelog/blog post and restyle as a small text link near the nav rather than a hero centerpiece.

**2. Centered single-column hero stack** (instant)
Tell: badge → oversized H1 → two-line gray subheadline → two buttons → screenshot, every element centered on the page axis in one narrow column.
Why: statistically the most common hero in LLM training data, so every generator converges on it.
Fix: keep the same content but move to an asymmetric two-column grid (copy left, visual right-anchored) or left-align the stack against a wide margin.

**3. Dual-CTA formula (solid + ghost)** (instant)
Tell: primary filled "Get Started" beside a ghost/outline "Learn More", equal size, side by side under the subheadline.
Why: the default two-button pair shipped in every hero block library; humans usually commit to one action.
Fix: one primary CTA with a specific destination; demote the secondary to an inline text link pointing somewhere concrete (docs, demo video, pricing).

**4. Floating browser-chrome product screenshot** (instant)
Tell: hero screenshot wrapped in a fake macOS/browser frame (traffic-light dots, URL bar), drop-shadowed or glowing, often tilted in perspective and cut off by the fold.
Why: standard v0/Lovable hero visual; the frame signals "mockup" rather than product.
Fix: crop to a real, legible piece of the actual UI at natural scale, annotate one real workflow, or use a short product capture — drop the decorative window chrome.

**5. Avatar-cluster + stars social-proof line under CTAs** (instant)
Tell: 3–5 overlapping circular avatars, five gold stars, and "Loved by 10,000+ developers" directly beneath the hero buttons.
Why: shipped verbatim in hero-block libraries; the avatars are stock and the number is invented.
Fix: one verifiable proof point (named customer quote, linked G2/App Store rating) or remove until real numbers exist.

**6. min-h-screen hero with dead space** (strong)
Tell: hero forced to exactly 100vh, small content island vertically centered, huge empty margins, next section reveals zero pixels above the fold.
Why: `min-h-screen flex items-center justify-center` is the generator default; humans size heroes to content and let the page peek.
Fix: size the hero to its content and let the top of the next section show above the fold to invite scrolling.

**7. 50/50 split hero (text left, visual right)** (strong)
Tell: the other default hero — perfect half-and-half split, headline stack left, illustration/screenshot right, both vertically centered, followed by three feature boxes.
Why: the pre-2024 Tailwind-template average that AI reproduces when not centering.
Fix: break the ratio (60/40 or 7/5), bleed the visual to the viewport edge, or let it overlap the section below.

**8. Full-sentence display headline dominating the viewport** (strong)
Tell: an entire sentence set at 60–96px filling the hero, pushing everything else down.
Why: generators equate "hero" with "maximum font size" regardless of copy length.
Fix: tighten the headline to a short phrase at display size and move the detail into the subheadline, or step the size down.

**9. Double-mockup hero (desktop + tilted phone)** (mild)
Tell: laptop screenshot with a smaller phone mockup overlapping its corner at an angle, both generic device frames.
Why: stock "we're multi-platform" composition from template marketplaces that AI mimics.
Fix: show one honest visual of the surface users actually live in; mention platform support in text.

## Section patterns & order

**10. Canonical section conveyor belt** (instant)
Tell: the exact scroll order hero → logo bar → 3-column features → how-it-works → testimonials → pricing → FAQ → final CTA band → mega footer.
Why: models learned this as "what a landing page is" — the average of the training corpus; every generated site that week shares it.
Fix: reorder around the buyer's actual questions, delete sections lacking real content, merge features + how-it-works into one deep product story.

**11. Eyebrow → H2 → subtitle ritual on every section** (strong)
Tell: each section opens with a centered tiny all-caps eyebrow ("FEATURES", "TESTIMONIALS"), an H2, and one gray subtitle sentence, then the content grid.
Why: the universal section-header scaffold in generated code; the *repetition* of the identical formula is the tell.
Fix: vary header treatment per section — left-align some, drop eyebrows that duplicate nav labels, let one section open with content instead of a header.

**12. Logo bar as mandatory section two** (strong)
Tell: grayscale customer-logo row titled "Trusted by leading teams" immediately after the hero, regardless of whether the product has customers.
Why: generators insert social proof positionally, not evidentially.
Fix: only real, permissioned logos; with fewer than ~5 real customers, replace the strip with one named case-study sentence.

**13. Infinite logo marquee** (strong)
Tell: auto-scrolling duplicated logo loop with faded edges, often the only motion on the page.
Why: a one-prompt add-on component that reads as template; looping hides how few logos exist.
Fix: static, generously spaced row of real logos; reserve a marquee for genuinely long lists (12+), and keep it pausable.

**14. Placeholder company logos** (instant)
Tell: "trusted by" strip contains gray text names — Acme Corp, TechCorp, Globex, Initech — or obviously generated marks.
Why: the model fills the slot with fictional companies when none are supplied.
Fix: delete the section entirely until real logos exist; fabricated logos are a trust liability, not decoration.

**15. Three-numbered-steps "How it works"** (strong)
Tell: exactly three circles labeled 01/02/03 joined by a connector line, each with icon, title, and one sentence — regardless of the product's real flow.
Why: a named vibe-code pattern; real onboarding rarely has exactly three abstract steps.
Fix: show the actual flow with real UI states as visuals, use however many steps reality has, annotate screenshots instead of abstract numbered circles.

**16. Four-stat metrics banner** (strong)
Tell: one row of four big numbers with small labels — "10K+ users / 99.9% uptime / 4.9★ / 24/7 support" — often between hero and features.
Why: "big number, small label, three supporting stats — used everywhere, trusted nowhere"; the numbers are usually invented.
Fix: keep only metrics you can source and date, place them in narrative next to the claim they support, delete the rest.

**17. Impossible social proof on a pre-launch site** (instant)
Tell: a waitlist/beta product displaying "Trusted by 10,000+ professionals", a testimonial wall, and enterprise logos alongside "Join the waitlist".
Why: the logical contradiction (zero-traffic site, five-figure userbase) outs the generator instantly.
Fix: honest traction — "In private beta with 12 teams since May" — specificity converts better than fiction.

**18. Uniform testimonial card wall** (strong)
Tell: 3-column grid of identical cards, each avatar + name + title + five stars + a quote of suspiciously equal length and enthusiasm.
Why: every card gets the same layout math with zero asymmetric breaks — real quotes vary wildly in length and specificity.
Fix: fewer, longer, verifiable testimonials with full names, companies, and links; feature one as a large pull-quote and let the rest differ in size.

**19. Opposing-direction testimonial marquees** (strong)
Tell: two or three rows of testimonial cards auto-scrolling horizontally in alternating directions.
Why: a signature v0/Magic-UI component; motion applied to trust content signals decoration over evidence.
Fix: make testimonials static and readable; if genuinely many, a filterable or paginated static grid preserves them all.

**20. Three-tier pricing with sanctified middle card** (strong)
Tell: Starter/Pro/Enterprise cards, middle one scaled up or ring-bordered with "Most Popular", all three with near-identical checkmark lists differing by one line.
Why: the most templated pricing composition on the internet, reproduced by default with invented prices.
Fix: keep tiers but make differences real — distinct feature sets, actual prices, a badge only if backed by data; consider a usage slider or comparison table if that matches the real model.

**21. Ritual FAQ accordion** (mild)
Tell: 5–6 chevron accordion rows in a narrow centered column titled "Frequently asked questions", just before the footer, with questions no user asked.
Why: generators append an FAQ as a structural obligation; the accordion hides thin answers.
Fix: source questions from real users/support; if few, show answers as visible text; move objection-handling next to the section it concerns (pricing questions at pricing).

**22. "Ready to get started?" final CTA band** (strong)
Tell: full-width colored band above the footer with a centered H2 ("Ready to get started?" / "Start building today"), one sentence, and a white button.
Why: the terminal block of the canonical template; phrasing and placement interchangeable across thousands of generated sites.
Fix: keep a closing CTA but make it specific to product and audience, and vary its structure — e.g., side-by-side with a proof point or a founder note instead of the centered band.

**23. All-green-vs-all-red comparison table** (mild)
Tell: "Why choose us" table where your column is entirely green checks and the competitor column entirely red X marks.
Why: generated competitive sections optimize for the pattern, not the truth; no real comparison is a shutout.
Fix: compare on real dimensions including one honest tradeoff, name sources, link claims — credibility beats symmetry.

**24. Decorative integration grid** (mild)
Tell: "Works with your favorite tools" wall or orbit of famous app icons (Slack, Notion, Figma) with no actual integrations behind them.
Why: the integration cloud is a stock credibility section added regardless of shipped functionality.
Fix: show only live integrations and link each icon to its setup docs; if none exist, cut the section.

## Grids & cards

**25. Everything-in-threes composition** (strong)
Tell: the whole page beats in triplets — 3 features, 3 steps, 3 testimonials, 3 tiers, 3 values — because grids default to three columns.
Why: content was generated to fill the layout rather than the layout built for content.
Fix: let real content set counts — a 2-item or 5-item section is a humanity signal; break one triplet into spotlight-plus-list.

**26. Icon-tile feature card grid** (instant)
Tell: 3×2 grid of identical rounded cards, each with a small rounded-square icon tile, bold short title, and exactly two lines of gray text.
Why: the "universal AI feature-card template" — the default AI homepage layout.
Fix: promote the 1–2 features that matter into full-width sections with real product UI, demote the rest to a compact inline list, vary card size by importance.

**27. Bento grid with no content logic** (strong)
Tell: trendy mixed-size bento boxes where cell size has no relationship to content — a double-width cell holding one icon and four words.
Why: bento became the 2024–25 default and AI applies it as pure decoration.
Fix: size cells by what they hold (screenshot large, single fact small) or collapse to a simpler grid; every cell must earn its area with real substance.

**28. Metronomic zig-zag feature rows** (strong)
Tell: three-plus alternating image/text rows at exact 50/50, same gap, same image treatment, flipping left-right-left.
Why: the "alternating sections" loop is the generator's answer to "more features" — the *perfect* alternation rhythm is the tell.
Fix: vary the ratio per row, let one row go full-bleed or stack, anchor rows with genuinely different visual types (screenshot, diagram, quote).

**29. Card grid as the only content container** (strong)
Tell: features, testimonials, blog posts, team, stats, and FAQ all rendered as the same rounded card in the same grid.
Why: the card is the model's universal container — "those same card layouts."
Fix: give each content type its native form — quotes as typographic pull-quotes, steps as a flow, stats inline in prose, prose as prose; reserve cards for genuinely card-shaped content.

**30. Cards nested inside cards** (strong)
Tell: rounded bordered containers inside rounded bordered containers, sometimes three levels deep.
Why: generators wrap everything defensively; nesting creates noise and fake depth.
Fix: flatten the hierarchy; group with spacing, typography, and dividers instead of nested boxes.

**31. Equal-height cards with stretched copy** (strong)
Tell: every card in a row pixel-identical in height because copy was visibly padded or truncated to match.
Why: AI writes content to fit the layout instead of fitting layout to content.
Fix: allow natural card heights (align tops), or restructure so different-length content isn't forced into twins.

**32. Grids that are always perfectly full** (mild)
Tell: item counts are always exact multiples of the column count — 6 features, 3 testimonials, 9 logos — in every section.
Why: the generator invents or trims content to complete rows; reality rarely divides evenly.
Fix: keep the true count and design for remainders (featured first item, asymmetric last row) rather than padding content.

**33. Filler cards completing the grid** (mild)
Tell: the last cell is "And much more...", "Your feature here", or a near-duplicate of another card, existing only to close the row.
Why: pure layout-filling — content generated in service of the grid.
Fix: delete filler and reflow the grid to the honest count.

## Containers, spacing & alignment

**34. One max-width container for the entire page** (strong)
Tell: every section constrained to the same centered `max-w-7xl` box — no full-bleed moments, no breakouts, identical gutters top to bottom.
Why: generated sections all copy the same wrapper; human layouts vary measure by content type.
Fix: vary container widths (narrow ~65ch for prose, wide for tables, full-bleed for key visuals); let one element per page break its container.

**35. Identical vertical padding on every section** (strong)
Tell: metronomic `py-20`/`py-24` rhythm — the page scrolls as evenly spaced slabs.
Why: monotonous spacing is a named slop pattern; humans compress related sections and open space around key moments.
Fix: tighten gaps between tightly coupled sections, expand space only around the 1–2 moments that deserve emphasis.

**36. Uniform grid gutters everywhere** (mild)
Tell: the same `gap-8` between logos, feature cards, pricing tiers, and footer columns regardless of content density.
Why: one spacing token applied globally is averaging, not design.
Fix: tighten gutters for dense small items (logos, tags), widen for large cards, so grouping reads intentionally.

**37. Empty-at-scale desktop layout** (strong)
Tell: at 1440px+ the page is mostly whitespace — small content islands floating in voids.
Why: responsive-by-default templates grow margins instead of layouts at large viewports; generous whitespace standing in for design decisions.
Fix: add real wide-viewport variants (extra column, larger visual, side-by-side sections) instead of inflating margins.

**38. Perfect mirror symmetry throughout** (strong)
Tell: every section balances exactly around the vertical center axis; nothing is off-grid, offset, or edge-anchored anywhere.
Why: symmetry is the zero-risk average; total absence of asymmetry reads as machine output.
Fix: deliberate asymmetry in 2–3 places — offset a section heading, run a 2/3–1/3 split, anchor one visual to the viewport edge.

**39. Center-aligned everything, including body text** (instant)
Tell: every heading, multi-line paragraph, button group, and list down the whole page is `text-center`.
Why: generators inherit the centered hero and propagate centering globally; centered multi-line body copy is a classic non-designer/AI tell.
Fix: left-align body text and most section content; reserve centering for short standalone statements (hero headline, CTA band).

**40. Hermetically sealed section slabs** (strong)
Tell: sections are strict horizontal bands stacked like plates — no element ever overlaps a boundary, no layering, no z-depth.
Why: generated markup is a linear list of `<section>` blocks; crafted sites let a visual straddle two sections.
Fix: pull one visual across a section boundary (negative margin/overlap) — one such moment breaks the slab rhythm.

**41. Alternating white/gray section stripes** (strong)
Tell: sections separated purely by alternating `bg-white` / `bg-gray-50`, the stripe flip being the only sectioning device.
Why: the zebra-stripe fallback is how templates fake structure without layout variety.
Fix: separate sections through spacing and layout change; use background shifts only for true context changes (e.g., pricing), not every other block.

**42. Uniform section heights and scroll cadence** (mild)
Tell: nearly every section occupies roughly the same viewport height; scrolling feels like flipping identical slides.
Why: each section was generated independently to the same template depth.
Fix: vary density — one short punchy band (a single sentence) between deep sections, and one long-form section.

## Navigation

**43. Navbar formula: logo left / links center / CTA right** (instant)
Tell: full-width 64px navbar — logo left, 4–5 links dead center, "Sign in" + filled "Get Started" right — identical across v0, Lovable, and Bolt outputs.
Why: the highest-probability nav in training data; all three tools produce it for the same prompt.
Fix: keep usability but break the template — group links beside the logo, add real destinations (Docs, Changelog), vary the CTA treatment. Restructure navigation, never remove it.

**44. Floating detached pill navbar** (strong)
Tell: rounded-full navbar floating with visible margin below the top edge, drop-shadowed, hovering over content.
Why: a signature v0-era component that spread through generated sites in 2024–25.
Fix: dock the nav to the top or square it off; keep the pill only if rounded geometry is a genuine brand motif used elsewhere.

**45. Anchor-only navigation IA** (strong)
Tell: every nav link (Features, Pricing, FAQ) is a `#fragment` scrolling the same single page; no second route exists.
Why: generators produce one page, so navigation can only point inward — a structural fingerprint of one-shot generation.
Fix: build the 2–3 real pages the business needs (about, contact/docs, legal) and link them; keep anchors as secondary in-page nav.

**46. Nav mirrors the section list one-to-one** (mild)
Tell: nav labels are exactly the homepage sections in scroll order — a table of contents, not an information architecture.
Why: nav was generated from the same section list as the page body.
Fix: organize nav by user tasks (Product, Docs, Pricing, Company) rather than scroll positions.

**47. Every CTA on the page targets the same URL** (mild)
Tell: nav button, hero pair, band CTA, and all three pricing buttons point to the identical /signup with identical labels.
Why: one CTA value propagated through the template; real funnels differentiate intent.
Fix: differentiate destinations and labels by context — trial vs. demo vs. docs vs. contact-sales on the enterprise tier.

## Footer

**48. Mega-footer formula on a tiny site** (instant)
Tell: logo + tagline + social icons column plus 3–4 link columns headed Product / Company / Resources / Legal, closing © bar — under a one-page site.
Why: the enterprise footer scaffold generated wholesale; its scale mismatches the site above it.
Fix: right-size to reality — a single-row footer with links that actually exist — and let it grow as pages are added.

**49. Dead footer links** (strong)
Tell: footer links with `href="#"` or pointing to /careers, /blog, /press pages that were never created.
Why: links were part of the template, not the site — unproofread generation.
Fix: remove links to nonexistent pages and actually create the legally required ones (privacy, terms) with real content.

**50. Footer/site disproportion** (strong)
Tell: 30–40 footer links, a language selector, and app-store badges beneath a single-feature waitlist page.
Why: footer complexity signals company scale; the mismatch reads as costume.
Fix: prune to the real link set; a small honest footer builds more trust than an aspirational mega-footer.

**51. Unwired newsletter block** (mild)
Tell: "Subscribe to our newsletter" input + button in the footer that posts nowhere or has no provider attached.
Why: the newsletter slot ships with the footer template whether or not a newsletter exists.
Fix: connect it to a real list with a real cadence, or remove the block.

## Information architecture & pages

**52. Single-landing-page-only information architecture** (strong)
Tell: the entire "company" is one route — no about, contact, blog, docs, changelog, or GitHub link anywhere.
Why: sites lacking an about page with names, dated posts, and a changelog lack the structural evidence of a real project.
Fix: add a minimal but genuine about page (names, faces, why), a contact page with real channels, and legal pages — three small real pages beat ten generated sections.

**53. Thin centered about page** (strong)
Tell: /about is one centered mission paragraph in a narrow column — no names, photos, dates, or location.
Why: the model can generate mission-speak but not biography; the structural emptiness is visible in seconds.
Fix: add concrete facts — founder names and photos, founding date, city, the actual origin story. Three sentences of specifics transforms it.

**54. Contact page that is only a form** (strong)
Tell: /contact is exactly a name/email/message form — no email address, phone, physical address, or response-time expectation.
Why: the contact form is a component; contact *information* is a business reality the generator doesn't have.
Fix: publish a real monitored email address (and any other real channel) alongside the form, plus expected response time.

**55. Placeholder blog section** (strong)
Tell: "From our blog" grid or /blog with three template cards — generic covers, "Blog post title here", or undated generic posts.
Why: a blog scaffold without dated content is negative proof.
Fix: remove the blog until 2–3 real dated posts exist; never ship placeholder cards.

**56. Zero temporal texture** (mild)
Tell: every page pixel-consistent and same-day new — no dates, no changelog, no old URLs, no slightly inconsistent legacy page anywhere.
Why: real sites accrete inconsistency over time; simultaneous generation has no history.
Fix: add a dated changelog or release notes and date all published content — visible history is unfakeable structure.

**57. Structure outrunning content** (strong)
Tell: full 10-section landing architecture (logos, stats, testimonials, FAQ, blog) wrapping a product with one feature and no users — sections exist as labeled shells with near-zero information.
Why: the template's ambition exposes the content's absence — "they all looked the same and none had the information you were looking for."
Fix: cut the page to only sections with real substance; a short specific page outperforms a long empty one and stops pattern-matching to slop.

## Mobile

**58. Source-order single-column mobile collapse** (strong)
Tell: on mobile every grid stacks in DOM order — zig-zag rows become image/text/image/text monotony, the logo bar becomes a logo tower, nothing reprioritized.
Why: `grid-cols-1 md:grid-cols-3` is responsive-by-default, not designed-for-mobile.
Fix: adjust per breakpoint — consistent text-before-image order, collapse the logo strip to one row, convert steps to a vertical timeline, hide decorative duplicates.

**59. Desktop spacing preserved on mobile** (mild)
Tell: `py-24` section gaps and giant hero margins retained at 375px, making mobile mostly empty scrolling between islands.
Why: the uniform spacing scale was never revisited per breakpoint.
Fix: halve section padding at small breakpoints and tighten intra-section gaps so density matches the device.

**60. Full-screen hamburger overlay for five links** (mild)
Tell: mobile hamburger opens a 100vh overlay with five giant centered anchor links — for a one-page site.
Why: the overlay menu is the template's mobile nav regardless of nav size.
Fix: compact dropdown sized to the actual link count, or surface the 1–2 links that matter inline next to the logo.

**61. Mobile hero pushing every CTA below the fold** (mild)
Tell: stacked badge + headline + subhead + two full-width buttons + screenshot means the first mobile screen contains only a headline fragment.
Why: the desktop-centered stack was collapsed without re-editing for the small viewport.
Fix: on mobile drop the badge, shorten the subhead, keep one CTA, let the screenshot follow — get action above the fold.

## App shells

**62. Dashboard KPI-shell template (vibe-coded apps)** (strong)
Tell: app opens on the universal admin shell — sidebar left, four equal stat cards across the top, a line-chart card, a table card below.
Why: the default dashboard scaffold every generator produces before knowing what the app does.
Fix: design the opening screen around the user's actual first task; size cards by importance; delete KPI cards with no real data behind them.

**63. Lone waitlist card page** (mild)
Tell: pre-launch site is a single centered card — headline, one sentence, email input, "Join the waitlist" — floating in a decorated void.
Why: the canonical one-prompt output for "make me a waitlist page."
Fix: keep the form but add substance around it — what the product does, who it's for, one real visual or founder note.

## VOCAB — greppable/measurable signals for this file

- Class patterns: `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` · `container mx-auto` · repeated `py-16|py-20|py-24|py-32` on every section · `min-h-screen flex flex-col items-center justify-center` · page-wide `text-center` · `grid grid-cols-1 md:grid-cols-3 gap-8` · `grid-cols-2 lg:grid-cols-4` · `inline-flex items-center rounded-full border px-3 py-1 text-sm` (pill badge) · `-space-x-2|-space-x-3` (avatar cluster) · `bg-gray-50`/`bg-muted` stripes · `h-16` + `flex items-center justify-between` (navbar) · `animate-marquee` · `aspect-video rounded-xl shadow-2xl` (hero shot) · `sticky top-0 z-50`
- Anchors as the whole nav: `#features` `#how-it-works` `#testimonials` `#pricing` `#faq` `#contact`
- Component names: Hero, Navbar, LogoCloud/TrustedBy, Features, HowItWorks, Stats, Testimonials, Pricing, FAQ, CTA/CallToAction, Footer, BentoGrid, SocialProof, Waitlist
- Section strings: "Trusted by" · "Loved by" · "How it works" · "Why choose us" · "What our customers say" · "Simple, transparent pricing" · "Frequently asked questions" · "Ready to get started?" · "Most Popular" · "Join the waitlist" · "10,000+" "99.9%" "4.9/5" "24/7"
- Placeholder tells: "Acme Corp" "TechCorp" "Globex" "Initech" · `href="#"` · footer columns exactly Product/Company/Resources/Legal · "[Your Company]" · "Blog post title here"
- Ratios to measure: identical section padding across all sections · all grids exactly 3 columns · item counts ≡ 0 mod columns · one max-width for 100% of sections · 0 elements crossing section boundaries · 100% centered headings · nav = 4–5 links + 1 filled CTA · 1 route in the sitemap

Sources: developersdigest.tech "AI design slop and how to spot it" · impeccable.style/slop · sikora.software "AI website design" · slopdar.com detection guide · shuffle.dev "Why do most AI-generated websites look the same" · axe-web.com "AI website design sameness" · uibakery.io "Lovable vs Bolt vs v0" · shadcn.io block library · freedesignmd.com lexicon · writerdock.in UI trends 2026 · nataliewritesthings.substack.com "No one wants to Get Started" · HN threads 43502363/49024805
