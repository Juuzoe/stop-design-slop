# Catalog 7/7: Tool fingerprints, code & meta tells (#252–284, #286)

Builder watermarks, framework leftovers, head/SEO, dead wiring, bundle smells, a11y and perf tells. You find these by viewing source, opening devtools, and running the grep sweep at the end of this file. A screenshot hides most of them. Anyone who opens the source sees them in seconds. Severity: **instant** / **strong** / **mild** (see SKILL.md).

## Builder watermarks & fingerprints

**252. Lovable badge** (instant)
Tell: floating "Edit with Lovable" / "Made with Lovable" pill pinned bottom-right, injected as element id `lovable-badge`.
Why: Lovable stamps its own name on free-tier projects, so every visitor reads which tool built the site.
Fix: turn it off in Project Settings → Publishing (paid plan), or export the repo and host it yourself. Hiding it with CSS while you stay on the preview host does not count.

**253. Bolt / v0 / Replit badge** (instant)
Tell: "Made in Bolt" edge pin, "Built with v0" footer line, Replit "Made with Replit" banner.
Why: each builder stamps its free-tier output, so the first person to reach the footer learns what made the page.
Fix: delete the badge component or footer line when you export, or upgrade and republish. Check the live URL afterward, since the editor preview can differ.

**254. Builder subdomain in production** (instant)
Tell: real traffic served from *.lovable.app, *.bolt.host, *.replit.app, *.repl.co, *.base44.app, *.v0.dev, *.vercel.app, *.netlify.app.
Why: someone shipped preview infrastructure as the company's public address.
Fix: buy a domain, attach it in the host dashboard, 301 the old subdomain, and point the canonical tag at the new one.

**255. gptengineer.js runtime script** (strong)
Tell: `<script src="https://cdn.gpteng.co/gptengineer.js">` in head (also `/__l5e/` platform scripts).
Why: nobody removed Lovable's editor runtime before launch, so visitors download a third-party script the site never uses.
Fix: delete the script tag from index.html in the exported repo, then search the head for any other cdn.gpteng.co reference.

**256. Builder generator/meta tags** (strong)
Tell: `lovable-tagger` meta, `<meta name="generator">` naming the builder, `@base44/sdk` strings in the bundle.
Why: nobody stripped the build plugin, so the tool's name ships inside the HTML you serve.
Fix: remove the tagger plugin from vite.config, strip the generator meta, and tree-shake the builder SDKs you no longer call.

**257. /lovable-uploads/ asset paths** (strong)
Tell: images served from `/lovable-uploads/<uuid>.png`, the marker that survives export and outlives every other Lovable trace.
Why: the team kept the tool's upload directory as the site's asset structure.
Fix: move the assets to paths that describe them (/images/team-oslo.jpg), compress them, and update every reference.

**258. v0 placeholder.svg images** (strong)
Tell: `<img src="/placeholder.svg?height=400&width=600">` across the page, because nobody replaced v0's stock image stub.
Why: someone shipped a generation-time placeholder as final art.
Fix: replace every placeholder.svg with a real art-directed asset, or cut the image slot.

## Framework leftovers

**259. Default page title** (instant)
Tell: browser tab reads "Create Next App", "Vite + React", "React App", "My App", or the builder's project-name slug.
Why: nobody edited the scaffold metadata. A visitor reads the framework's name in the tab before the page paints.
Fix: write a title template in the layout metadata (Brand: what it does) and give every page its own title.

**260. Default framework favicon** (instant)
Tell: Vercel/Next triangle, Vite lightning bolt (vite.svg), CRA React atom, or no favicon (gray globe).
Why: the first brand pixel a user sees belongs to the framework. (Gradient-square placeholder mark: #151.)
Fix: generate a favicon set from the real logo (SVG favicon, apple-touch-icon, 512px manifest icon) and put the files where your framework expects them.

**261. Scaffold package name leakage** (strong)
Tell: "my-app", "my-v0-project", "vite-react-typescript-starter" appearing in manifest.json, source maps, error stacks, or the repo.
Why: nobody renamed the project after `create-*` ran.
Fix: rename it in package.json, set name and short_name in the web manifest, then rebuild.

**262. Default README in a public repo** (mild)
Tell: "Getting Started with Create React App" or v0's "Automatically synced with your v0.dev deployments" README on the linked GitHub.
Why: the README documents the generator while the product goes undocumented.
Fix: write a README about the product, or make the repo private.

**263. Stock 404 / blank error routes** (strong)
Tell: framework-default "404 | This page could not be found", or an SPA rendering a blank white page for bad routes.
Why: a model builds error paths when you ask and not before, and nobody typed a bad URL to check. (404 wording: #221.)
Fix: build a branded 404 that offers a way back, and add a catch-all route in the router.

## Head & SEO

**264. Empty SPA shell source** (strong)
Tell: view-source shows nothing but `<div id="root"></div>` plus `/assets/index-[hash].js`, with no readable content.
Why: Bolt and Lovable ship the Vite client-rendered default. Teams who hand-build a marketing site tend to serve real HTML.
Fix: prerender or SSR the public pages (Next/Astro/vite-ssg) so the content lives in the source. The app behind the login can stay client-rendered.

**265. Missing or builder-default OG tags** (strong)
Tell: no og:title/og:image/twitter:card, or sharing shows the builder's default preview card.
Why: one-shot generation skips social metadata, and the first person who pastes the link into Slack sees the result.
Fix: write full OG and Twitter meta for every page, and draw a branded 1200×630 og:image.

**266. Generic or missing meta description** (strong)
Tell: absent description, duplicated titles across pages, or AI boilerplate ("The all-in-one platform to elevate your workflow").
Why: a model wrote the description for no company in particular.
Fix: hand-write a title and description per page that name who the page is for and what it does.

**267. No robots.txt or sitemap** (mild)
Tell: /robots.txt and /sitemap.xml both 404.
Why: chat-to-deploy pipelines skip crawl infrastructure.
Fix: add a robots.txt that points at a generated sitemap.xml, then submit it to Search Console.

**268. No structured data** (mild)
Tell: zero JSON-LD on a site type that warrants it (org, product, FAQ, articles).
Why: the generator stops at the visible pixels, and nobody added the machine-readable layer afterward.
Fix: add small, accurate JSON-LD (Organization plus the page-type schema). Never invent ratings.

## Dead wiring

**269. href="#" dead links beyond the footer** (strong)
Tell: nav items and CTAs with `href="#"` or empty onClick; links to /docs, /pricing, /api that 404. (Footer-specific version: #49.)
Why: the model writes a plausible navbar for pages it never built.
Fix: delete the links that go nowhere, build or stub the destinations you meant to have, and give every clickable element a working target before launch.

**270. Decorative social icons** (strong)
Tell: Twitter/LinkedIn/Instagram icons linking to "#" or the platforms' homepages.
Why: the model drew an icon row as decoration, and nobody ever opened the accounts.
Fix: link the real profiles or delete the row. A missing icon costs less than one that lies.

**271. Ghost contact form** (strong)
Tell: form fires a success toast with no network request in devtools, or submits nowhere; no email ever arrives.
Why: AI scaffolds form UI and hardcodes the "Thanks, we'll be in touch!" state without a backend.
Fix: wire it to a real endpoint (API route, Formspree, Resend), add error states, send a confirmation copy, and walk the whole path yourself.

## Bundle & source smells

**272. Default Tailwind palette in compiled CSS** (strong)
Tell: production CSS full of untouched blue-500/indigo-600/violet-500 and default gray ramps; no custom theme tokens anywhere.
Why: Tailwind's defaults saturate the training data, which makes `bg-indigo-500` the statistical mean. (The visual result: #64; shadcn tokens: #90.)
Fix: define a brand palette as theme tokens, then lint for raw default color utilities.

**273. Cookie-cutter component taxonomy exposed** (mild)
Tell: HeroSection, FeatureCard, CTASection, TestimonialCard legible in shipped class names, source maps, or data attributes.
Why: you are shipping the model's canonical landing-page vocabulary where any visitor can read it.
Fix: disable production source maps and strip build artifacts. Name your internals whatever you like, then keep those names out of the served bundle.

**274. HTML comments left in served markup** (strong)
Tell: `<!-- Hero Section -->`, `<!-- Testimonials -->`, decorative divider comments, emoji in markup.
Why: a real build pipeline strips these, so finding them says nobody set one up.
Fix: turn on comment-stripping minification in the build.

**275. Hardcoded fake-data arrays in the bundle** (mild)
Tell: testimonials/stats/pricing as literal JS arrays in the client bundle, with entries anyone can see were invented.
Why: someone baked the content in at generation time, which leaves greppable proof that the social proof is fiction.
Fix: move real content into a CMS or markdown source, and delete the invented entries.

**276. Exposed secrets in the client bundle** (mild)
Tell: `sk-` API keys, Supabase service keys, or .env values greppable in served JS.
Why: whoever built it pasted env config into client code. That is a security incident before it is an origin tell.
Fix: move the secrets server-side and rotate every leaked key today. (Tell the user this is a security issue and give it that priority.)

**277. Console errors on load** (strong)
Tell: devtools shows 404'd assets, failed fetches to localhost/Supabase, unhandled promise rejections on first paint.
Why: nobody opened devtools before shipping.
Fix: clear every red line before you deploy, and delete the dead API calls and missing-asset references behind them.

**278. Hydration warnings** (strong)
Tell: React "Hydration failed" / "Text content does not match server-rendered HTML" in console.
Why: generated components render Date(), random values, and locale strings one way on the server and another in the browser, which is where unreviewed AI React shows itself first.
Fix: make the render deterministic, move client-only values into effects, and reach for `suppressHydrationWarning` where the mismatch is legitimate.

## Accessibility & performance tells

**279. Missing focus states** (strong)
Tell: `outline-none` with no :focus-visible replacement, so tabbing through the page shows nothing.
Why: the generated CSS strips the browser default, and nobody tabbed through the page afterward.
Fix: put a :focus-visible ring in the brand accent on every interactive element, then tab through each page once.

**280. Missing or nonsense alt text** (strong)
Tell: `alt=""` on meaningful images, alt="image", alt="hero-image-2", or no alt attribute at all.
Why: nobody ran the accessibility pass, so screen-reader users hear nothing useful.
Fix: write alt text that describes what the image shows or does. Reserve empty alt for images that carry no information.

**281. aria-label noise** (mild)
Tell: aria-labels on non-interactive divs, labels duplicating visible text, role attributes sprinkled without logic.
Why: the model performs accessibility theater in place of semantics, and the result makes screen-reader navigation worse than plain HTML would.
Fix: delete the redundant ARIA, reach for the semantic element instead, and run one pass with a screen reader.

**282. Broken heading hierarchy** (mild)
Tell: multiple H1s, jumps from H1 to H4, styled divs where headings belong.
Why: the model wrote each section on its own, and nobody minded the document outline.
Fix: one H1 per page and no skipped levels. Check the result with a headings-map extension.

**283. Multi-megabyte hero images** (strong)
Tell: 3–8MB PNG or AI-generated hero art, no srcset, no lazy loading, LCP over 4s.
Why: the prompt-to-deploy flow has no step where anyone compresses an image.
Fix: export WebP or AVIF, add responsive srcset and sizes, preload the LCP image, and lazy-load everything below the fold.

**284. Default selection/tap details** (mild)
Tell: default blue ::selection and stock mobile tap-highlight on an otherwise "branded" site.
Why: nobody looked past the template at the details the browser fills in on its own.
Fix: set ::selection to a brand tint and tune -webkit-tap-highlight-color. Both take a minute, and the kind of visitor who notices is the kind you want.

**286. Version or build stamp on a marketing page** (mild)
Tell: `v1.4.2`, `Build 0048`, `last sync 4s ago · main` in a landing-page footer or inside a hero preview.
Why: these are devtool fixtures borrowed to look technical. A docs site, an app shell or a changelog earns a build stamp; a marketing page has no use for one, so its presence marks copied furniture.
Fix: delete it from marketing surfaces. Keep build and version strings in docs, the app shell, or a dated changelog, where a reader can act on them.

## VOCAB: the grep sweep (run against source AND built output)

- Builder marks: `Made with Lovable` `Edit with Lovable` `lovable-badge` `lovable.app` `lovable-uploads` `lovable-tagger` `cdn.gpteng.co` `gptengineer` `Built with v0` `v0.dev` `my-v0-project` `placeholder.svg?height=` `Made in Bolt` `bolt.new` `bolt.host` `stackblitz` `replit.app` `repl.co` `Made with Replit` `base44` `vercel.app` `netlify.app`
- Scaffold: `Create Next App` `Generated by create next app` `Vite + React` `vite.svg` `React App` `Getting Started with Create React App` `Automatically synced with your v0.dev` `my-app` `name="generator"`
- Dead wiring: `href="#"` `example.com` `mailto:` (absent where a contact should be) `action=""` (forms)
- Hygiene: `lorem` `TODO` `{{` `[Your` `© 2024` `<!-- Hero` `<!-- Testimonials` `HeroSection` `FeatureCard` `TestimonialCard` `CTASection`
- Security/a11y/perf: `sk-` `supabase.co` (client-side service keys) `outline-none` `suppressHydrationWarning` `alt=""` `alt="image"`. Then run the devtools checks: console clean? network 404s? Lighthouse a11y + LCP.

Sources: capacity.so Lovable-badge guide · vibe0.com.au "How to tell if a website is vibe coded" · slopdar.com detection guide · sinton.agency "How to spot a vibe-coded website" · dev.to "I analyzed 100 vibe-coded websites" · dev.to "Vibe coded sites are bad at SEO" · vibe-coded.lol · isthatvibecoded.com · freedesignmd.com · prg.sh · HN thread 43502363
