# Catalog 6/7: Copy & content (#184–251, #287)

Headlines, AI sentence constructions, word blacklist, CTAs, section copy, trust signals, testimonials, FAQ, about pages, blog, content hygiene. Severity: **instant** / **strong** / **mild** (see SKILL.md).

Two master tests for this file. **The swap test**: if a sentence still works with a competitor's logo on the page, it's slop. **The read-aloud test**: would the founder say this sentence to a customer?

## Headlines & value proposition

**184. "Verb your Noun" headline formula** (instant)
Tell: hero H1 = imperative marketing verb + "your" + abstract noun: "Supercharge Your Workflow", "Elevate Your Business", "Transform Your Productivity."
Why: the model averages thousands of SaaS heroes into one template. Its verb comes from the AI verb set, and its noun names no product or outcome.
Fix: name the mechanism and the object in plain words: "Turn your Stripe exports into investor-ready reports" (cf. Stripe's "Financial infrastructure for the internet").

**185. "The future of X" headline** (instant)
Tell: "The Future of Work Is Here", "The future of team collaboration."
Why: a category claim that carries no information. The model reaches for it when it doesn't know what the product does.
Fix: say what it does today and for whom: "Payroll for restaurants that run on tips."

**186. "X, reimagined" appositive headline** (instant)
Tell: single noun + comma + past participle: "Invoicing, reimagined.", "Meetings, simplified.", "Email, reinvented."
Why: the model borrows Apple's cadence and promises novelty without naming any.
Fix: state the reimagining itself: "Invoices that chase themselves: auto-reminders until you're paid."

**187. Twin staccato imperative hero** (instant)
Tell: two 2–3 word parallel imperatives with periods: "Build faster. Ship smarter.", "Work less. Achieve more."
Why: ask a model for "punchy" and it picks rhythm over meaning. The result fits any product in the category.
Fix: make one concrete claim with a real object: "Deploy a Postgres branch in 300ms."

**188. "All-in-one platform" positioning** (instant)
Tell: "The all-in-one platform for modern teams", "One platform. Endless possibilities."
Why: the most common value prop a model writes. It claims every job and proves none of them.
Fix: pick the one job you do best and lead with it; name the tools you replace: "Replaces Trello + Slack threads + weekly status emails."

**189. Category-free abstraction headline** (instant)
Tell: the hero never says what the product IS: "Scale without limits", "Build the future", "Unlock your potential."
Why: the model averages headlines into vapor. A visitor who has read the first screen still can't say what this is.
Fix: apply the one-sentence-value-prop test. A stranger reading only H1 and subhead should be able to say what it is, who it's for, and why it differs. Add the category noun ("An uptime monitor that...").

**190. Echo subheadline** (instant)
Tell: the subhead restates the H1 in buzzword long-form: "Our platform helps teams of all sizes streamline their workflow, boost productivity, and achieve more."
Why: the model treats the subhead as a place to elaborate, so it restates the H1 with three buzzwords.
Fix: give the subhead the mechanism or proof the H1 couldn't fit: "Connects to your GitHub, flags the 5% of PRs that cause 80% of incidents."

**191. "Whether you're X or Y" audience hedge** (strong)
Tell: "Whether you're a solo founder or a Fortune 500 team, Acme scales with you."
Why: a documented inclusiveness template. The model dodges the choice of customer, and no reader feels addressed.
Fix: pick the primary user and name them: "Built for agencies juggling 20+ client accounts". Secondary audiences self-select.

**192. "AI-powered" as the entire value prop** (strong)
Tell: "AI-powered insights for modern teams", "Harness the power of AI". AI is the subject and the benefit goes unstated.
Why: "AI-powered" describes the implementation and leaves the value to the reader. It now reads as template output.
Fix: say what the AI does: "Drafts your reply in your past tone; you edit and send."

## AI sentence constructions

**193. "It's not just X — it's Y" negation pivot** (instant)
Tell: "It's not just a CRM — it's your revenue engine.", "This isn't software. It's a movement."
Why: the most-cited AI construction. Wikipedia ranks negative parallelism as the most prominent tell, and three or more per page crosses the slop threshold. The contrast manufactures depth the sentence doesn't have.
Fix: cut the negation and keep a specific second half: "A CRM that writes the follow-up email for you". Budget one deliberate contrast per page.

**194. "Say goodbye to X / say hello to Y"** (strong)
Tell: "Say goodbye to spreadsheets. Say hello to clarity." (also "Stop guessing. Start growing.")
Why: a paired-imperative contrast, another face of the not-X-but-Y tic. The model leans on it for drama.
Fix: keep the pain and drop the greeting-card frame: "Your budget lives in 11 spreadsheets. Put it in one place that updates itself."

**195. "No X. No Y. Just Z."** (strong)
Tell: "No code. No hassle. Just results.", "No fluff. No filler. Just answers."
Why: a documented staccato triplet. It scans as rhythm and carries one claim at most.
Fix: keep the strongest negation and make it verifiable: "No credit card, no sales call. The free tier is the real product."

**196. Rule-of-three everywhere** (strong)
Tell: every heading, list, and sentence resolves in triads ("Fast, reliable, and secure", "Plan, execute, and optimize"), plus three cards, three steps, three tiers.
Why: models resolve toward the tricolon. More than one polished triplet per 200 words is a measured threshold. (Layout version: #25.)
Fix: break the count on purpose with two blunt items or four uneven ones; cut the weakest member of every triad.

**197. Trailing "-ing" significance clause** (strong)
Tell: sentences end with a participial value-claim: "...integrates with Slack, ensuring seamless collaboration across your organization."
Why: a habit Wikipedia documents. The model bolts hollow analysis onto a fact with a present participle.
Fix: end at the fact, or give the consequence its own sentence: "Messages sync to Slack in under a second."

**198. "In today's fast-paced world" opener** (strong)
Tell: section or blog opens "In today's fast-paced digital world...", "In the age of AI...", "In an era where..."
Why: a throat-clearing orientation the model emits by default. Editors cut it.
Fix: delete the sentence and start with the claim or the problem: "Your team wastes 6 hours a week in status meetings."

**199. Em-dash density** (mild)
Tell: multiple em dashes per paragraph: "Acme is fast — really fast — and secure."
Why: models write em dashes at about twice the human rate, and readers now flag them. Density is what matters (>2 per 100 words).
Fix: keep em dashes you'd defend; convert the rest to commas, parentheses, or two sentences.

**200. "Not only... but also..."** (mild)
Tell: "Not only does Acme save time, but it also reduces errors."
Why: padding that appears on every AI-tell list. It doubles the length and leaves the meaning where it was.
Fix: use two plain sentences, or one with "and": "Acme saves time and catches errors before they ship."

**201. "From X to Y" fake-range construction** (mild)
Tell: "From startups to enterprises, from marketing to engineering, Acme has you covered."
Why: a documented range template. It simulates coverage and offers no evidence.
Fix: name 2–3 real customers across the range instead of the abstract span.

**202. Hedging modals in sales copy** (mild)
Tell: "can help you improve...", "may reduce costs", "designed to potentially streamline."
Why: the model hedges to stay safe. Marketing that won't commit reads as generated.
Fix: commit where you have evidence and scope where you don't: "Cuts render times 35–60% on codebases over 100k lines."

**203. Metronomic sentence rhythm** (mild)
Tell: every sentence 15–20 words, same subject-verb-object shape, paragraph after paragraph.
Why: low variance in sentence length is one of the few AI fingerprints you can measure.
Fix: follow a long compound sentence with a three-word punch; read the page aloud and mark where you'd breathe.

## The word blacklist (grep the rendered text)

**204. Marketing-verb density** (strong)
Tell: unlock, unleash, elevate, empower, supercharge, streamline, harness, revolutionize, transform clustered across headings.
Why: the documented AI marketing verb set. More than one per screen reads as generated.
Fix: swap in the literal action: "Supercharge your productivity" → "Cut invoice prep from 2 hours to 10 minutes."

**205. "Seamless/seamlessly"** (strong)
Tell: "seamless integration", "seamlessly connects with your tools."
Why: the flagship AI adjective, top of every 2024–2026 blacklist, and a quality claim nobody can falsify.
Fix: replace it with the evidence: "Two-way Salesforce sync every 60 seconds, no field mapping."

**206. "Effortless/effortlessly"** (strong)
Tell: "Effortlessly manage your projects", "Effortless expense tracking."
Why: a stock AI adverb. It promises the absence of work and names none of the work removed.
Fix: name the effort you removed: "No spreadsheets: receipts photograph themselves into categories."

**207. Speed hyperbole compounds** (strong)
Tell: "blazing-fast", "lightning-fast performance", "insanely fast."
Why: the dev-tool signature. Hyphenated speed compounds arrive with no benchmark behind them.
Fix: state the measurement and link it: "Cold start under 50ms (benchmarks below)."

**208. Edge-adjective cluster** (strong)
Tell: "cutting-edge", "next-level", "game-changing", "state-of-the-art", "best-in-class", "world-class", "industry-leading."
Why: safe superlatives that award the product a rank nobody else assigned.
Fix: replace the rank claim with a differentiator only you can make: "The only editor with local-first sync (works on planes)."

**209. "In seconds" / "in minutes, not months"** (strong)
Tell: "Create stunning reports in seconds", "Launch in minutes, not months."
Why: the default time-compression template. Few of these claims survive a stopwatch, and the time contrast is a known tic.
Fix: give the honest median time: "Most teams ship their first workflow in 25 minutes."

**210. "10x your X"** (strong)
Tell: "10x your productivity", "10x your content output."
Why: a growth-hack multiplier with no baseline and no source, and a core AI hype token.
Fix: cite a measured delta with a denominator: "Writers on Acme publish 3.1× more posts/month (n=1,240, 2025 cohort)". Otherwise drop the number.

**211. ChatGPT lexicon in site prose** (strong)
Tell: delve, tapestry, realm, landscape ("the ever-evolving landscape of e-commerce"), testament, pivotal, robust, multifaceted, holistic in About/blog/feature copy.
Why: the researched LLM focal-word set. These words spiked about 25× after ChatGPT shipped, and more than three per 500 words is a reproducible threshold.
Fix: grep for the blacklist below and rewrite each hit as something a founder would say aloud.

**212. Self-praise UI adjectives** (strong)
Tell: "intuitive interface", "powerful features", "beautiful dashboards", "simple yet powerful."
Why: the product grades its own homework in the adjective set models default to, naming feelings the visitor hasn't had yet.
Fix: show it, then let a customer say it: screenshot plus "Set up our 40-person rollout without reading a doc" (Dana R., IT lead, linked).

**213. "Actionable insights" / "data-driven decisions"** (strong)
Tell: feature blurbs ending "...so you can make data-driven decisions with actionable insights."
Why: the two most recycled B2B noun phrases in AI output. Neither one names an insight.
Fix: name one insight the product surfaces: "See which onboarding step loses 30% of signups."

**214. "Everything you need" absolutes** (strong)
Tell: "Everything you need to grow your business", "The only tool you'll ever need."
Why: the model compresses a value prop into a total claim, and the visitor's five-second scan falsifies it.
Fix: scope the claim to something you can defend: "Everything a 2-sided marketplace needs for payments: escrow, splits, refunds, 1099s."

**215. "Focus on what matters" cliché** (strong)
Tell: "...so you can focus on what matters most", "spend less time on busywork and more time doing what you love."
Why: the benefit of last resort. The model reaches for it when it can't name the real one.
Fix: say what they'll do with the saved time, in their vocabulary: "Close books by the 3rd instead of the 15th."

## CTAs & microcopy

**216. Generic CTA labels** (instant)
Tell: "Get Started" and "Learn More" label every button site-wide, whatever the click does. (The hero button-pair layout: #3.)
Why: the dominant CTA labels in training data. A generic label tells the visitor that nobody thought about the next step.
Fix: label the literal action and its payoff: "Create your first form (free)", "See a 2-min demo", "Get a quote". Give two adjacent buttons two different verbs.

**217. "Start your free trial today" filler CTA** (strong)
Tell: "Start your free trial today!", "Sign up now and transform your workflow."
Why: the model appends "today" and "now" as urgency filler. The copy sells the signup and skips what the click delivers.
Fix: sell the first session: "Import your data, see your dashboard in 3 minutes". Keep the free-trial fact as microcopy ("Free for 14 days").

**218. Exclamation saturation** (strong)
Tell: several exclamation points per screen: "Get started today!", "It's that easy!", "And the best part? It's free!"
Why: the model props up an empty claim with punctuation. Uniform excitement flattens the emphasis you needed elsewhere.
Fix: budget one exclamation point per page at most, and let the specifics carry the energy.

**219. Emoji in headings and body copy** (instant)
Tell: "🚀 Launch Faster", "✨ Smart Features", "🎉 You're all set!", emoji-bulleted feature lists.
Why: ChatGPT decorates marketing copy with the same small emoji set (🚀✨💡🎯🎉). Heading density is now a primary slop marker. (Emoji as icons: #144.)
Fix: strip emoji from headings; if the brand voice is playful, prove it with wit in the words.

**220. "Made with ❤️" signature** (mild)
Tell: "Made with ❤️ by the Acme team", "Crafted with love and coffee ☕."
Why: a template-era affectation the model reproduces. It signals warmth instead of showing any.
Fix: be human on the page: "Built by two ex-Shopify engineers in Ottawa. Email us: real@address."

**221. Default empty-state/error/404 microcopy** (mild)
Tell: "Oops! Something went wrong.", "No items found.", "Error 404: Page not found", "🎉 Success!" toasts.
Why: generator defaults survive in the places where voice costs least to show, and unowned microcopy reads as an unowned product. (Missing 404 route: #263.)
Fix: write these in brand voice with a next step. 404: "That page moved or never existed. The three most-visited pages are..." Empty state: "No invoices yet. Import from Stripe or create one (30 sec)."

## Section copy

**222. Feature-card copy formula** (strong)
Tell: 3 or 6 cards, each with an icon, a 2–3 word Title Case label, and a two-line any-product blurb: "Real-Time Analytics / Get deep insights into your data with powerful, customizable dashboards." (Card layout: #26.)
Why: the canonical AI feature grid. Each blurb is an averaged description that fits every competitor.
Fix: one card carries one capability and its proof: "Anomaly alerts / Pings Slack when checkout conversion drops 2σ below the 28-day mean". Kill the cards you can't make specific.

**223. Bolded-lead bullet formula** (strong)
Tell: lists of "**Fast:** Get results in record time. **Secure:** Your data is always protected. **Scalable:** Grows with your business."
Why: someone pasted ChatGPT's bold-header-colon-explanation output into the page.
Fix: give every bullet a number, a name, or a noun that only your product has; unbold the decoration.

**224. Generic section headings** (strong)
Tell: "Features", "Benefits", "Why Choose Us?", "What We Offer", "What Our Customers Say", "Get In Touch."
Why: scaffolding labels nobody replaced. The model names a section by its function; a writer names it by its message.
Fix: make each heading an assertion: "Why Choose Us?" → "Why teams switch from Jira"; "Features" → "What you can ship with it."

**225. Generic 1-2-3 "How it works" copy** (strong)
Tell: "1. Sign Up — Create your account in seconds. 2. Connect — Link your tools. 3. Grow — Watch your business thrive." (Step layout: #15.)
Why: the default three-step onboarding narrative. Step 3 names an outcome the visitor has to imagine.
Fix: describe the real first session with real nouns: "1. Paste your Stripe key. 2. Pick the 3 metrics you report to investors. 3. Get the Notion-ready digest every Monday 8am."

**226. Swap-logo interchangeability** (strong)
Tell: body copy passes the swap test. Put a competitor's logo on the page and every sentence still works ("With Acme, you can streamline collaboration and boost productivity").
Why: the model averages the category's marketing, so nothing in the copy ties back to what this product does.
Fix: put product-specific nouns in every section: feature names, supported file types, limits, latencies, customer names. If a sentence could run on a rival's site, rewrite it or cut it.

**227. Uniform enthusiasm, zero tradeoffs** (strong)
Tell: every sentence sells. No opinions, no "this isn't for you if...", no known limitations.
Why: flat, unbroken positivity is a documented AI signature. A person with a real product has priorities and gripes.
Fix: add one honest constraint: "Not built for teams over 200. We optimize for speed at small scale". Disqualifying copy raises trust and the quality of the conversions you get.

## Trust & proof claims

**228. Round-number herd claims** (instant)
Tell: "Trusted by 10,000+ teams worldwide", "Join thousands of happy customers", with no logos or links behind them. (Hero avatar-cluster version: #5; stat banner: #16.)
Why: the most parodied element on an AI-built site. The model adds the herd claim by default, even for a product with no users.
Fix: give checkable proof at whatever scale is true: "412 workspaces created this month", "Used by 214 YC companies" (linked). Odd precise numbers outperform round ones. Remove the claim until it's true.

**229. Implausible famous-logo bar** (instant)
Tell: Google, Microsoft, Netflix, Airbnb logos under "Trusted by industry leaders" on a product launched last week. (Fake made-up company logos: #14.)
Why: the model scaffolds a logo wall as standard page anatomy and fills it with famous brands. One email to any named "customer" ends it.
Fix: show only logos you have permission and a story for. With none, show design partners, an accelerator badge, or open metrics ("2,400 GitHub stars").

**230. "As seen on / Featured in" with no coverage** (strong)
Tell: press bar citing TechCrunch/Forbes/Product Hunt with no linked article (or the "coverage" is a paid directory).
Why: a borrowed-authority template the model includes by default. One search catches it, and the doubt spreads across the page.
Fix: link every outlet to the piece. Until real press exists, quote a named user.

**231. Unsourced star rating** (strong)
Tell: "4.9/5 stars" or five gold stars with no platform, no review count, no link.
Why: a rating summarizes reviews. With no reviews named, the stars are decoration the model added to look credible.
Fix: "4.7 on G2 (312 reviews)" linked to the G2 profile; if you have 6 reviews, quote the best one rather than averaging.

**232. Suspiciously precise unsourced percentages** (strong)
Tell: "Boost productivity by 47%", "Reduce churn by 32%" with no study, cohort, or link.
Why: models hallucinate numbers that feel authoritative. Precision without provenance is the tell.
Fix: attach the source, or soften the claim: "Pilot teams (n=14) reported saving ~4 h/week (survey, Jan 2026)."

**233. Stage-contradicting claims** (strong)
Tell: "Join 50,000+ users" on a waitlist page; a "Beta" badge next to "Trusted by thousands"; "No credit card required" on a product with no billing at all. (Pre-launch social proof: #17.)
Why: the model writes each section on its own against an imagined company, so the claims contradict what the visitor can see.
Fix: audit every claim against reality. Early-stage honesty converts: "We launched 3 weeks ago. 214 people are already using it daily."

**234. Security theater phrases** (strong)
Tell: "Bank-level security", "Enterprise-grade encryption", "SOC 2 compliant" with no security page, DPA, or certificate anywhere.
Why: the model adds compliance vocabulary as decoration. The buyer who cares looks for the artifact and finds nothing.
Fix: claim what's true and link it: "AES-256 at rest, TLS 1.3 in transit; SOC 2 Type II in progress (Q4). Security page →."

## Testimonials

**235. Central-casting testimonial names** (strong)
Tell: "Sarah Chen, Product Manager", "Sarah Johnson, Marketing Lead at TechFlow", "Michael Rodriguez, CEO of DataSync": names balanced across demographics, generic titles, ungoogleable companies. (Fake avatar photos: #143; card-wall layout: #18.)
Why: models default to these names, so the same roster recurs across AI-built sites. Readers pattern-match it now.
Fix: use real people with verifiable anchors: full name, linked company, LinkedIn or X handle, written permission. Two real quotes beat six synthetic ones.

**236. Generic-praise testimonial quotes** (strong)
Tell: "This changed everything for our team!", "An absolute game-changer. Highly recommend!", "10/10 — best tool we've ever used."
Why: the model writes praise that points at nothing: no feature, no before and after. Every quote reduces to a five-star adjective.
Fix: every quote should carry a specific: "We switched from Asana and cut our Monday planning from 90 to 25 minutes". Interview customers and transcribe what they say.

**237. Testimonial set uniformity** (mild)
Tell: all quotes are 2 sentences, same enthusiasm, same cadence, no dates, none mention problems or caveats.
Why: one generation produced the whole set. A real review set varies, and some of it runs lukewarm.
Fix: vary length and temperature; include one caveat quote ("Setup took an afternoon, but..."). A mild negative makes the positives land.

## FAQ

**238. FAQ questions nobody asked** (strong)
Tell: "What makes Acme different?", "Why should I choose Acme?", "Is Acme right for my business?": marketing pitches wearing question marks. (Accordion layout: #21.)
Why: the model writes FAQs from the seller's side. Real users ask about price, limits, migration, cancellation, and data.
Fix: pull questions from support tickets and sales calls, and answer the awkward ones: "Can I export everything if I leave?" → "Yes, one-click JSON/CSV, no lock-in."

**239. "Yes! Absolutely." FAQ answers** (mild)
Tell: every answer opens "Yes! Absolutely..." then restates the question with buzzwords and no facts.
Why: the model's answer shape is affirmation, restatement, reassurance, with no information in it.
Fix: answer like a support engineer. First sentence is the fact ("Yes, export is on every plan, including free"), second is the caveat or the link.

## About & company

**240. Mission-statement vapor** (strong)
Tell: "We believe in empowering businesses to unlock their full potential through innovative solutions", "Our mission is to democratize X."
Why: corporate-speak the model can produce for any company. It names no market and stakes no belief anyone could argue with.
Fix: state an arguable conviction: "We think expense reports shouldn't exist, so we're deleting them one receipt-scan at a time."

**241. Origin-story boilerplate** (strong)
Tell: "Founded with a vision to revolutionize the industry...", "What started as a simple idea has grown into a passion for excellence", with no names, dates, or events. (Thin about-page structure: #53.)
Why: with no facts to work from, the model builds a founding myth out of stock phrases.
Fix: give specifics: founders' names, the year, the incident that started it ("We built this after losing a $40k invoice in an email thread in 2023"), photos of the people.

**242. Phantom "team of experts"** (strong)
Tell: "Our team of experts is dedicated to your success", "world-class team of engineers", with no names, faces, or LinkedIn links anywhere on the site.
Why: the model asserts an institutional depth the site can't evidence.
Fix: name real people with real roles and links. A solo founder saying "It's just me, here's my GitHub" outperforms a fictional team.

## Blog & long-form

**243. AI blog scaffold** (strong)
Tell: posts opening "In this article, we'll explore...", an H2 every ~80 words, "Let's dive in", bold-header bullet stacks, closing "In conclusion" + "Remember, ..."
Why: the documented ChatGPT article skeleton, start to finish. Readers discount it and so does Google.
Fix: one thesis per post, first-person experience, one real example with numbers. Delete the intro and outro paragraphs and start at the point. (For deep prose de-sloping, the Anthropic `stop-slop` skill applies.)

**244. Fabricated blog citations** (strong)
Tell: "Studies show that 73% of marketers...", "According to industry reports..." with no link, or links to nonexistent studies; vague attribution ("Experts agree").
Why: hallucinated authority is a signature LLM failure, and vague attribution is weasel-wording that editors flag.
Fix: link every stat to a named primary source and year, or cut it.

**245. Ghost bylines and same-day archives** (strong)
Tell: every post "By Admin" or authorless, 12 posts all dated the launch week, identical 5-min read times.
Why: someone generated the content calendar in one batch, and the metadata says so. (Site-wide missing history: #56.)
Fix: give every post a real author with a bio and a photo, publish on a human cadence, and delete the filler. Three real articles beat twenty generated ones.

## Content hygiene

**246. Raw LLM artifacts in copy** (instant)
Tell: "Certainly! Here's a compelling headline for your landing page:", "As an AI language model...", "I hope this helps!" shipped verbatim.
Why: someone pasted a chat transcript into production without reading it.
Fix: grep the built site for "Certainly", "Here's a", "As an AI", "I hope this helps", "Feel free to customize."

**247. Markdown bleed-through** (instant)
Tell: literal `**bold**` asterisks, `# headings`, or `[link text](url)` rendered as text on the live site.
Why: the render pipeline passes the model's output format straight through.
Fix: grep rendered HTML text nodes for `**`, `](`, and backticks, then fix the copy pipeline that let them through.

**248. Placeholder leftovers** (instant)
Tell: "Lorem ipsum...", "Your Company", john@example.com, (555) 123-4567, "123 Main Street", "[Insert testimonial here]", "Feature one description goes here."
Why: the generator emitted scaffold text and nobody replaced it.
Fix: pre-launch grep (and add it as a CI check): lorem, ipsum, example.com, "your company", "coming soon", TODO, [insert, {{, placeholder, "123 Main", "555".

**249. Product name drift** (strong)
Tell: hero calls it "TaskFlow", pricing calls it "Taskflow Pro", FAQ says "our platform", legal says a third name.
Why: separate prompts wrote each section against different context, and nobody read the page end to end.
Fix: single-source the product name, read the whole page aloud before launch, and grep for old working titles.

**250. Stale or mismatched copyright line** (strong)
Tell: "© 2024 YourCompany. All rights reserved." in a later year, or a footer naming a different product than the header.
Why: a template date nobody proofread. It tells the visitor that nobody lives here.
Fix: dynamic year, correct legal entity name; read your own footer once.

**251. Template-tainted legal pages** (strong)
Tell: Privacy Policy/Terms containing "[Company Name]", the wrong company, boilerplate describing data the site never collects, no contact address.
Why: the publisher never read the generated legal text. That carries legal exposure on top of the aesthetic problem.
Fix: use a reputable policy service or counsel, with the real entity, jurisdiction, and data practices. Grep legal pages for brackets and other product names.

**287. Invisible characters from the copy pipeline** (mild)
Tell: zero-width spaces (`U+200B`, `U+200C`, `U+200D`), a byte-order mark (`U+FEFF`), or a non-breaking space sitting where a plain space belongs, left in the rendered text.
Why: model output and chat-window copy-paste carry these through. They are invisible on screen, so nobody proofreads them out, and they break search, text selection and screen readers.
Fix: strip them in the content pipeline. A grep for the zero-width range over the built output catches them, and it belongs in the pre-deploy check next to the placeholder grep.

## VOCAB: the blacklist (grep rendered text; rewrite each hit rather than deleting it)

- **Verbs:** unlock, unleash, elevate, empower, supercharge, streamline, revolutionize, transform your, harness, leverage, delve, dive into, embark, unveil, uncover, foster, ignite, utilize, facilitate, showcase, navigate the, boost your, curate, democratize, delight your, level up
- **Adjectives/adverbs:** seamless(ly), effortless(ly), frictionless, hassle-free, blazing(-)fast, lightning(-)fast, game-changing, game-changer, cutting-edge, next-level, state-of-the-art, best-in-class, world-class, industry-leading, award-winning, revolutionary, transformative, robust, intuitive, comprehensive, holistic, multifaceted, nuanced, pivotal, ever-evolving, ever-changing, fast-paced, future-ready, must-have, limitless
- **Nouns/phrases:** tapestry, realm, landscape, ecosystem, beacon, testament, symphony, synergy, paradigm shift, (your) journey, innovative solutions, scalable solution, powerful features, intuitive interface, simple yet powerful, actionable insights, data-driven decisions/insights, peace of mind, endless possibilities, crucial role, the power of, at your fingertips, at scale, like never before, like magic
- **Formulas:** in today's, in the age/era/world of, digital age, in seconds, in minutes not, 10x your, next level, take your * to the next level, unlock the/your (power|potential), full potential, harness the power, all-in-one, one-stop shop, everything you need, the only tool you'll ever need, the last * you'll ever need, look no further, we've got you covered, work smarter not harder, say goodbye to, say hello to, stop guessing, focus on what matters, what you do best, achieve more, without limits, the future of, reimagined, reinvented, redefined, stay ahead of the (curve|competition), experience the difference, drive impact, unlock value, empower your team, supercharge your workflow, streamline your workflow, boost productivity
- **Trust/company:** trusted by thousands, trusted by 10,000, join thousands, loved by teams, happy customers, made with ❤️, made with love, no fluff, no hassle, just results, why choose us, what sets us apart, our mission is to, we believe in empowering, our team of experts, dedicated to your success, your success is our success, every step of the way, bank-level security, enterprise-grade, 99.9% uptime, 24/7 support, 500+ integrations, 10,000+ users, 4.9/5, as seen on
- **Constructions:** it's not just, isn't just, it's more than just, not only, but also, whether you're, ready to, ensuring, empowering, enabling you to, allowing you to, so you can
- **CTAs:** get started today, start your free trial today, sign up now, learn more, no credit card required, cancel anytime
- **Blog tells:** in conclusion, let's dive in, in this article, moreover, furthermore, additionally, ultimately, it's worth noting, it's important to note, studies show, experts agree, research suggests, industry reports
- **Artifacts:** lorem ipsum, your company, example.com, [insert, {{, coming soon, oops, certainly! here's, as an AI language model, i hope this helps, 🚀, ✨, 🎉, 💡, 🎯

Sources: en.wikipedia.org "Signs of AI writing" · slopdetector.org "Signs of AI writing" · 925studios.co "AI slop web design guide" · microcopyexamples.substack.com · quotablecopy.com AI vocabulary · oliviacal.com "AI writing tells" · contentbeta.com overused AI words · copyadscontent.com · stryng.io AI sentence structures · landingrabbit.com hero/CTA guides · wisernotify.com social proof · developersdigest.tech · 0xminds.com testimonial-prompt guide · globalspex.com on mission statements · HN thread 49024805
