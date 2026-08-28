# Catalog 4/7 — Imagery, illustrations, icons & logos (#122–153)

AI-image artifacts, cliché subjects, stock illustration systems, product imagery, icon treatments, logo/favicon tells. Severity: **instant** / **strong** / **mild** (see SKILL.md).

## AI-image artifacts (audit every generated/unknown image at 200% zoom)

**122. Garbled pseudo-text in generated imagery** (instant)
Tell: signage, whiteboards, or UI inside the image where lettering is alien glyphs — "CAVTIGN" instead of CAUTION, melted keyboard keys, chart axes with squiggle-runes.
Why: diffusion models reproduce the shape of text, not spelling; one warped letter breaks the illusion instantly.
Fix: crop the frame so no in-image text is visible, or replace with a real photo/screenshot; never ship generated lettering — if a caption is needed, set it in live HTML text over the image.

**123. Hand and finger anatomy errors** (instant)
Tell: a person in the hero has six fingers, a missing thumb, an extra knuckle, or fingers fused mid-handshake.
Why: hands are the canonical AI-image failure and the first thing suspicious viewers zoom into.
Fix: choose a crop where hands are out of frame or in pockets, or swap to a real photo of the actual team/customer; if the image must stay, regenerate until hands pass a zoom-in check.

**124. Waxy, poreless skin on people** (instant)
Tell: faces with beauty-filter smoothness, no pores or micro-asymmetry, subtle plastic sheen, uniformly perfect teeth.
Why: models trained on retouched photography bake in flawless skin; viewers read the uncanny polish as synthetic within seconds.
Fix: an unretouched photo of a real person connected to the company (founder, support lead) shot in natural light — real faces with visible texture outperform synthetic perfection for trust.

**125. Everything-in-focus cinematic lighting** (strong)
Tell: image evenly, flatteringly lit from nowhere, candy-saturated, uniformly sharp foreground-to-background, dead-centered composition.
Why: "excessive perfection" is the aggregate AI-photo signature — real cameras have a light source, grain, and depth of field.
Fix: swap for a photo with one visible light source and natural depth of field; a slightly imperfect real photo beats a perfect render.

**126. Impossible background geometry** (strong)
Tell: office scene with misaligned stair steps, curved walls, "identical" lamps that all differ, chairs merging into desks, or a background blurred into abstraction to hide all of this.
Why: diffusion models fail at structural consistency away from the subject; observers subconsciously register the wrongness.
Fix: a real environment photo (even a phone shot of the actual workspace) or a solid-color/graphic hero with no fake environment at all.

**127. Melted props, jewelry, and small details** (mild)
Tell: eyeglasses fusing into temples, mismatched earrings, a subtly elongated coffee mug, hair strands becoming a scarf, watch faces without hands.
Why: object coherence at the edges of a generated image degrades; in aggregate these micro-errors trigger the "AI made this" gestalt.
Fix: audit every generated image at 200% zoom before shipping; discard frames with prop errors rather than inpainting endlessly.

## Cliché subjects

**128. "Diverse team high-fiving in glassy office" render** (instant)
Tell: hero photo of an impossibly well-lit open-plan office, multicultural group laughing at one laptop, glass boardroom handshake — AI-generated or top-of-Unsplash stock.
Why: the statistical average of "business success photo"; it appears verbatim on thousands of sites and signals no real company behind the page.
Fix: one honest photo — the actual product in use, the real (small) team, or the founder — or drop people imagery entirely and show the product.

**129. Isometric robot / cute robot mascot** (instant)
Tell: 3D or isometric render of a friendly robot typing on a laptop, holding a magnifying glass, or gesturing at floating charts, used to mean "AI product."
Why: the default visual metaphor every image generator produces for "AI"; it describes the category, not the product.
Fix: show what the AI feature actually outputs — a real screenshot of a completed task, a before/after — instead of a mascot for the concept.

**130. Purple-lit abstract 3D orbs/waves hero** (instant)
Tell: hero background of glossy floating spheres, ribbon waves, or chrome blobs in violet/indigo lighting, subtle depth-of-field, meaning nothing.
Why: the 2023–2025 default "premium tech" filler produced by every generator and template; reads as "we had nothing real to show."
Fix: a real product screenshot or a typographic hero; if abstract art is wanted, commission one distinctive graphic tied to brand geometry and use it once.

**131. Glowing orb as the AI itself** (strong)
Tell: the AI assistant depicted as a luminous gradient sphere/energy ball hovering above a hand or dashboard.
Why: the "magic orb" idiom is the industry-wide placeholder for unexplainable AI; it's now shorthand for vaporware.
Fix: depict the assistant through its interface — an actual chat/inline-suggestion screenshot with real (redacted) content.

**132. Recognizable Unsplash office/laptop stock** (strong)
Tell: the MacBook-on-desk-with-latte flatlay, hands-typing-with-code-overlay, or a viral Unsplash portrait you've seen on ten other sites.
Why: recognized stock reads as placeholder; trust drops the moment a photo is identified as stock, and popular free photos are seen everywhere.
Fix: run the competitor test — if the image could sit on a rival's site unchanged, replace it with product UI or real workspace shots, or delete the image and let the section breathe.

## Illustration systems

**133. Corporate Memphis blob people** (instant)
Tell: flat vector humans with noodle limbs, tiny heads, oversized hands, blue/purple skin, mid-leap poses on a flat background.
Why: the late-2010s big-tech house style is now universally mocked as soulless filler; AI site builders still emit it by default.
Fix: delete the illustration and show the product; if the brand needs illustration, commission one artist's distinct style (visible linework, brand palette, real proportions) and use it in 2–3 places max.

**134. unDraw illustrations with default #6C63FF accent** (instant)
Tell: the exact undraw.co flat characters (one accent color, grey blobs for scenery), often still in unDraw's default purple, on empty states and 404s.
Why: unDraw is the canonical free option — its single aesthetic is instantly recognized as zero-budget default across thousands of SaaS pages.
Fix: for empty states, a miniature real-UI preview or a plain-language message plus one action button; if keeping any illustration, recolor to exact brand tokens and edit the composition so it isn't stock-identifiable.

**135. Humaaans/Open Peeps mix-and-match characters** (strong)
Tell: modular flat/ink characters with swappable haircuts and poses (identifiable library body shapes) scattered through features.
Why: same free-library fingerprint as unDraw — recognizable because everyone assembled from the same kit.
Fix: replace with product visuals; where a human element matters, use one real photograph rather than a third library's mannequin.

**136. 3D clay/Blender-pastel characters and icons** (strong)
Tell: soft inflated 3D figures with mitten hands, pastel gradients and studio shadows, or icon packs of squishy clay rockets/locks/coins.
Why: the 2021-era claymorphism marketplace-pack look is now a generator default; it dates the site while matching no brand.
Fix: swap 3D icon packs for a single 2D icon set in one weight; reserve 3D renders for an actual product's real 3D subject matter.

**137. Library illustration colors that ignore the brand** (mild)
Tell: illustrations carry their source-library palette (unDraw purple, Storyset blue) while buttons and links use different brand colors.
Why: proves assets were downloaded, not designed — pattern-matches with other defaults into the slop gestalt.
Fix: recolor every illustration's accent layers to your exact brand tokens (SVGs make this a find-replace on fill values).

**138. Mixed generation styles across one page** (strong)
Tell: hero is photoreal AI render, feature 1 is flat vector, feature 2 is 3D clay, blog cards are fantasy paintings — no shared palette or grain.
Why: each image was prompted independently with no art direction — the defining trait of slop assembly.
Fix: pick one imagery system (e.g., real screenshots + one spot-illustration style) and re-make the outliers; run all photos through the same color grade.

## Product imagery

**139. Fake dashboard hero with meaningless charts** (instant)
Tell: hero "product shot" showing an unlabeled up-and-to-the-right line, three stat cards (2,543 / +12% / $8.4k), avatar rows, generic sidebar — data corresponding to nothing.
Why: AI builders generate plausible-dashboard filler; users pattern-match empty analytics theater to vaporware.
Fix: screenshot the real product seeded with coherent demo data — named entities, consistent date ranges, numbers that add up — and keep labels legible at the rendered size.

**140. Invented UI inside generated imagery** (strong)
Tell: "product" screenshots that are themselves AI-rendered — dashboards with smeared widgets, buttons with garbled labels, charts whose lines detach from axes.
Why: rendering a fake picture of software instead of screenshotting the software means there may be no software.
Fix: replace every rendered UI with a genuine screenshot at native resolution; if the feature is unbuilt, show a designed Figma frame honestly styled as a mock, not a photo of one.

**141. Fake terminal with three traffic-light dots** (strong)
Tell: macOS-style window chrome with red/yellow/green dots framing nonsense code or a staged `npm install your-product` that isn't real.
Why: a recurring AI-generated component fingerprint; developers immediately spot fake shell content.
Fix: paste a genuine copy-pasteable command/output (and test it), or a real code snippet with working syntax highlighting; drop the window chrome if the content can't be real.

**142. Glassmorphic blurred screenshot as backdrop** (mild)
Tell: product screenshot blurred and tinted behind hero text, or frosted `backdrop-blur` cards floating over it, so no actual UI is legible.
Why: blurring the product suggests there's nothing worth reading.
Fix: un-blur and shrink the screenshot into its own legible block beside the headline; keep text on a solid background.

**143. Stock/AI faces on testimonials** (instant)
Tell: testimonial avatars from i.pravatar.cc / randomuser.me / UI Faces or ThisPersonDoesNotExist headshots (asymmetric earrings, smeared background), paired with "Sarah Johnson, CEO."
Why: ~90% of visitors already assume landing-page testimonials are fabricated; a recognizable placeholder face confirms it and poisons the whole page.
Fix: 2–3 real quotes with permission to use real names, companies, and photos (or drop the photo and keep verifiable name + linked company); delete the testimonial section entirely before faking it.

## Icons

**144. Emoji as feature icons** (instant)
Tell: ⚡🔒📊🚀🎯 sitting above feature headings, or ✨/🚀 inside the H1 and hero badge.
Why: emoji render differently per OS, carry no brand, and are the zero-effort icon choice AI drafts default to; detectors literally scan headings for sparkle/rocket emoji.
Fix: one icon set in one weight sized to the type scale — or remove the pictograms and let specific headings carry meaning.

**145. Lucide strokes in tinted rounded squares** (instant)
Tell: 24px Lucide/Heroicons outline icons centered in 48px `bg-indigo-100 rounded-xl` (or `bg-primary/10`) tiles atop three feature cards.
Why: Lucide ships by default with shadcn scaffolds, and the tinted-tile treatment is the single most-templated feature-section pattern.
Fix: keep one icon family but delete the tinted tile containers — icons inline at text scale in a muted foreground color, optically aligned to the heading; or swap to a distinct set (Phosphor duotone, Untitled, Material Symbols) chosen to match brand voice.

**146. The lightning/shield/chart icon triad** (strong)
Tell: exactly Zap="Blazing fast", Shield="Secure by default", BarChart="Powerful analytics" — the same three concept icons on every generated features grid.
Why: the statistical center of "SaaS features" in training data; the icons describe categories, not your product.
Fix: replace concept icons with ones depicting the actual mechanism (or tiny real UI crops per feature); rewrite pairings so no icon could survive being moved to a competitor's card.

**147. Mixed icon styles on one page** (strong)
Tell: outline Lucide in the nav, filled Font Awesome in the footer, an emoji in the hero, one 3D clay icon in pricing — stroke weights and corner radii colliding.
Why: signals assembled-from-parts with no design pass; humans feel the inconsistency before they can name it.
Fix: audit every icon on the page into one set, one stroke weight, one size scale; replace stragglers one-for-one, including footer social icons.

**148. Sparkles ✨ on the AI feature** (strong)
Tell: every AI-related button/badge marked with the four-point sparkle glyph, often gradient-filled, sometimes three different sparkle drawings in one product.
Why: the sparkle is the industry-wide default that NN/g found users don't even map to AI (0% associated it unprompted) — it reads "bolted-on AI feature."
Fix: label the feature by its function in plain text ("Summarize", "Draft reply"); at most one sparkle usage with a text label — never sparkle alone as the signifier.

**149. Gradient-filled icons** (mild)
Tell: icon strokes/fills carrying a purple-to-blue linear gradient while surrounding text is flat.
Why: a template-kit affectation that pattern-matches with the AI default gradient family.
Fix: set icons to `currentColor` so they inherit text color; reserve any gradient for a single hero element.

## Logo & favicon

**150. Wordmark-is-just-Inter logo** (strong)
Tell: the "logo" is the company name typed in Inter/Poppins Bold (sometimes gradient text), indistinguishable from the nav links beside it.
Why: shows no identity work was done — the brand is a string, the same string-in-a-font every scaffold emits.
Fix: craft a real wordmark — distinct typeface not used elsewhere on the site, adjusted spacing/letterform detail, delivered as SVG with dark/light variants.

**151. Letter-in-gradient-rounded-square logo/favicon** (instant)
Tell: single initial centered in a purple-blue gradient rounded square, used as logo mark, favicon, and OG image.
Why: the auto-generated placeholder mark of every AI builder — the visual equivalent of "Untitled Project."
Fix: a drawn mark (even a simple geometric monogram with one distinctive cut/counter) in flat brand color; export as SVG favicon + 180px apple-touch-icon.

**152. AI-generated logo mark** (strong)
Tell: over-symmetrical abstract mark with tiny artifacts on curves, inconsistent corner radii, tapering line weights, warped letterforms, or a generic category symbol (leaf=wellness, shield=security, swoosh=motion).
Why: generated marks remix the same industry clichés and collapse at small sizes; customers register "amateur."
Fix: redraw the mark as clean vectors that survive three tests — 16px size, single color, and an explanation of why the shape belongs to this brand.

**153. Raster-only logo with fringe** (mild)
Tell: logo is a PNG/JPG with white halo pixels on dark backgrounds, slightly blurry at retina sizes, no one-color or reversed variant anywhere.
Why: "one glossy image" delivery is a hallmark of generated logos — no production thinking behind it.
Fix: rebuild as SVG with transparent background, plus one-color and reversed variants; swap every instance sitewide.

## VOCAB — greppable signals for this file

- Stock/illustration: `images.unsplash.com` `source.unsplash.com` `pexels.com` `undraw` `#6C63FF` `humaaans` `openpeeps` `open-doodles` `storyset` `freepik` `flaticon` `icons8` `placehold` `placekitten` `picsum.photos`
- Fake avatars: `i.pravatar.cc` `randomuser.me` `thispersondoesnotexist` `ui-avatars.com` `uifaces` `dicebear` `boringavatars`
- Icons: `lucide-react` `Sparkles` `Zap` `Shield` `BarChart` `heroicons` `react-icons` `@fortawesome` `phosphor-react`
- Visual checks: zoom generated images to 200% (hands, text, props, background) · reverse-image-search hero photos and testimonial avatars · count distinct icon styles on the page (>1 = tell) · check logo at 16px and in one color

Sources: tech.co "Ways to detect AI images" · lifehackedai.com "Why AI images look fake" · en.wikipedia.org "Corporate Memphis" · pixels.market unDraw review · rubberduckers.co.uk on generic stock · nngroup.com "AI sparkles icon problem" · manishtamang.com "Icons for vibecoded sites" · unbounce.com on testimonial trust · lefthd.com "How to spot an AI-generated logo" · growthguys.tech · screenhance.com · isthatvibecoded.com · 925studios.co
