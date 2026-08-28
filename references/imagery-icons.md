# Catalog 4/7: Imagery, illustrations, icons & logos (#122–153)

AI-image artifacts, cliché subjects, stock illustration systems, product imagery, icon treatments, logo/favicon tells. Severity: **instant** / **strong** / **mild** (see SKILL.md).

## AI-image artifacts (audit every generated/unknown image at 200% zoom)

**122. Garbled pseudo-text in generated imagery** (instant)
Tell: signage, whiteboards, or UI inside the image carries alien glyphs: "CAVTIGN" where CAUTION belongs, melted keyboard keys, chart axes ruled in squiggle-runes.
Why: diffusion models copy the shape of letters and get the spelling wrong, and one warped word breaks the illusion.
Fix: crop the frame so no in-image text shows, or swap in a real photo or screenshot; when you need a caption, set it in live HTML text over the image instead of shipping generated lettering.

**123. Hand and finger anatomy errors** (instant)
Tell: a person in the hero has six fingers, a missing thumb, or fingers fused mid-handshake.
Why: hands are the canonical AI-image failure, and a suspicious viewer zooms there first.
Fix: pick a crop with hands out of frame or in pockets, or swap to a real photo of your team or a customer. If the image has to stay, regenerate until the hands survive a zoom-in check.

**124. Waxy, poreless skin on people** (instant)
Tell: faces with beauty-filter smoothness, no pores or micro-asymmetry, a plastic sheen across the cheekbones.
Why: models trained on retouched photography bake in flawless skin, and viewers read the polish as synthetic within seconds.
Fix: use an unretouched photo of someone connected to the company, a founder or a support lead, shot in natural light and left with its pores and asymmetries intact.

**125. Everything-in-focus cinematic lighting** (strong)
Tell: flat even light with no visible source, candy saturation, sharp focus from foreground to background, subject parked dead center.
Why: "excessive perfection" is the aggregate AI-photo signature; every real camera leaves behind a light source, grain, and a plane of focus.
Fix: use a photo with one visible light source and natural depth of field, and accept the flaws that come with it.

**126. Impossible background geometry** (strong)
Tell: an office scene with misaligned stair steps, chairs merging into desks, "identical" lamps that all differ, or a background blurred into abstraction that hides the lot.
Why: diffusion models lose structural consistency away from the subject, and viewers register the wrongness before they can name it.
Fix: use a real environment photo, where a phone shot of the actual workspace does the job, or a solid-color hero with no invented room behind it.

**127. Melted props, jewelry, and small details** (mild)
Tell: eyeglasses fusing into temples, mismatched earrings, hair strands turning into a scarf, watch faces with no hands.
Why: generated images lose object coherence at the edges, and enough micro-errors add up to the "AI made this" gestalt.
Fix: audit every generated image at 200% zoom before shipping, and discard frames with prop errors instead of inpainting them one by one.

## Cliché subjects

**128. "Diverse team high-fiving in glassy office" render** (instant)
Tell: hero photo of a bright open-plan office, a multicultural group laughing at one laptop, or a glass-boardroom handshake, generated or lifted from the top of Unsplash.
Why: it is the statistical average of "business success photo", it runs verbatim on thousands of sites, and it tells a visitor no real company stands behind the page.
Fix: use one honest photo, the product in use or the actual small team, or drop people imagery and show the product.

**129. Isometric robot / cute robot mascot** (instant)
Tell: 3D or isometric render of a friendly robot typing on a laptop, holding a magnifying glass, or gesturing at floating charts, standing in for "AI product."
Why: every image generator reaches for this metaphor when asked to draw "AI", so it names your category and says nothing about your product.
Fix: show what the feature produces, a screenshot of a completed task or a before/after, in place of a mascot for the concept.

**130. Purple-lit abstract 3D orbs/waves hero** (instant)
Tell: hero background of glossy floating spheres, ribbon waves, or chrome blobs lit violet-indigo, shallow depth of field, no subject in sight.
Why: generators and templates pumped out this "premium tech" filler across 2023–2025, and visitors read it as an admission you had nothing real to show.
Fix: use a real product screenshot or a typographic hero. If you want abstract art, commission one distinctive graphic tied to your brand geometry and use it once.

**131. Glowing orb as the AI itself** (strong)
Tell: a luminous gradient sphere or energy ball hovering above a hand or a dashboard, standing in for the assistant.
Why: the "magic orb" idiom became the industry placeholder for AI nobody could explain, and readers now take it as shorthand for vaporware.
Fix: show the assistant through its interface, a chat or inline-suggestion screenshot carrying real content, redacted where you need to.

**132. Recognizable Unsplash office/laptop stock** (strong)
Tell: the MacBook-on-desk-with-latte flatlay, hands-typing-with-code-overlay, or a viral Unsplash portrait you have seen on ten other sites.
Why: a visitor who recognizes the photo files it as a placeholder, and the most popular free photos turn up everywhere, so plenty of visitors will have met this one.
Fix: run the competitor test. If the image could sit on a rival's site unchanged, replace it with product UI or a shot of the real workspace, or delete it and let the section breathe.

## Illustration systems

**133. Corporate Memphis blob people** (instant)
Tell: flat vector humans with noodle limbs, tiny heads, oversized hands, and blue or purple skin, frozen mid-leap on a flat background.
Why: designers mocked this late-2010s big-tech house style out of fashion years ago, and AI site builders still emit it as a default.
Fix: delete the illustration and show the product. If the brand needs illustration, commission one artist with a distinct style (visible linework, brand palette, real proportions) and use it in 2–3 places at most.

**134. unDraw illustrations with default #6C63FF accent** (instant)
Tell: the exact undraw.co flat characters (one accent color, grey blobs for scenery), often still in unDraw's default purple, on empty states and 404s.
Why: unDraw is the canonical free option, and its one aesthetic has run on thousands of SaaS pages, so readers clock it as the zero-budget default.
Fix: for empty states, use a miniature preview of the real UI or a plain-language message with one action button. If you keep an illustration, recolor it to your exact brand tokens and edit the composition so nobody can trace it back to the library.

**135. Humaaans/Open Peeps mix-and-match characters** (strong)
Tell: modular flat or ink characters with swappable haircuts and poses, carrying the library's recognizable body shapes, scattered through the features.
Why: the same free-library fingerprint as unDraw, recognizable because every builder assembled from the same kit.
Fix: replace them with product visuals. Where a human element matters, use one real photograph instead of a third library's mannequin.

**136. 3D clay/Blender-pastel characters and icons** (strong)
Tell: soft inflated 3D figures with mitten hands and studio shadows, or icon packs of squishy clay rockets, locks, and coins.
Why: generators now default to the 2021-era claymorphism marketplace pack, which dates the site and matches no brand.
Fix: swap 3D icon packs for a single 2D icon set in one weight, and reserve 3D renders for products whose real subject matter is 3D.

**137. Library illustration colors that ignore the brand** (mild)
Tell: illustrations carry their source-library palette (unDraw purple, Storyset blue) while buttons and links run your brand colors.
Why: it shows that someone downloaded the assets and stopped there, and the mismatch joins the other defaults in the slop gestalt.
Fix: recolor every illustration's accent layers to your exact brand tokens. In SVGs this is a find-replace on fill values.

**138. Mixed generation styles across one page** (strong)
Tell: the hero is a photoreal AI render, feature 1 is flat vector, feature 2 is 3D clay, and the blog cards are fantasy paintings, with no palette or grain in common.
Why: someone prompted each image on its own with no art direction, which is what slop assembly looks like from the outside.
Fix: pick one imagery system (real screenshots plus a single spot-illustration style, say) and remake the outliers, then run every photo through the same color grade.

## Product imagery

**139. Fake dashboard hero with meaningless charts** (instant)
Tell: a hero "product shot" with an unlabeled up-and-to-the-right line, three stat cards (2,543 / +12% / $8.4k), avatar rows, and a generic sidebar, none of it tied to real data.
Why: AI builders emit plausible-dashboard filler, and users have learned to read empty analytics theater as vaporware.
Fix: screenshot the real product seeded with coherent demo data (named entities, consistent date ranges, numbers that add up) and keep the labels legible at the size you render.

**140. Invented UI inside generated imagery** (strong)
Tell: "product" screenshots that are themselves AI renders, with smeared widgets, buttons carrying garbled labels, and chart lines that detach from their axes.
Why: a builder who renders a picture of software instead of screenshotting it may not have the software.
Fix: replace every rendered UI with a genuine screenshot at native resolution. If the feature is unbuilt, show a designed Figma frame styled as a mock and label it as one.

**141. Fake terminal with three traffic-light dots** (strong)
Tell: macOS-style window chrome with red, yellow, and green dots framing nonsense code or a staged `npm install your-product` that nobody can run.
Why: it is a recurring fingerprint of generated components, and developers spot fake shell content on sight.
Fix: paste a genuine copy-pasteable command with its output and test it, or a real code snippet with working syntax highlighting. Drop the window chrome when the content can't be real.

**142. Glassmorphic blurred screenshot as backdrop** (mild)
Tell: the product screenshot sits blurred and tinted behind hero text, or frosted `backdrop-blur` cards float over it, leaving no UI legible.
Why: when you blur the product, visitors conclude there was nothing worth reading.
Fix: un-blur the screenshot and shrink it into its own legible block beside the headline, with the text on a solid background.

**143. Stock/AI faces on testimonials** (instant)
Tell: testimonial avatars pulled from i.pravatar.cc / randomuser.me / UI Faces, or ThisPersonDoesNotExist headshots (asymmetric earrings, smeared background), paired with "Sarah Johnson, CEO."
Why: about 90% of visitors assume landing-page testimonials are fabricated, and a recognizable placeholder face confirms the suspicion for the rest of the page.
Fix: get 2–3 real quotes with permission to use names, companies, and photos, or drop the photo and keep a verifiable name with a linked company. Delete the testimonial section before you fake one.

## Icons

**144. Emoji as feature icons** (instant)
Tell: ⚡🔒📊🚀🎯 sitting above feature headings, or ✨/🚀 wedged into the H1 and hero badge.
Why: emoji change shape from one OS to the next, carry no brand, and cost nothing to add, which is why AI drafts reach for them; slop detectors scan headings for the sparkle and rocket glyphs.
Fix: use one icon set in one weight, sized to the type scale, or remove the pictograms and let specific headings carry the meaning.

**145. Lucide strokes in tinted rounded squares** (instant)
Tell: 24px Lucide/Heroicons outline icons centered in 48px `bg-indigo-100 rounded-xl` (or `bg-primary/10`) tiles atop three feature cards.
Why: shadcn scaffolds ship Lucide out of the box, and the tinted tile is the most templated feature-section treatment in circulation.
Fix: keep one icon family and delete the tinted tile containers, so the icons sit inline at text scale in a muted foreground color, aligned to the heading by eye. Or move to a set with more character (Phosphor duotone, Untitled, Material Symbols) picked against your brand voice.

**146. The lightning/shield/chart icon triad** (strong)
Tell: Zap="Blazing fast", Shield="Secure by default", BarChart="Powerful analytics", the same three concept icons on every generated features grid.
Why: this trio sits at the statistical center of "SaaS features" in the training data, so it names your category and leaves your product undescribed.
Fix: pick icons that depict the mechanism each feature uses, or crop a small piece of the real UI per feature, and rewrite the pairings so none would survive a move to a competitor's card.

**147. Mixed icon styles on one page** (strong)
Tell: outline Lucide in the nav, filled Font Awesome in the footer, an emoji in the hero, a 3D clay icon in pricing, with stroke weights and corner radii colliding.
Why: nobody made a design pass, and readers feel the inconsistency before they can name it.
Fix: audit every icon on the page into one set, one stroke weight, and one size scale, replacing stragglers one for one, footer social icons included.

**148. Sparkles ✨ on the AI feature** (strong)
Tell: a four-point sparkle glyph on every AI-related button and badge, often gradient-filled, sometimes drawn three different ways in one product.
Why: NN/g tested the sparkle and found 0% of users connected it to AI unprompted, so readers take the industry default as a sign that someone bolted the feature on late.
Fix: label the feature by its function in plain text ("Summarize", "Draft reply"). Use at most one sparkle, and put a text label beside it every time.

**149. Gradient-filled icons** (mild)
Tell: icon strokes and fills carrying a purple-to-blue linear gradient while the surrounding text stays flat.
Why: template kits ship this affectation, and it lands in the same family as the default AI gradient.
Fix: set icons to `currentColor` so they inherit text color, and save any gradient for a single hero element.

## Logo & favicon

**150. Wordmark-is-just-Inter logo** (strong)
Tell: the "logo" is the company name typed in Inter or Poppins Bold, sometimes as gradient text, indistinguishable from the nav links beside it.
Why: nobody did the identity work, and every scaffold emits the same name-in-a-font.
Fix: draw a real wordmark: a typeface used nowhere else on the site, spacing and letterform adjustments of your own, delivered as SVG with dark and light variants.

**151. Letter-in-gradient-rounded-square logo/favicon** (instant)
Tell: a single initial centered in a purple-blue gradient rounded square, doing duty as logo mark, favicon, and OG image.
Why: every AI builder auto-generates this placeholder, which carries about as much identity as the file name "Untitled Project."
Fix: draw a mark, even a geometric monogram with one distinctive cut or counter, in flat brand color; export an SVG favicon and a 180px apple-touch-icon.

**152. AI-generated logo mark** (strong)
Tell: an over-symmetrical abstract mark with artifacts on the curves, inconsistent corner radii, and warped letterforms, or a category symbol anyone could claim (leaf=wellness, shield=security).
Why: generators remix the same industry clichés, the results collapse at small sizes, and customers file the company as amateur.
Fix: redraw the mark as clean vectors and put it through three tests: it holds at 16px, it works in one color, and you can say why the shape belongs to this brand.

**153. Raster-only logo with fringe** (mild)
Tell: the logo is a PNG or JPG with white halo pixels on dark backgrounds, soft at retina sizes, with no one-color or reversed variant anywhere.
Why: generated logos arrive as one glossy image because nobody thought about production.
Fix: rebuild the mark as SVG on a transparent background, add one-color and reversed variants, and swap every instance sitewide.

## VOCAB: greppable signals for this file

- Stock/illustration: `images.unsplash.com` `source.unsplash.com` `pexels.com` `undraw` `#6C63FF` `humaaans` `openpeeps` `open-doodles` `storyset` `freepik` `flaticon` `icons8` `placehold` `placekitten` `picsum.photos`
- Fake avatars: `i.pravatar.cc` `randomuser.me` `thispersondoesnotexist` `ui-avatars.com` `uifaces` `dicebear` `boringavatars`
- Icons: `lucide-react` `Sparkles` `Zap` `Shield` `BarChart` `heroicons` `react-icons` `@fortawesome` `phosphor-react`
- Visual checks: zoom generated images to 200% (hands, text, props, background) · reverse-image-search hero photos and testimonial avatars · count distinct icon styles on the page (>1 = tell) · check logo at 16px and in one color

Sources: tech.co "Ways to detect AI images" · lifehackedai.com "Why AI images look fake" · en.wikipedia.org "Corporate Memphis" · pixels.market unDraw review · rubberduckers.co.uk on generic stock · nngroup.com "AI sparkles icon problem" · manishtamang.com "Icons for vibecoded sites" · unbounce.com on testimonial trust · lefthd.com "How to spot an AI-generated logo" · growthguys.tech · screenhance.com · isthatvibecoded.com · 925studios.co
