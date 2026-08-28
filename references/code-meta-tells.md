# Catalog 7/7 — Tool fingerprints, code & meta tells (#252–284)

Builder watermarks, framework leftovers, head/SEO, dead wiring, bundle smells, a11y/perf tells. These are found by viewing source, opening devtools, and running the grep sweep — many are invisible in a screenshot but instantly out the site to anyone who looks. Severity: **instant** / **strong** / **mild** (see SKILL.md).

## Builder watermarks & fingerprints

**252. Lovable badge** (instant)
Tell: floating "Edit with Lovable" / "Made with Lovable" pill pinned bottom-right, injected as element id `lovable-badge`.
Why: the free-tier watermark literally names the generator.
Fix: disable it in Project Settings → Publishing (paid plan) or export the repo and self-host; don't just CSS-hide it while staying on the preview host.

**253. Bolt / v0 / Replit badge** (instant)
Tell: "Made in Bolt" edge pin, "Built with v0" footer line, Replit "Made with Replit" banner.
Why: builder free tiers stamp their output — instant attribution.
Fix: remove the badge component/footer line on export, or upgrade and republish; verify on the live URL, not just the editor.

**254. Builder subdomain in production** (instant)
Tell: real traffic served from *.lovable.app, *.bolt.host, *.replit.app, *.repl.co, *.base44.app, *.v0.dev, *.vercel.app, *.netlify.app.
Why: preview infrastructure shipped as the company's public address.
Fix: buy a domain, attach it in the host dashboard, 301 the old subdomain, set canonical to the custom domain.

**255. gptengineer.js runtime script** (strong)
Tell: `<script src="https://cdn.gpteng.co/gptengineer.js">` in head (also `/__l5e/` platform scripts).
Why: Lovable's editor runtime left running in production — a third-party script visitors never needed.
Fix: delete the script tag from index.html in the exported repo; audit the head for any cdn.gpteng.co reference.

**256. Builder generator/meta tags** (strong)
Tell: `lovable-tagger` meta, `<meta name="generator">` naming the builder, `@base44/sdk` strings in the bundle.
Why: the toolchain self-identifies in served HTML.
Fix: remove the tagger plugin from vite.config, strip generator meta, tree-shake unused builder SDKs.

**257. /lovable-uploads/ asset paths** (strong)
Tell: images served from `/lovable-uploads/<uuid>.png` — Lovable's most durable marker, surviving export.
Why: the tool's upload directory structure fossilized into the site.
Fix: move assets to meaningful paths (/images/team-oslo.jpg), compress them, update references.

**258. v0 placeholder.svg images** (strong)
Tell: `<img src="/placeholder.svg?height=400&width=600">` throughout — v0's stock image stub never replaced.
Why: a generation-time placeholder shipped as final art.
Fix: replace every placeholder.svg with a real, art-directed asset or remove the image slot.

## Framework leftovers

**259. Default page title** (instant)
Tell: browser tab reads "Create Next App", "Vite + React", "React App", "My App", or the builder's project-name slug.
Why: scaffold metadata untouched — the tab confesses before the page loads.
Fix: a real title template (Brand — what it does) in layout metadata plus per-page titles.

**260. Default framework favicon** (instant)
Tell: Vercel/Next triangle, Vite lightning bolt (vite.svg), CRA React atom, or no favicon (gray globe).
Why: the first brand pixel a user sees belongs to the framework. (Gradient-square placeholder mark: #151.)
Fix: generate a favicon set from the actual logo (SVG favicon + apple-touch-icon + 512px manifest icon), placed per framework convention.

**261. Scaffold package name leakage** (strong)
Tell: "my-app", "my-v0-project", "vite-react-typescript-starter" appearing in manifest.json, source maps, error stacks, or the repo.
Why: the project was never renamed after `create-*` ran.
Fix: rename package.json, set real name/short_name in the web manifest, rebuild.

**262. Default README in a public repo** (mild)
Tell: "Getting Started with Create React App" or v0's "Automatically synced with your v0.dev deployments" README on the linked GitHub.
Why: the repo documents the generator, not the product.
Fix: write a README about the actual product, or make the repo private.

**263. Stock 404 / blank error routes** (strong)
Tell: framework-default "404 | This page could not be found", or an SPA rendering a blank white page for bad routes.
Why: error paths are never generated unless asked; no human ever tested them. (404 wording: #221.)
Fix: a branded 404 with navigation back; add a catch-all route in the router.

## Head & SEO

**264. Empty SPA shell source** (strong)
Tell: view-source shows only `<div id="root"></div>` plus `/assets/index-[hash].js` — no readable content.
Why: the Vite client-rendered default of Bolt/Lovable; hand-built marketing sites usually serve real HTML.
Fix: prerender or SSR the public pages (Next/Astro/vite-ssg) so content exists in source; keep the app itself CSR if needed.

**265. Missing or builder-default OG tags** (strong)
Tell: no og:title/og:image/twitter:card, or sharing shows the builder's default preview card.
Why: one-shot generation skips social metadata; link shares expose it instantly.
Fix: complete OG + Twitter meta per page and a branded 1200×630 og:image.

**266. Generic or missing meta description** (strong)
Tell: absent description, duplicated titles across pages, or AI boilerplate ("The all-in-one platform to elevate your workflow").
Why: metadata reads as statistical filler, not a company describing itself.
Fix: hand-write unique title + description per page naming who it's for and what it does.

**267. No robots.txt or sitemap** (mild)
Tell: /robots.txt and /sitemap.xml both 404.
Why: chat-to-deploy pipelines skip crawl infrastructure entirely.
Fix: add robots.txt referencing a generated sitemap.xml; submit to Search Console.

**268. No structured data** (mild)
Tell: zero JSON-LD on a site type that warrants it (org, product, FAQ, articles).
Why: generated sites stop at visible pixels; the machine-readable layer is absent.
Fix: minimal accurate JSON-LD (Organization + page-type schema) — never fabricate ratings.

## Dead wiring

**269. href="#" dead links beyond the footer** (strong)
Tell: nav items and CTAs with `href="#"` or empty onClick; links to /docs, /pricing, /api that 404. (Footer-specific version: #49.)
Why: the LLM generates a plausible navbar for pages it never built.
Fix: delete links to nothing; build or stub the real destinations; every clickable element gets a working target before launch.

**270. Decorative social icons** (strong)
Tell: Twitter/LinkedIn/Instagram icons linking to "#" or the platforms' homepages.
Why: an icon row generated as decoration; no accounts were ever wired.
Fix: link real profiles or remove the row — an absent icon is better than a lying one.

**271. Ghost contact form** (strong)
Tell: form fires a success toast with no network request in devtools, or submits nowhere; no email ever arrives.
Why: AI scaffolds form UI and hardcodes the "Thanks, we'll be in touch!" state without a backend.
Fix: wire to a real endpoint (API route, Formspree, Resend), add error states, send a confirmation copy, test end-to-end.

## Bundle & source smells

**272. Default Tailwind palette in compiled CSS** (strong)
Tell: production CSS full of untouched blue-500/indigo-600/violet-500 and default gray ramps; no custom theme tokens anywhere.
Why: Tailwind's defaults are baked into LLM training — `bg-indigo-500` is the statistical mean. (The visual result: #64; shadcn tokens: #90.)
Fix: define a brand palette as theme tokens and lint against raw default color utilities.

**273. Cookie-cutter component taxonomy exposed** (mild)
Tell: HeroSection, FeatureCard, CTASection, TestimonialCard legible in shipped class names, source maps, or data attributes.
Why: the LLM's canonical landing-page vocabulary left visible in production.
Fix: disable prod source maps and strip build artifacts (internal naming is fine — just don't ship it legibly).

**274. HTML comments left in served markup** (strong)
Tell: `<!-- Hero Section -->`, `<!-- Testimonials -->`, decorative divider comments, emoji in markup.
Why: generation artifacts a real build pipeline would strip.
Fix: enable comment-stripping minification in the build.

**275. Hardcoded fake-data arrays in the bundle** (mild)
Tell: testimonials/stats/pricing as literal JS arrays in the client bundle with obviously invented entries.
Why: content baked in at generation time — greppable proof the social proof is fiction.
Fix: move real content to a CMS/markdown source; delete invented entries outright.

**276. Exposed secrets in the client bundle** (mild)
Tell: `sk-` API keys, Supabase service keys, or .env values greppable in served JS.
Why: the vibe coder pasted env config into client code — a security incident doubling as an origin tell.
Fix: move secrets server-side immediately and rotate every leaked key. (Flag this to the user as a security issue, not just a slop finding.)

**277. Console errors on load** (strong)
Tell: devtools shows 404'd assets, failed fetches to localhost/Supabase, unhandled promise rejections on first paint.
Why: shipped without devtools ever being opened.
Fix: clear every red line before deploy; remove dead API calls and missing-asset references.

**278. Hydration warnings** (strong)
Tell: React "Hydration failed" / "Text content does not match server-rendered HTML" in console.
Why: generated components render Date()/random/locale content differently on server vs client — a hallmark of unreviewed AI React.
Fix: make renders deterministic; move client-only values into effects; `suppressHydrationWarning` only where legitimate.

## Accessibility & performance tells

**279. Missing focus states** (strong)
Tell: `outline-none` with no :focus-visible replacement — tabbing is invisible.
Why: generated CSS strips browser defaults and nobody keyboard-tested.
Fix: :focus-visible rings in the brand accent on every interactive element; tab through every page once.

**280. Missing or nonsense alt text** (strong)
Tell: `alt=""` on meaningful images, alt="image", alt="hero-image-2", or the attribute absent entirely.
Why: the accessibility pass never ran; screen readers get nothing.
Fix: functional alt describing content/purpose; empty alt only for genuinely decorative images.

**281. aria-label noise** (mild)
Tell: aria-labels on non-interactive divs, labels duplicating visible text, role attributes sprinkled without logic.
Why: the model performs accessibility theater instead of semantics — and it actively harms screen-reader UX.
Fix: remove redundant ARIA, prefer semantic HTML elements, test once with a screen reader.

**282. Broken heading hierarchy** (mild)
Tell: multiple H1s, jumps from H1 to H4, styled divs where headings belong.
Why: sections generated independently with no document-level structure.
Fix: one H1 per page, sequential levels; audit with a headings-map extension.

**283. Multi-megabyte hero images** (strong)
Tell: 3–8MB PNG or AI-generated hero art, no srcset, no lazy loading, LCP over 4s.
Why: asset optimization isn't part of the prompt-to-deploy flow.
Fix: WebP/AVIF, responsive srcset/sizes, preload the LCP image, lazy-load below the fold.

**284. Default selection/tap details** (mild)
Tell: default blue ::selection and stock mobile tap-highlight on an otherwise "branded" site.
Why: the detail layer below the template was never considered.
Fix: set ::selection to a brand tint and tune -webkit-tap-highlight-color — cheap signals of care.

## VOCAB — the grep sweep (run against source AND built output)

- Builder marks: `Made with Lovable` `Edit with Lovable` `lovable-badge` `lovable.app` `lovable-uploads` `lovable-tagger` `cdn.gpteng.co` `gptengineer` `Built with v0` `v0.dev` `my-v0-project` `placeholder.svg?height=` `Made in Bolt` `bolt.new` `bolt.host` `stackblitz` `replit.app` `repl.co` `Made with Replit` `base44` `vercel.app` `netlify.app`
- Scaffold: `Create Next App` `Generated by create next app` `Vite + React` `vite.svg` `React App` `Getting Started with Create React App` `Automatically synced with your v0.dev` `my-app` `name="generator"`
- Dead wiring: `href="#"` `example.com` `mailto:` (absent where a contact should be) `action=""` (forms)
- Hygiene: `lorem` `TODO` `{{` `[Your` `© 2024` `<!-- Hero` `<!-- Testimonials` `HeroSection` `FeatureCard` `TestimonialCard` `CTASection`
- Security/a11y/perf: `sk-` `supabase.co` (client-side service keys) `outline-none` `suppressHydrationWarning` `alt=""` `alt="image"` — plus devtools checks: console clean? network 404s? Lighthouse a11y + LCP.

Sources: capacity.so Lovable-badge guide · vibe0.com.au "How to tell if a website is vibe coded" · slopdar.com detection guide · sinton.agency "How to spot a vibe-coded website" · dev.to "I analyzed 100 vibe-coded websites" · dev.to "Vibe coded sites are bad at SEO" · vibe-coded.lol · isthatvibecoded.com · freedesignmd.com · prg.sh · HN thread 43502363
