# Art direction: how to reach a direction you can defend

This file covers the process that produces a commitment. `directions.md` holds the specifications you commit to, `derivation.md` holds the math, and `method.md` explains why the removal-only approach fails.

Work through this before you touch a token. The gate at step 8 exists because a direction chosen after the code is written becomes a justification for whatever the code already does.

## 1. The perception brief

Ask stakeholders (or the repo owner, or yourself) perception questions rather than fact questions. Facts describe the product. Perception describes the gap you are closing.

- What should someone believe about this company after ten seconds on the page?
- What makes a company credible in this category?
- If the brand spoke, how would it sound?
- What do customers misunderstand about the category?
- Where does this brand match category expectations, and where does it break them?

Record the answers word for word. You will reuse that wording later, and a stakeholder recognizing their own sentence in your reasoning ends most arguments about taste.

**Solo shortcut.** Working alone on your own project, answer these in writing anyway. The value comes from committing answers to text before you see any pixels.

## 2. Competitor perception map

Collect 8 to 15 competitor homepages. Draw two axes (Traditional/Progressive, Corporate/Human) and place every competitor. Place your current site too.

Where competitors cluster, you have a category default. Your current site probably sits inside that cluster, which is the actual finding.

## 3. Attributes, sourced from reasons

Gather images across unrelated categories: transport, furniture, architecture, an object, a drink, an animal. Pick one per category and write four or five adjectives explaining the pick. Cluster the adjectives, not the images.

Clustering reasons rather than pictures separates the brand from personal taste. Somebody who picks a brass lamp and a concrete building is telling you about weight and permanence, not about lamps.

## 4. Attribute disambiguation

The step that decides whether you diverge or converge. For each attribute, answer two questions: what it means **in this category**, and what it explicitly **does not** mean.

Worked example. "Bold" could mean bright color, oversized type, or an expressive system. In a financial product, bold has to coexist with security and competence, so the real brief becomes: *what kind of boldness still reads as trustworthy?* That qualified question has no default answer, which is why it produces work no competitor is doing.

Categories converge because everyone renders the same adjective with the same default grammar. The qualifier is where the open territory sits.

Output: 3 to 5 attributes, each with an is / is-not pair.

## 5. Element-decomposed competitive audit

Never compare whole brands. Build one board per element with every competitor on it:

- logos
- color palettes
- typography
- graphic devices
- imagery, split into product photography, corporate imagery, illustration, charts

Then chart color frequency across the set. Convergence hides at the whole-brand level and shows up at the element level. The frequency chart turns "everyone uses blue" from an impression into a number, which also makes your color proposal defensible: color arguments are subjective until you present them against the competitive set.

## 6. White-space plot

Choose two axes built from visual attributes rather than brand values: minimal/maximal, heritage/futuristic, artisanal/commercial, serious/playful. Plot every competitor and look for empty quadrants.

Then apply the filter that most teams skip: **discard any empty quadrant your audience would not value.** Empty does not mean ownable. Some quadrants are empty because nobody wants what lives there.

Audit two more dimensions while you are here. How rigorously does each competitor hold its system together, and is each one chasing trends or setting them? A category full of loosely-held systems means consistency alone will differentiate you.

## 7. Anti-mood board

Collect what is wrong. Colors that feel draining, materials that feel synthetic, layouts that read as generic. Annotate each with why it fails against your step-4 attributes.

Rejection is faster and more reliable than aspiration, and an exclusion list can be tested during review in a way that an inspiration board cannot. Add the current category defaults to the list by name:

> gradient mesh hero · Inter or an equivalent neutral sans · three-column feature grid · dark theme with minimalist white text · product UI floating on a soft gradient · abstract letterform logo with a linear gradient · three-word tagline ("Build. Ship. Scale.") · fade-up on scroll with spring easing · cursor-reactive particle field · card tilt on hover

Naming a default makes it refusable. An unprompted "modern SaaS website" resolves to the most statistically common layout in the training data, so the ban list is doing the work the prompt cannot.

## 8. Pre-code gate

Do not open an editor until all eight hold:

1. You can state what the brand should communicate.
2. You have defined brand character.
3. You know what that character means and what it does not.
4. Your references are tied to perception rather than taste.
5. Brand ideas have become visual principles (step 9).
6. You have an early call on type, color, imagery, and graphic language.
7. You have written down where people agree and disagree.
8. You can name which directions would be wrong.

The first concept should not feel like a guess.

## 9. Design code

Translate each verbal idea into visual grammar before designing. Real translations from studio practice:

| Brand idea | Visual device |
|---|---|
| "Personalized support for your unique journey" | organic shapes, handwritten lines, softer compositions |
| "Parenting is messy and magical" | soft gradients, layered imagery, playful irregularity |
| "Research-backed support for real life" | data snapshots, infographics, editorial layouts |
| "Momentum in motion" | lines, arrows, ripple effects, motion blur |
| "Building blocks" | modular shapes, stacked compositions |

This table is the bridge between strategy and pixels. Without it, "trustworthy" never becomes a hex value.

## 10. Five pre-concept commitments

Answer each with a written reason. The reason becomes the justification sentence for that decision later.

1. **Typography:** editorial, technical, warm, precise, expressive, or restrained?
2. **Color:** follow category codes or contrast against them?
3. **Logo:** quiet typographic mark, flexible symbol, or expressive character?
4. **Photography:** documentary, polished, intimate, product-led, everyday, or aspirational?
5. **Illustration:** explain ideas, add warmth, or carry a distinctive language?

## 11. The one decision competitors would never make

After the audit, isolate a single choice your competitive set is structurally unwilling to make, then commit to it everywhere:

- a display face with real character where everyone else runs a neutral sans
- a palette containing no gray at all
- zero rounded corners in a category of soft cards
- body copy set at 22px
- an entire site with no photography

Distinctiveness rides on a small number of high-salience decisions rather than broad tasteful adjustment. A rival can only copy this one by abandoning their own positioning, which is what makes it defensible. Propagating it across every page converts a quirk into an identity.

## 12. Diverge on surface, converge on structure

The rule that keeps divergence from costing conversion.

**Hold at category convention:** navigation clarity, form behavior, responsive grids, information hierarchy, checkout. These are load-bearing, and breaking them costs real money.

**Move all differentiation here:** typography, color, section ordering, storytelling structure, imagery, microcopy, motion.

Reorder sections around how customers actually evaluate rather than the default hero → features → pricing stack. Bend conventions rather than rejecting them. Distinctiveness layers through tone, color, and refinement, not through layout chaos.

## 13. Cross-category reference import

Identify the dominant visual language of your category, then source references from an unrelated category solving a similar perception problem.

Oatly found the gap between health-focused soy-milk imagery and traditional pastoral dairy, then imported a typographic system resembling lifestyle magazines. Dollar Shave Club met Gillette's hyper-masculine technology-led language and imported a conversational style from lifestyle categories.

References from inside your category regress toward the category mean. References from outside arrive with a grammar the category has no defense against, and they stay coherent because they are internally consistent systems in their own right.

## 14. Load-bearing constraints

Impose a constraint tied to something real, then derive the system from it. One typeface. Two colors. No photography. No shadows. Nothing wider than 8 columns.

Constraints and creativity have an inverted-U relationship, so the right amount generates invention. The constraint has to be load-bearing and connected to something true about the product. An arbitrary constraint is a rule dressed up as a design principle, and it demoralizes rather than generates.

For genuinely under-determined choices: pick fast, tie the pick to a real anchor (a design-code line, an exclusion from the anti-mood board, a technical limit), then never revisit it. Commitment is what reads as authored. Revisiting is what produces mush.

## 15. Two or three routes, then cull

Develop each route to a hero, one dense inner page, and one component-heavy state. Kill any route you would be unhappy to build. The filler option exists to flatter the real one, and it gets picked often enough that every experienced designer has a story about it.

Name routes as directions rather than designs. "The Archivist" and "The Challenger" invite strategic comparison; "Option A" invites preference.

## 16. Agree criteria before showing work

When presenting to anyone, state the criteria and get explicit agreement **before** the artifact appears. Then per direction: reasoning first, artifact second, context third.

Agreeing criteria up front converts what would be post-hoc justification into a pre-registered test, and it moves evaluation from "I like it" to "does this express the brand we agreed on?" Route every piece of feedback back through the criteria, and separate must-change from would-prefer. Take the observation seriously even when the proposed fix is wrong, because the underlying observation is usually correct.

Show what you ruled out. It proves the criteria were applied and stops the work drifting back toward the category mean.

## 17. Design principles

Write 3 to 6 principles in "We want X because of Y" form. Each needs a point of view and each must state what you do not do. Keep them practical rather than visionary. Ground each in a real user problem, then check it against a good and a bad example already in the product.

Test: look at any design decision and say whether it adheres. A principle that cannot fail is decoration.

Then embed them. Revisit default settings and templates so the principle becomes the path of least resistance, and use the principles in review to end discussions that are really about taste.

## 18. Propagation

A decision that lives in one component is an accident. A decision applied everywhere is an identity.

**Three-tier tokens.** Primitives (`blue-600`, `space-4`) → semantic (`text-primary`, `surface-raised`) → component (`button-bg-hover`). A token references exactly one tier below. It never skips a tier and never reaches sideways. A component token pointing straight at a primitive has quietly opted out of theming for itself.

**Theme by swapping semantics.** Primitives stay constant while semantic tokens re-point: `text-primary` keeps its name and points at `gray-900` in light, `gray-100` in dark.

**One base unit.** An 8pt linear scale (8/16/24/32/40) with a 4pt half-step. Put type on a 4pt baseline so line-heights stay divisible by 4. Avoid a 4pt primary unit, which creates too many variables to hold consistent.

**Twelve columns,** because they divide into halves, thirds, fourths, and sixths. Take gutters from the same spacing scale so layout and component padding share one rhythm.

**Declare hard against soft grid per component class.** Element-first strict sizing for predictable controls (buttons, inputs, chips). Content-first strict padding where content length is unpredictable. Write the rule down so nobody relitigates it per component.

**Two motion registers.** A productive set for functional feedback (short, ease-out) and an expressive set for brand moments (longer, characterful). Name both as tokens and record which components may use which.

**Fix contrast as a system rule.** Derive contrast from brightness and saturation rather than by adding black, and re-derive the whole palette at once when it fails. Patching contrast per component makes a palette darker and duller over time.

**Lint it.** Run a design linter in CI to flag hard-coded hex values, off-scale spacing (`17px`, `24px` where the scale says 16 or 32), and raw elements used where a system component exists. Emit results as PR comments, start as warnings, escalate to errors. Enforcement is what keeps the direction alive after you stop paying attention.

**Carry the name.** Keep the direction's name attached to the token file, the principles doc, and the review checklist, so later decisions get checked against a named argument rather than an accumulated style.

## Sources

smashingmagazine.com "How to turn brand strategy into visual direction" and "Practical guide to design principles" · desantisbreindel.com on visual brand audits · milkable.com.au on visual competitor audits · onestep4ward.com on the anti-mood board · storyflow.so on presenting design concepts · designsystems.com "Space, grids and layouts" · pixmauxguides.com on token naming · contentful.com on design token systems · thisisalso.com "Every website looks the same" · overpass.studio "Why SaaS websites look the same" · designnotes.blog.gov.uk on the GOV.UK color update · lapidist.net on design linting · everything.design on motion brand guidelines · typetype.org on choosing a brand typeface
