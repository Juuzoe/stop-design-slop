# Catalog 1/7: Structure & layout (#1–63)

Page architecture, hero formulas, section patterns, grids, spacing, nav/footer skeletons, information architecture, mobile. Severity: **instant** = triggers "AI made this" in the first 5 seconds · **strong** = obvious on one scroll · **mild** = counts in aggregate.

## Hero construction

**1. Announcement pill badge above the hero H1** (instant)
Tell: rounded-full pill chip sitting above the headline, reading "✨ Announcing our Series A" or "New: v2.0 is live →", with a sparkle emoji or colored dot, thin border, tinted background.
Why: v0 and shadcn put this block at the top of every hero template they ship. Companies with real news date it and link it somewhere.
Fix: delete the chip when you have no news. With news, point it at a dated changelog or blog post and restyle it as a small text link near the nav.

**2. Centered single-column hero stack** (instant)
Tell: badge → oversized H1 → two-line gray subheadline → two buttons → screenshot, every element centered on the page axis in one narrow column.
Why: this is the most common hero in LLM training data, so every generator converges on it.
Fix: keep the content and move it into an asymmetric two-column grid (copy left, visual right-anchored), or left-align the whole stack against a wide margin.

**3. Dual-CTA formula (solid + ghost)** (instant)
Tell: primary filled "Get Started" beside a ghost/outline "Learn More", equal size, side by side under the subheadline.
Why: every hero block library ships this button pair as its default. Humans commit to one action.
Fix: run one primary CTA with a specific destination, and demote the secondary to an inline text link pointing at something concrete (docs, a demo video).

**4. Floating browser-chrome product screenshot** (instant)
Tell: hero screenshot wrapped in a fake macOS/browser frame (traffic-light dots, URL bar), drop-shadowed or glowing, often tilted in perspective and cut off by the fold.
Why: v0 and Lovable reach for this hero visual by default, and visitors read the window frame as a sign of a mockup.
Fix: crop to a legible piece of the real UI at natural scale and annotate one workflow, or record a short product capture. Drop the decorative window chrome.

**5. Avatar-cluster + stars social-proof line under CTAs** (instant)
Tell: 3–5 overlapping circular avatars, five gold stars, and "Loved by 10,000+ developers" beneath the hero buttons.
Why: hero-block libraries ship this line verbatim. The avatars come from stock sets and the model invents the number.
Fix: show one verifiable proof point, such as a named customer quote or a linked G2/App Store rating. Remove the line until you have real numbers.

**6. min-h-screen hero with dead space** (strong)
Tell: hero forced to 100vh, a small content island floating at its center, huge empty margins, and zero pixels of the next section above the fold.
Why: `min-h-screen flex items-center justify-center` is the generator default. Designers size heroes to their content and let the page peek.
Fix: size the hero to what it holds, so the top of the next section shows above the fold and invites a scroll.

**7. 50/50 split hero (text left, visual right)** (strong)
Tell: the fallback hero when the generator skips centering. An even half-and-half split, headline stack left, illustration or screenshot right, both aligned on the vertical axis, followed by three feature boxes.
Why: this was the pre-2024 Tailwind-template average, and models reproduce it.
Fix: break the ratio to 60/40 or 7/5, and bleed the visual past the viewport edge or over the section below.

**8. Full-sentence display headline dominating the viewport** (strong)
Tell: an entire sentence set at 60–96px filling the hero and pushing everything else down.
Why: generators equate "hero" with "maximum font size" whatever the copy length.
Fix: cut the headline to a short phrase at display size and move the detail into the subheadline, or step the size down.

**9. Double-mockup hero (desktop + tilted phone)** (mild)
Tell: laptop screenshot with a smaller phone mockup overlapping its corner at an angle, both in generic device frames.
Why: template marketplaces sell this "we're multi-platform" composition, and models copy it.
Fix: show one honest visual of the surface users live in, and mention platform support in text.

## Section patterns & order

**10. Canonical section conveyor belt** (instant)
Tell: the same scroll order every time, hero → logo bar → 3-column features → how-it-works → testimonials → pricing → FAQ → final CTA band → mega footer.
Why: models learned this order as the definition of a landing page, averaged out of the training corpus, and every site generated that week shares it.
Fix: reorder around the questions buyers ask, delete sections with no real content behind them, and merge features and how-it-works into one deep product story.

**11. Eyebrow → H2 → subtitle ritual on every section** (strong)
Tell: each section opens with a centered tiny all-caps eyebrow ("FEATURES", "TESTIMONIALS"), an H2, and one gray subtitle sentence, then the content grid.
Why: generated code uses this scaffold for every section header, and the repetition of the identical formula gives it away.
Fix: vary the header treatment per section. Left-align some and drop eyebrows that repeat nav labels, then open at least one section with content and no header at all.

**12. Logo bar as mandatory section two** (strong)
Tell: grayscale customer-logo row titled "Trusted by leading teams" right after the hero, whether or not the product has customers.
Why: the generator fills the slot by position and never checks whether the evidence exists.
Fix: show real, permissioned logos. Below about five customers, replace the strip with one named case-study sentence.

**13. Infinite logo marquee** (strong)
Tell: auto-scrolling duplicated logo loop with faded edges, often the one piece of motion on the page.
Why: one prompt adds this component, and the loop covers how few logos exist.
Fix: lay out real logos in a static row with wide spacing. Reserve a marquee for lists of 12 or more, and keep it pausable.

**14. Placeholder company logos** (instant)
Tell: the "trusted by" strip carries gray text names such as Acme Corp, TechCorp, Globex, and Initech, or marks the model drew itself.
Why: the model fills the slot with fictional companies when nobody supplies real ones.
Fix: delete the section until you have real logos. Fabricated logos cost you trust.

**15. Three-numbered-steps "How it works"** (strong)
Tell: three circles labeled 01/02/03 joined by a connector line, each with icon, title, and one sentence, whatever the product's real flow looks like.
Why: this is a named vibe-code pattern, and few real onboarding flows come out to three abstract steps.
Fix: show the flow you ship, using real UI states as visuals and as many steps as it takes. Annotate screenshots in place of abstract numbered circles.

**16. Four-stat metrics banner** (strong)
Tell: one row of four big numbers with small labels ("10K+ users / 99.9% uptime / 4.9★ / 24/7 support"), often sitting between hero and features.
Why: "big number, small label, three supporting stats — used everywhere, trusted nowhere"; the model invents the figures.
Fix: keep the metrics you can source and date, and put each one next to the claim it supports. Cut the rest.

**17. Impossible social proof on a pre-launch site** (instant)
Tell: a waitlist or beta product showing "Trusted by 10,000+ professionals", a testimonial wall, and enterprise logos beside "Join the waitlist".
Why: a zero-traffic site claiming a five-figure userbase contradicts itself, and readers catch it in one glance.
Fix: state traction a reader can check, such as "In private beta with 12 teams since May".

**18. Uniform testimonial card wall** (strong)
Tell: 3-column grid of identical cards, each with avatar, name, title, five stars, and a quote of near-equal length and enthusiasm.
Why: every card runs the same layout math with no asymmetric break, while real quotes vary in length and specificity.
Fix: use fewer, longer testimonials with full names, companies, and links. Pull one out as a large quote and let the others differ in size.

**19. Opposing-direction testimonial marquees** (strong)
Tell: two or three rows of testimonial cards auto-scrolling in alternating directions.
Why: this is a signature v0 and Magic-UI component, and putting trust content in motion turns evidence into decoration.
Fix: hold testimonials still and readable. For a large set, a filterable or paginated static grid keeps them all.

**20. Three-tier pricing with sanctified middle card** (strong)
Tell: Starter/Pro/Enterprise cards, the middle one scaled up or ring-bordered with "Most Popular", all three carrying near-identical checkmark lists that differ by one line.
Why: this is the most templated pricing composition on the internet, and models reproduce it with invented prices.
Fix: keep the tiers and make the differences real, with distinct feature sets and actual prices, plus a badge when the data supports one. A usage slider or comparison table may fit your model better.

**21. Ritual FAQ accordion** (mild)
Tell: 5–6 chevron accordion rows in a narrow centered column titled "Frequently asked questions", placed before the footer, answering questions no user asked.
Why: the generator appends an FAQ to satisfy the structure, and the accordion hides how thin the answers are.
Fix: pull questions from users and support tickets. With few of them, show the answers as visible text, and move objection-handling next to the section it concerns (pricing questions at pricing).

**22. "Ready to get started?" final CTA band** (strong)
Tell: full-width colored band above the footer with a centered H2 ("Ready to get started?" / "Start building today"), one sentence, and a white button.
Why: this is the terminal block of the canonical template, and its phrasing and placement swap between thousands of generated sites without changing.
Fix: keep a closing CTA, write it for your product and audience, and vary the structure. Set it side by side with a proof point or a founder note in place of the centered band.

**23. All-green-vs-all-red comparison table** (mild)
Tell: "Why choose us" table where your column carries green checks all the way down and the competitor column carries red X marks.
Why: generated competitive sections optimize for the pattern and skip the truth. No real comparison ends in a shutout.
Fix: compare on real dimensions, include one honest tradeoff, and link each claim to its source.

**24. Decorative integration grid** (mild)
Tell: "Works with your favorite tools" wall or orbit of famous app icons (Slack, Notion, Figma) with no integrations behind them.
Why: the generator adds an integration cloud as stock credibility whatever functionality shipped.
Fix: show live integrations and link each icon to its setup docs. With none built, cut the section.

## Grids & cards

**25. Everything-in-threes composition** (strong)
Tell: the whole page beats in triplets, 3 features, 3 steps, 3 testimonials, 3 tiers, 3 values, because grids default to three columns.
Why: the model wrote content to fill the layout instead of building the layout for the content.
Fix: let real content set the counts. A 2-item or 5-item section reads as human, and one triplet can become a spotlight plus a list.

**26. Icon-tile feature card grid** (instant)
Tell: 3×2 grid of identical rounded cards, each with a small rounded-square icon tile, bold short title, and two lines of gray text.
Why: this is the universal AI feature-card template, the default AI homepage layout.
Fix: promote the one or two features that matter into full-width sections with real product UI, drop the rest into a compact inline list, and size cards by importance.

**27. Bento grid with no content logic** (strong)
Tell: trendy mixed-size bento boxes where cell size bears no relationship to content, such as a double-width cell holding one icon and four words.
Why: bento became the 2024–25 default and models apply it as decoration.
Fix: size cells by what they hold, so a screenshot gets a large one and a single fact gets a small one. Collapse to a simpler grid when the cells cannot earn their area.

**28. Metronomic zig-zag feature rows** (strong)
Tell: three or more alternating image/text rows at an even 50/50, same gap, same image treatment, flipping left-right-left.
Why: the "alternating sections" loop is how the generator answers a request for more features, and the rhythm never breaks.
Fix: vary the ratio per row, let one row go full-bleed or stack, and anchor rows with different visual types (screenshot, diagram, quote).

**29. Card grid as the only content container** (strong)
Tell: features, testimonials, blog posts, team, stats, and FAQ all render as the same rounded card in the same grid.
Why: the model treats the card as a universal container, producing "those same card layouts."
Fix: give each content type its native form, so quotes become typographic pull-quotes, steps become a flow, and stats sit inline in prose. Save cards for content that is card-shaped.

**30. Cards nested inside cards** (strong)
Tell: rounded bordered containers inside rounded bordered containers, sometimes three levels deep.
Why: the generator wraps everything for safety, and the nesting adds noise and fake depth.
Fix: flatten the hierarchy and group with spacing, typography, and dividers.

**31. Equal-height cards with stretched copy** (strong)
Tell: every card in a row matches its neighbors to the pixel because someone padded or truncated the copy to match.
Why: the model writes content to fit the layout instead of fitting the layout to the content.
Fix: let cards take their natural heights and align their tops, or restructure so copy of different lengths never gets forced into twins.

**32. Grids that are always perfectly full** (mild)
Tell: item counts land on multiples of the column count in every section, at 6 features, 3 testimonials, 9 logos.
Why: the generator invents or trims content to complete rows. A real feature set or customer list comes out to whatever number it comes out to.
Fix: keep the true count and design for the remainder, with a featured first item or an asymmetric last row.

**33. Filler cards completing the grid** (mild)
Tell: the last cell reads "And much more...", "Your feature here", or repeats another card, and exists to close the row.
Why: the model wrote that cell to fill the layout.
Fix: delete the filler and reflow the grid to the honest count.

## Containers, spacing & alignment

**34. One max-width container for the entire page** (strong)
Tell: every section sits in the same centered `max-w-7xl` box, with no full-bleed moments, no breakouts, and identical gutters top to bottom.
Why: the generator copies one wrapper into every section, while designers set the measure by content type.
Fix: vary container widths, at about 65ch for prose, wider for tables, full-bleed for key visuals. Let one element per page break its container.

**35. Identical vertical padding on every section** (strong)
Tell: metronomic `py-20`/`py-24` rhythm, so the page scrolls as a stack of slabs at one fixed interval.
Why: monotonous spacing is a named slop pattern. Designers compress related sections and open space around key moments.
Fix: tighten the gaps between sections that belong together, and expand space around the one or two moments that deserve emphasis.

**36. Uniform grid gutters everywhere** (mild)
Tell: the same `gap-8` between logos, feature cards, pricing tiers, and footer columns whatever the content density.
Why: applying one spacing token across the page averages the design away.
Fix: tighten gutters for dense small items such as logos and tags, and widen them for large cards, so the grouping reads as a choice.

**37. Empty-at-scale desktop layout** (strong)
Tell: at 1440px and up the layout thins out to small content islands floating in wide empty voids.
Why: responsive-by-default templates grow their margins instead of their layouts at large viewports, and the whitespace stands in for a design decision.
Fix: build real wide-viewport variants by adding a column or setting two sections side by side.

**38. Perfect mirror symmetry throughout** (strong)
Tell: every section balances around the vertical center axis, with nothing offset, off-grid, or anchored to an edge.
Why: symmetry is the zero-risk average, and a page with no asymmetry anywhere reads as machine output.
Fix: introduce asymmetry in two or three places. Offset a section heading, run a 2/3–1/3 split, or anchor one visual to the viewport edge.

**39. Center-aligned everything, including body text** (instant)
Tell: every heading, multi-line paragraph, button group, and list down the page carries `text-center`.
Why: the generator inherits the centered hero and spreads centering across the page, and centered multi-line body copy is a classic non-designer tell.
Fix: left-align body text and most section content. Save centering for short standalone statements such as a hero headline or a CTA band.

**40. Hermetically sealed section slabs** (strong)
Tell: sections stack as strict horizontal bands like plates, with no element crossing a boundary and no layering or z-depth.
Why: generated markup is a linear list of `<section>` blocks, while crafted sites let a visual straddle two sections.
Fix: pull one visual across a section boundary with a negative margin. One overlap breaks the slab rhythm.

**41. Alternating white/gray section stripes** (strong)
Tell: sections separated by alternating `bg-white` and `bg-gray-50`, with the stripe flip doing all the sectioning work.
Why: templates fake structure with a zebra stripe when the layout itself never varies.
Fix: separate sections through spacing and layout change. Shift the background for a true context change such as pricing, and leave the other blocks alone.

**42. Uniform section heights and scroll cadence** (mild)
Tell: most sections occupy about the same viewport height, so scrolling feels like flipping identical slides.
Why: the generator built each section on its own to the same template depth.
Fix: vary the density. Drop one short band of a single sentence between two deep sections, and let one section run long.

## Navigation

**43. Navbar formula: logo left / links center / CTA right** (instant)
Tell: full-width 64px navbar with the logo left, 4–5 links dead center, and "Sign in" plus a filled "Get Started" right, identical across v0, Lovable, and Bolt outputs.
Why: this is the highest-probability nav in training data, and all three tools produce it from the same prompt.
Fix: keep the usability and break the template. Group links beside the logo, point them at real destinations (Docs, Changelog), and vary the CTA treatment. Restructure navigation and never remove it.

**44. Floating detached pill navbar** (strong)
Tell: rounded-full navbar floating below the top edge with a visible margin, drop-shadowed, hovering over the content.
Why: this signature v0-era component spread through generated sites in 2024–25.
Fix: dock the nav to the top or square it off. Keep the pill when rounded geometry is a brand motif you use elsewhere.

**45. Anchor-only navigation IA** (strong)
Tell: every nav link (Features, Pricing, FAQ) is a `#fragment` scrolling the same page, and no second route exists.
Why: the generator produces one page, so the nav can point inward and nowhere else. It leaves a structural fingerprint of one-shot generation.
Fix: build the two or three real pages the business needs (about, contact/docs, legal) and link them. Keep anchors for secondary in-page nav.

**46. Nav mirrors the section list one-to-one** (mild)
Tell: nav labels match the homepage sections in scroll order, giving readers a table of contents in the place of an information architecture.
Why: the generator built the nav from the same section list it used for the page body.
Fix: organize the nav around user tasks (Product, Docs, Pricing, Company) rather than scroll positions.

**47. Every CTA on the page targets the same URL** (mild)
Tell: nav button, hero pair, band CTA, and all three pricing buttons point at the same /signup under the same label.
Why: one CTA value propagated through the template, while real funnels separate intent.
Fix: differentiate destinations and labels by context, with a trial in the hero, a demo or docs mid-page, and contact-sales on the enterprise tier.

## Footer

**48. Mega-footer formula on a tiny site** (instant)
Tell: logo, tagline, and social icons in one column beside 3–4 link columns headed Product / Company / Resources / Legal, closing with a © bar, under a one-page site.
Why: the generator ships the enterprise footer scaffold whole, and its scale does not match the site above it.
Fix: right-size the footer to what exists, as a single row of links that resolve, and grow it as you add pages.

**49. Dead footer links** (strong)
Tell: footer links carrying `href="#"` or pointing at /careers, /blog, and /press pages nobody created.
Why: those links came with the template, and nobody proofread the output.
Fix: remove links to pages that do not exist, and write the pages the law requires (privacy, terms) with real content.

**50. Footer/site disproportion** (strong)
Tell: 30–40 footer links, a language selector, and app-store badges beneath a single-feature waitlist page.
Why: footer complexity signals company scale, and readers notice when the size claim outruns the site.
Fix: prune the footer down to the links you have and the pages that resolve.

**51. Unwired newsletter block** (mild)
Tell: "Subscribe to our newsletter" input and button in the footer that post nowhere and have no provider behind them.
Why: the newsletter slot arrives with the footer template whether or not a newsletter exists.
Fix: connect it to a real list on a real cadence, or remove the block.

## Information architecture & pages

**52. Single-landing-page-only information architecture** (strong)
Tell: the whole "company" is one route, with no about, contact, blog, docs, changelog, or GitHub link anywhere.
Why: an about page with names, dated posts, and a changelog carries the structural evidence of a real project, and this site has none of it.
Fix: add a small genuine about page (names, faces, why), a contact page with real channels, and legal pages that say something.

**53. Thin centered about page** (strong)
Tell: /about is one centered mission paragraph in a narrow column, with no names, photos, dates, or location.
Why: the model can write mission-speak and cannot supply a biography, and the structural emptiness shows in seconds.
Fix: add concrete facts, meaning founder names and photos, the founding date, the city, and how the thing started.

**54. Contact page that is only a form** (strong)
Tell: /contact holds a name/email/message form and nothing else, with no email address, phone, physical address, or response-time expectation.
Why: the contact form is a component, while contact *information* is a business reality the generator does not have.
Fix: publish a monitored email address beside the form, along with any other real channel and the response time you expect to hit.

**55. Placeholder blog section** (strong)
Tell: "From our blog" grid or /blog holding three template cards with generic covers, "Blog post title here", or undated filler posts.
Why: a blog scaffold with no dated content behind it counts as evidence against the site.
Fix: remove the blog until two or three real dated posts exist. Never ship placeholder cards.

**56. Zero temporal texture** (mild)
Tell: every page is consistent to the pixel and same-day new, with no dates, no changelog, no old URLs, and no odd legacy page that nobody updated.
Why: real sites accrete inconsistency over the years, and a site generated in one pass has no history to show.
Fix: add a dated changelog or release notes, and put a date on everything you publish.

**57. Structure outrunning content** (strong)
Tell: a full 10-section landing architecture (logos, stats, testimonials, FAQ, blog) wraps a product with one feature and no users, and the sections stand as labeled shells holding almost no information.
Why: the more the template promises, the more the missing content shows: "they all looked the same and none had the information you were looking for."
Fix: cut the page down to the sections with real substance behind them, and let it be short.

## Mobile

**58. Source-order single-column mobile collapse** (strong)
Tell: on mobile every grid stacks in DOM order, so zig-zag rows become image/text/image/text monotony and the logo bar becomes a logo tower, with nothing reprioritized.
Why: `grid-cols-1 md:grid-cols-3` is responsive by default, and nobody designed for the small screen.
Fix: adjust per breakpoint. Keep text before image throughout, collapse the logo strip to one row, turn steps into a vertical timeline, and hide decorative duplicates.

**59. Desktop spacing preserved on mobile** (mild)
Tell: `py-24` section gaps and giant hero margins survive at 375px, so the mobile page scrolls through long empty stretches between content islands.
Why: nobody revisited the uniform spacing scale per breakpoint.
Fix: halve the section padding at small breakpoints and tighten the gaps inside sections, so the density matches the device.

**60. Full-screen hamburger overlay for five links** (mild)
Tell: the mobile hamburger opens a 100vh overlay with five giant centered anchor links, on a one-page site.
Why: the template ships this overlay as its mobile nav whatever the nav size.
Fix: use a compact dropdown sized to the link count, or surface the one or two links that matter beside the logo.

**61. Mobile hero pushing every CTA below the fold** (mild)
Tell: stacked badge, headline, subhead, two full-width buttons, and a screenshot leave the first mobile screen holding a fragment of the headline.
Why: the desktop centered stack collapsed without anyone re-editing it for the small viewport.
Fix: on mobile, drop the badge, shorten the subhead, keep one CTA, and let the screenshot follow, so an action lands above the fold.

## App shells

**62. Dashboard KPI-shell template (vibe-coded apps)** (strong)
Tell: the app opens on the universal admin shell, with a sidebar left, four equal stat cards across the top, a line-chart card, and a table card below.
Why: every generator produces this dashboard scaffold before it knows what the app does.
Fix: design the opening screen around the user's first task, size the cards by importance, and delete KPI cards with no data behind them.

**63. Lone waitlist card page** (mild)
Tell: the pre-launch site is a single centered card holding a headline, one sentence, an email input, and "Join the waitlist", floating in a decorated void.
Why: this is the canonical one-prompt output for "make me a waitlist page."
Fix: keep the form and add substance around it, covering what the product does, who it serves, and one real visual or founder note.

## VOCAB: greppable/measurable signals for this file

- Class patterns: `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8` · `container mx-auto` · repeated `py-16|py-20|py-24|py-32` on every section · `min-h-screen flex flex-col items-center justify-center` · page-wide `text-center` · `grid grid-cols-1 md:grid-cols-3 gap-8` · `grid-cols-2 lg:grid-cols-4` · `inline-flex items-center rounded-full border px-3 py-1 text-sm` (pill badge) · `-space-x-2|-space-x-3` (avatar cluster) · `bg-gray-50`/`bg-muted` stripes · `h-16` + `flex items-center justify-between` (navbar) · `animate-marquee` · `aspect-video rounded-xl shadow-2xl` (hero shot) · `sticky top-0 z-50`
- Anchors as the whole nav: `#features` `#how-it-works` `#testimonials` `#pricing` `#faq` `#contact`
- Component names: Hero, Navbar, LogoCloud/TrustedBy, Features, HowItWorks, Stats, Testimonials, Pricing, FAQ, CTA/CallToAction, Footer, BentoGrid, SocialProof, Waitlist
- Section strings: "Trusted by" · "Loved by" · "How it works" · "Why choose us" · "What our customers say" · "Simple, transparent pricing" · "Frequently asked questions" · "Ready to get started?" · "Most Popular" · "Join the waitlist" · "10,000+" "99.9%" "4.9/5" "24/7"
- Placeholder tells: "Acme Corp" "TechCorp" "Globex" "Initech" · `href="#"` · footer columns exactly Product/Company/Resources/Legal · "[Your Company]" · "Blog post title here"
- Ratios to measure: identical section padding across all sections · all grids exactly 3 columns · item counts ≡ 0 mod columns · one max-width for 100% of sections · 0 elements crossing section boundaries · 100% centered headings · nav = 4–5 links + 1 filled CTA · 1 route in the sitemap

Sources: developersdigest.tech "AI design slop and how to spot it" · impeccable.style/slop · sikora.software "AI website design" · slopdar.com detection guide · shuffle.dev "Why do most AI-generated websites look the same" · axe-web.com "AI website design sameness" · uibakery.io "Lovable vs Bolt vs v0" · shadcn.io block library · freedesignmd.com lexicon · writerdock.in UI trends 2026 · nataliewritesthings.substack.com "No one wants to Get Started" · HN threads 43502363/49024805
