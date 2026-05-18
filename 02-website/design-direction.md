# Design Direction

## Design Intent

The website should feel like a focused software engineering company with a serious product portfolio. It should be calm, structured, and business facing.

## Visual Direction

- Clean typography.
- Strong spacing.
- Clear section hierarchy.
- Restrained color palette.
- Product screenshots or product interface previews where available.
- Minimal decoration.
- No exaggerated AI visuals.

## Interface Feel

The site should feel polished and practical. It should present information clearly, with enough product detail to build trust without becoming dense or technical for its own sake.

## Content Layout

Use full width sections with constrained content. Avoid overusing cards. Cards are useful for product summaries, services, and solution example listings.

## Recommended First Build

Astro is a good fit for the first marketing site because it supports fast static pages, clean content structure, and Markdown friendly workflows.

## Product Presentation

Products should have formal pages with:

- Product purpose.
- Workflow supported.
- Core capabilities.
- What it demonstrates about Jera Technologies.
- Clear truth boundaries.

## Avoid

- Flashy AI graphics.
- Generic startup hype.
- Personal portfolio framing.
- Casual project gallery language.
- Claims that imply client work without proof.

## Current Visual System

The site implements the Luminous Technical visual system:

- Warm off white and pale blue white page background.
- Deep navy and charcoal product panels.
- Soft blue and cyan accents.
- Glass style cards where appropriate.
- Rounded containers and strong whitespace.
- Crisp typography using system fonts.
- Subtle hover lift and button transitions.

The site intentionally avoids a plain light theme and a full dark theme. Dark technical panels are used for product and CTA emphasis.

## Slice 2 Refinements

The polish slice refined Luminous Technical rather than replacing it.

Typography decisions:

- Use a cleaner system font stack with Apple like system fonts first.
- Reduce over heavy heading weights.
- Keep letter spacing at 0.
- Tighten heading line height without making text cramped.
- Constrain heading measure so large titles wrap intentionally.
- Add paragraph measure helpers for readable line length.

Layout decisions:

- Reduce broad section padding into a more consistent rhythm.
- Increase card padding slightly and improve card hierarchy.
- Use balanced headings for page sections and technical panels.
- Improve hero text width so the headline wraps more deliberately.
- Structure the footer into brand, company, work, and contact groups.

Gradient decisions:

- Anchor page glows to top left, top right, and bottom right.
- Anchor technical panel glow to corners instead of centering it.
- Keep cyan and blue accents restrained.

## Launch Readiness Refinements

Browser QA reinforced these design decisions:

- The homepage hero headline should be concise enough to wrap deliberately.
- The supporting hero paragraph carries the fuller positioning sentence.
- The header should prioritize clean alignment over showing every call to action at every breakpoint.
- Tablet navigation should avoid crowding the brand block.
- Mobile navigation should wrap cleanly instead of creating horizontal page overflow.
- Mobile action buttons should use the available width for stable tap targets.
- Footer groups remain brand, company, work, and contact.

The visual direction remains Luminous Technical. No full dark theme, plain light theme, or generic SaaS template direction was introduced.

## Mobile Header And Footer Refinement

The launch cleanup slice made the responsive header more deliberate:

- The logo mark is fixed width and does not shrink.
- The brand remains readable at mobile widths.
- The large `Discuss a project` header button is hidden below wide desktop through an explicit CSS rule.
- Mobile navigation chips wrap cleanly.
- The Contact chip is visually emphasized so contact remains easy to find without adding a JavaScript menu.

Footer refinement:

- Footer nav groups remain stacked and readable on mobile.
- The contact email can wrap on narrow screens instead of running off the viewport.
- Bottom footer text uses max widths so it wraps cleanly.

## Responsive Systems QA Refinement

The responsive QA slice kept the Luminous Technical direction intact while tightening the system behavior:

- Active navigation is now route driven instead of relying on browser focus or clicked state.
- Active nav styling uses a subtle blue border, soft blue background, and stronger text.
- Hover styling remains a lighter surface and border lift.
- Focus visible styling remains a temporary outline for keyboard users.
- Mobile section headings use restrained clamp values and improved line height.
- Solution example headings use a smaller mobile scale so long headlines wrap deliberately.
- Mobile cards use slightly tighter padding to reduce excess height.
- CTA panels use smaller mobile padding and text scale.
- Section spacing is slightly tighter on mobile while preserving desktop whitespace.

Current QA notes:

- The in app browser confirmed the Solution Examples page no longer stacks the headline as aggressively on mobile.
- Mobile navigation chips wrap cleanly and do not create horizontal scrolling.
- Footer groups remain readable on mobile, and the contact email remains clickable.

## Page Hero Typography Refinement

The page hero typography slice addressed an issue where shared section heading styles were too narrow for page level introductions. The Services heading in particular was stacking into too many short desktop lines.

Typography decisions:

- Add a dedicated `page-heading` class for page hero titles.
- Add a dedicated `page-copy` class for page hero descriptions.
- Keep `section-title` for standard section intros.
- Widen desktop page heading measure so page heroes usually resolve into two or three strong lines.
- Use `text-wrap: balance` on large headings where supported.
- Reduce mobile page heading scale so long titles remain readable.
- Keep letter spacing at 0 and maintain the current system font stack.

Layout decisions:

- `SectionShell` now supports page heading variants without changing normal section rhythm.
- Page hero headings render as `h1` when used for route intros.
- Mobile navigation now uses a simple two column chip grid below narrow widths, then returns to wrapped chips at larger mobile and tablet widths.
- Shared shell widths use viewport based constraints to avoid inheriting accidental horizontal overflow.

Reviewed routes:

- Home.
- Services.
- Products.
- Structured Analysis Pipeline.
- Matchup Analyzer.
- Solution Examples.
- About.
- Contact.

## Typography Scale And Mobile Nav Refinement

The typography scale refinement slice moved the site closer to a calm native system UI feel.

Font stack decision:

- Use `ui-sans-serif`, `system-ui`, `-apple-system`, `BlinkMacSystemFont`, `SF Pro Display`, `SF Pro Text`, and `Segoe UI`.
- Do not import, download, bundle, or reference external font files.
- Keep letter spacing at 0.

Heading decisions:

- Reduce homepage hero scale.
- Reduce page hero scale across desktop and mobile.
- Reduce panel and section heading scale.
- Use `font-weight: 700` for primary design system headings instead of heavier custom weights.
- Keep `text-wrap: balance` on hero, page, section, panel, and card headings.
- Remove terminal periods from major public headings where they read as title statements.

Mobile nav decisions:

- Keep the logo and brand stable.
- Keep the large `Discuss a project` CTA hidden below wide desktop.
- Use a two column chip grid at narrow widths.
- Let Contact span the full mobile grid width.
- Preserve route driven active state, hover state, and focus visible state.

## Mature Product Surface Refinement

The mature product surface pass keeps the Luminous Technical system but makes it quieter and more product oriented.

Color decisions:

- Reduce bright cyan and electric blue as general purpose accents.
- Use deep navy, charcoal, slate, muted blue, and soft gray blue as the dominant palette.
- Reserve brighter blue for active navigation, focus states, small signal dots, and restrained highlights.
- Treat labels as quiet interface metadata instead of loud promotional text.

Typography and hero decisions:

- Keep the native system UI font stack.
- Keep headings balanced and editorial, with less oversized stacking.
- Preserve sentence style headings without terminal periods where they function as titles.
- Avoid turning page heroes into narrow text towers on desktop.

Product surface decisions:

- Product cards should feel like designed product surfaces.
- Each product card should use a muted category label, clear title, short description, concise capability points, and a consistent CTA.
- Dark product panels should feel integrated with the broader site rather than like a separate visual mode.
- Gradients and glows should stay corner anchored and restrained.

Interactive island decision:

- No island was added in this pass.
- Astro should remain mostly static unless interaction clearly improves visitor understanding.
- A future Capability Explorer can be revisited after preview feedback.

## Mature Rhythm And Copy Specificity Refinement

The pre preview polish pass adjusted the homepage hero and card rhythm without changing the Luminous Technical system.

Hero decisions:

- Reduce the homepage H1 slightly so it feels premium rather than oversized.
- Widen the hero H1 measure enough to avoid aggressive stacking.
- Keep `text-wrap: balance` for intentional line breaks.
- Give the hero visual card more horizontal room on desktop.
- Keep the artifact label as `Structured Delivery System`.
- Separate the hero artifact status pill from the heading so the heading no longer competes for width.

Card and tile decisions:

- Replace repeated generic descriptions with specific descriptions tied to each pattern or outcome.
- Use service outcome cards to explain what each outcome means in practical software terms.
- Keep cards calm, specific, and readable rather than dense.
- Preserve muted labels, soft borders, quiet shadows, and restrained blue accents.

Interactive island decision:

- No island was added.
- Larger interactive components remain deferred until after Vercel preview and launch readiness checks.

## Vercel Preview Readiness QA

The launch readiness pass did not change the visual direction, but it did identify and fix a mobile hero rhythm issue.

Responsive decision:

- The homepage hero grid now declares one mobile column before switching to the desktop split layout.
- The hero text column and artifact column use `min-w-0` so long text and the dark artifact surface cannot force horizontal overflow.
- The hero artifact keeps the preferred `Structured Delivery System` label.
- Mobile header, active navigation, footer wrapping, and contact email behavior remain unchanged.

Launch design status:

- Luminous Technical remains the approved visual system.
- No new interactive island was added.
- No backend contact form was added.
- Remaining visual review should happen against a Vercel preview URL across mobile, tablet, laptop, and desktop widths.

## Appearance Rhythm Refinement

The pre preview appearance pass tightened the Luminous Technical system without changing the approved direction.

Spacing decisions:

- Use explicit `SectionShell` spacing variants instead of one large global section padding.
- Keep page introductions premium, but start route content sooner.
- Use tight follow-on spacing between related sections.
- Connect overview cards to the detail panels they introduce.
- Reduce CTA and footer vertical padding so they feel intentional rather than oversized.

Services page decisions:

- Keep overview cards and service detail panels in one section.
- Center the final two service overview cards on desktop so the second row does not leave an awkward empty third column.
- Use a measured overview-to-detail transition: roughly 32px on mobile, 36px at 768px, and 40px on desktop.

Card and panel decisions:

- Slightly reduce card padding and internal list spacing.
- Keep body copy readable and avoid cramped mobile surfaces.
- Reduce heavy shadow intensity.
- Lower the visual volume of labels by using slate metadata treatments.
- Reserve brighter blue for active navigation, focus states, tiny signal dots, and rare highlights.

Responsive QA notes:

- Checked 360, 390, 430, 768, 1024, 1280, and 1440 widths.
- Checked Home, Services, Products, Structured Analysis Pipeline, Matchup Analyzer, Solution Examples, About, and Contact.
- No horizontal scrolling was detected.
- Header and active navigation remained stable.
- Footer wrapping and contact email behavior remained clean.

Launch design status:

- The site now feels tighter, more editorial, and more product quality.
- No new interactive island was added.
- No backend contact form was added.
- The site is visually ready for Vercel preview smoke testing.

## Component Responsive Surface Refinement

The component display polish pass keeps Luminous Technical but improves the actual display system used by cards, labels, hero copy, and page introductions.

Label decisions:

- Use a shared `surface-label` pattern for product cards, feature cards, metrics, dark artifact panels, and CTA metadata where appropriate.
- Keep the tiny signal dot inline inside the label treatment.
- Do not place decorative dots at the far right of cards.
- Keep label color muted: slate, blue gray, deep navy, soft off white, and subtle borders.
- Reserve bright blue for active navigation, focus states, and tiny signal dots.

Text measure decisions:

- Page headings use a wider page-level measure than standard section headings.
- Hero and page intro copy use broader desktop measures so important positioning copy does not wrap too early.
- Section intro copy supports a wider desktop line length for broad introductions.
- Card body copy remains narrower for scanning and readability.
- Headings use `text-wrap: balance`; paragraphs use `text-wrap: pretty` where supported.

Surface decisions:

- Add a reusable `pearl-surface` utility for selected cards and panels.
- Keep the pearl effect static and subtle, using warm off white, pale blue white, silver, and very low opacity aqua or lavender corner light.
- Avoid neon gradients, rainbow shimmer, heavy glassmorphism, and busy backgrounds behind text.
- Preserve strong text contrast on all pearl surfaces.

Responsive component decisions:

- Product, service, and feature cards can use container query behavior so labels, heading scale, and copy measure adapt to the card's available width.
- Keep this system simple and component local. Do not add JavaScript or interactive islands for this pass.

Responsive QA notes:

- Checked 360, 390, 430, 768, 1024, 1280, and 1440 widths.
- Checked Home, Services, Products, Structured Analysis Pipeline, Matchup Analyzer, Solution Examples, About, and Contact.
- No horizontal scrolling was detected.
- Active navigation, footer wrapping, and contact email wrapping remained stable.
- Product card labels no longer show loose dots at card edges.

Launch design status:

- The site is visually ready for Vercel preview smoke testing after this pass.
- Capability Explorer and other interactive ideas remain deferred until after preview feedback.

## May 12 UI/UX Polish Direction

The latest polish pass keeps the Luminous Technical direction but makes the public site feel more mature, crafted, and welcoming.

Typography direction:

- Use separate measures for page headings, page intros, section headings, section intros, panel copy, and card copy.
- Do not force broad desktop headings into narrow text towers.
- Keep `text-wrap: balance` for major headings and `text-wrap: pretty` for paragraphs where supported.
- Let cards keep tighter copy measures while page and section introductions use wider desktop lines.
- Avoid oversized headings that stack aggressively.

Surface direction:

- Use pearl and iridescent effects as a quiet surface refinement, not a visual theme.
- Prefer warm off white, pale blue white, soft silver, muted blue gray, and very low opacity aqua or lavender.
- Apply `pearl-panel`, `iridescent-edge`, and `soft-surface-glow` sparingly to product cards, solution/service detail panels, CTA panels, selected dark product panels, and the inquiry modal.
- Use `soft-surface` for ordinary cards so the pearl effect does not appear everywhere.
- Continue reserving bright blue for active navigation, focus states, tiny signal dots, and rare highlights.

Inquiry direction:

- The inquiry experience should feel easy, polished, and honest.
- The current implementation is a lightweight modal with one project category dropdown, name, email, company, and message fields.
- The form opens a prepared mailto draft and does not claim backend submission.
- A backend form can be revisited after preview if mailto becomes insufficient.

Tone direction:

- About should be company-first, not a personal portfolio lead.
- Broad service positioning stays client flexible.
- Enterprise Modernization should emphasize stronger architecture, cleaner patterns, integration flows, authentication and access patterns, workflow modernization, business logic preservation, and maintainable application structures without naming narrow stacks.

## May 14 Public Copy And Inquiry Refinement

This pass keeps the Luminous Technical direction intact while making the public copy more natural and visitor-facing.

Header decision:

- The small brand subtitle now reads `Practical AI & Software Engineering`.
- The subtitle is allowed to wrap under the brand on mobile with a restrained measure instead of disappearing or forcing header overflow.

About decision:

- Remove internal positioning language from the public About page.
- Keep `Calm engineering for complex systems` as the operating principles heading.
- Describe the principles in useful public language: practical AI tied to real workflows, enterprise judgment around existing systems, and product minded delivery that stays close to users.

Inquiry decision:

- Simplify the modal so visitors see one category decision, then direct contact fields.
- Use the title `Tell us what you are trying to build`.
- Use the intro `Share a few details about the workflow, system, or product idea. Jera Technologies will follow up with a practical next step.`
- Use the primary CTA `Send inquiry`.
- Preserve the mailto draft behavior and fallback email link.

Responsive direction:

- Prefer text measures, balanced headings, and comfortable field spacing over manual line breaks.
- Keep the modal full width only where mobile needs stable tap targets.
- Preserve the pearl panel, muted borders, navy anchors, soft blue focus states, and generous whitespace.

## May 14 Responsive UI Refinement Direction

This addendum keeps the Luminous Technical system but makes the layout more container aware and less brittle.

Responsive typography decisions:

- Widen narrow mobile heading measures slightly so long public headings wrap in fewer awkward fragments.
- Keep page titles strong, but avoid oversized mobile type and forced manual line breaks.
- Preserve separate measures for page headings, section headings, intro copy, panel summaries, and card copy.

Layout decisions:

- Keep the header polished at tablet widths by reducing desktop nav chip density before the wide desktop CTA appears.
- Use shared detail panel classes for Services and Solution Examples so summary copy and outcome cards can adapt to available width.
- Let service outcome cards use two columns on small tablet widths and three columns on desktop.
- Let solution pattern cards use two columns from small tablet upward.
- Avoid disconnected vertical gaps by keeping overview and detail content in connected sections.

Inquiry modal decisions:

- Treat the modal as a small product surface with clear title, concise intro, comfortable labels, strong focus states, and visible close behavior.
- Use a wider desktop panel and tighter vertical rhythm so the primary CTA and fallback email remain visible at normal laptop heights.
- Use `100dvh` based max height so mobile browser chrome does not make the modal feel cramped.
- Keep the pearl surface restrained and readable with navy actions and soft blue focus states.

Accessibility and interaction decisions:

- Preserve route driven active navigation, `aria-current`, dialog labelling, Escape close, click outside close, and focus return.
- Use event delegation for inquiry triggers so future CTAs inherit the behavior without adding more JavaScript.
- Keep native form validation in place before opening the mailto draft.

## May 15 Inquiry Modal Polish Direction

This focused pass keeps the inquiry modal static, lightweight, and Astro friendly while making the form feel more product quality before Vercel preview.

Visual decisions:

- Remove the modal-specific right edge artifact by softening the iridescent overlay on the modal panel and avoiding an always reserved scrollbar gutter.
- Keep the pearl panel treatment calm, low contrast, and readable.
- Use the final headline `Rough idea, stubborn workflow, or modernization effort?` with balanced wrapping and a measured headline width.
- Use the intro `Send over the shape of it, even if it is still messy. Jera Technologies will help turn it into a practical next step.` with prettier wrapping where supported.
- Treat the footer as an intentional form action area with a subtle divider, primary CTA on the left at desktop widths, direct email helper on the right, and a clean stacked mobile layout.
- Keep the CTA and fallback email visible at 390px by 900px.

Select decision:

- Keep the native select for accessibility, keyboard support, form validity, and low implementation risk.
- Polish the closed select state with a calm border, consistent radius, soft focus ring, and aligned chevron.
- Do not build a fake custom dropdown for launch. The open option list is browser and OS controlled and cannot be made fully consistent across browsers with lightweight CSS alone.

Final inquiry categories:

- Applied AI.
- Enterprise Modernization.
- Workflow Automation.
- Architecture & Integration.
- Decision Support Systems.
- Product Strategy.
- Not Sure Yet.

Final fallback copy:

- `Prefer a direct email?`
- `Send a short note to:`
- `support@jeratechnologies.com`

Remaining Vercel preview QA:

- Recheck the modal on the deployed preview at mobile, tablet, and desktop widths.
- Confirm mailto behavior from the live preview.
- Confirm the native select popup is acceptable in the target browsers.
- Recheck contact links, metadata, sitemap, redirects, and console output on the preview URL.

## May 15 Premium Design Architecture Direction

This pass formalized the Luminous Technical refinements that take the site from polished to top-dollar independent software studio. The system was strengthened without redesigning the underlying direction.

Token decisions:

- CSS tokens are grouped into base canvas, text, brand anchors, pearl detail, hairlines and borders, elevation, radii, layout, and focus ring.
- Three step elevation scale: `--shadow-soft` for resting cards, `--shadow-card` for surfaces that earn slight emphasis, and `--shadow-lift` for hover.
- A dedicated `--shadow-dark` for technical panels with a soft top highlight and a deeper outer shadow.
- Added `--color-border-soft` and `--color-border-strong` so hairlines and dividers can vary without ad hoc rgba values.
- `--ring-color` is the single source of truth for focus visible outlines.

Typography decisions:

- Body text uses `font-feature-settings: "ss01", "cv11", "kern"` and `font-optical-sizing: auto` so supported platforms get slightly tighter, more refined glyphs without bundling a typeface.
- Display headings use slight negative letter spacing: page (-0.016em), section (-0.012em), panel (-0.014em), card (-0.008em), homepage H1 (-0.02em).
- Uppercase metadata uses 0.04em on eyebrow and 0.06em on surface labels so small labels feel deliberate, not crowded.
- A `.tabular-nums` utility lines up step counters, metric values, and capability indices.
- `text-wrap: balance` remains the default for headings and important short labels. `text-wrap: pretty` is used for paragraphs.

Surface decisions:

- Iridescent edge treatment softens its right and bottom border opacities so the right edge cannot read as a duplicated line.
- The inquiry modal panel explicitly disables `iridescent-edge::after` so it cannot show a double line near the scrollbar gutter at any size.
- Pearl surfaces continue to lean on warm off white, pale blue white, soft silver, and very low opacity aqua or lavender corner light.
- Technical panels gained a quiet lavender corner glow so dark surfaces feel a touch more iridescent without becoming flashy.
- `subtle-lift` uses a cubic bezier ease and the `--shadow-lift` token plus a soft blue border on hover.

Button decisions:

- Primary uses a deeper vertical gradient with inset highlight and layered shadow.
- Secondary layers an inset highlight on a soft hairline border on a small drop shadow so it reads as a real product surface in light mode.
- Dark uses an inset highlight on a darker outer shadow so it sits naturally on technical panels.
- All buttons use a small `:active` settle plus a 200ms cubic bezier on `:hover`.

Header decisions:

- Brand mark uses a subtle radial inner highlight on the deep navy ground.
- Subtitle uses a slightly larger mobile measure so `Practical AI & Software Engineering` resolves into a deliberate two line wrap on narrow screens.
- Active nav uses a slightly stronger blue accent border plus a calm translucent fill.

Hero decisions:

- Three corner glows anchor the first viewport without busy decoration.
- A focus, approach, output tabular trust strip sits below the hero CTAs to give the first viewport quiet structural backbone.
- Hero artifact tiles use an inset bordered step counter with tabular numerals and a calmer artifact title.

Card decisions:

- Feature, Service, and Process cards carry a top inline hairline that anchors the card visually without adding a heavy border.
- Process step pairs the step counter with a fading hairline lead in.
- Product card removes loose decorative dots and keeps the metadata bar inside the shared label treatment.
- Metric card scales its value type smaller and uses balanced wrapping so words and short phrases both fit.
- Dark product panel uses `01 / 02 / 03 - Capability` lead ins on its capability tiles so the dark grid reads as designed rather than uniform pill text.

Inquiry modal decisions:

- Final copy: eyebrow `Project Inquiry`, headline `Rough idea, stubborn workflow, or modernization effort?`, intro `Send over the shape of it, even if it is still messy. Jera Technologies will help turn it into a practical next step.`, message label `What needs attention?`, fallback heading `Prefer a direct email?`, fallback helper `Send a short note to:`, fallback email `support@jeratechnologies.com`.
- The right edge artifact is removed by opting the modal panel out of `iridescent-edge::after`.
- The modal close uses an SVG cross icon, the submit uses an SVG check icon, and a soft 240ms rise animation is used on open (suppressed under `prefers-reduced-motion`).
- Native select stays. No custom dropdown was added.

Accessibility decisions:

- Focus visible uses a single token color and a consistent 2px ring with 3px offset.
- Reduced motion suppresses all transitions and animations including the modal entrance.
- Modal preserves dialog semantics, Escape close, outside click close, focus return, focus trap, labelled and described relationships, and visible field focus.
- Touch targets remain above 40px on mobile for nav chips, buttons, and the modal close.

Astro and performance decisions:

- No framework island, animation library, or runtime dependency was added.
- Static output remains the default.
- Shared utilities (`pearl-panel`, `iridescent-edge`, `soft-surface`, `surface-label`, `subtle-lift`, `tabular-nums`, `hairline`) carry the polish across components instead of scattered one-off styling.

Public copy direction (refresh):

- Homepage product portfolio eyebrow now reads `Product lab`, matching the brand direction of describing surfaced work as Jera built products and product lab work.
- About uses `Focus / Applied AI` and `Method / Structured` metric values instead of the earlier `Focus / AI` and `Approach / Build`.
- Public source and generated HTML continue to avoid `public positioning`, `recruiters`, `future consulting prospects`, `built to feel credible`, `broad enough`, `AI Application Engineering`, `Applied AI Engineering`, `jerattechnologies.com`, `client's system`, `internal workflow`, and `fake agency` style language.

## May 15 Text Composition Direction

This focused pass corrected an underlying composition issue: intro paragraphs and detail panel descriptions were running at 62 to 64rem, which renders as roughly 80 to 95 characters per line and breaks the calm, intentional reading rhythm the site aims for.

Measure system direction:

- Measures are now expressed in `ch` so the constraint scales with the rendered font size, not absolute pixels.
- The measures live on `:root` as named tokens and are applied through both refactored existing utilities and a new `.measure-*` utility family.
- All measure utilities use `max-inline-size` (logical) rather than `max-width`, with `hyphens: none` and `overflow-wrap: break-word` where appropriate so words do not hyphenate and the only word splits happen as a last resort.

Approved measure ranges:

- Hero subtitle and lead copy: 50ch.
- Page hero intro and section intro: 56ch.
- General body copy: 60ch.
- Dark panel copy (technical panel and CTA panel): 52ch.
- Card body copy (services, features, products): 38ch.
- Helper text (modal fallback, small notes): 34ch.
- Footer brand copy and tagline: 38ch.
- Footer legal line: 44ch.
- Page heading: 24ch.
- Section heading: 24ch.
- Panel heading (when explicitly constrained): 28ch.
- Card heading: 22ch (applied explicitly when needed; defaults to container width).
- Display lead in a hero artifact: 22ch with `ch` units replacing `rem` for the hero artifact title.

Wrapping direction:

- Headings use `text-wrap: balance` and a small negative letter spacing.
- Paragraphs use `text-wrap: pretty` so the last line is not a single orphan word.
- `text-wrap: balance` is preserved on the modal title and other prominent statements.

Footer composition direction:

- Brand descriptive paragraph uses the 38ch footer measure.
- Bottom row copyright uses the 44ch legal measure.
- Bottom row tagline uses the 38ch tagline measure.
- The contact email retains break-all on mobile and whitespace-nowrap from large desktop up so it never overflows on narrow widths.

Inquiry modal composition direction:

- Modal title: 26ch, balanced wrap.
- Modal intro: 50ch, pretty wrap.
- Fallback helper: 34ch.
- All copy, dialog semantics, focus handling, and mailto behavior remain unchanged.

Page level composition direction:

- Services and Solution Examples detail panel headings use the new 24ch section heading measure with balanced wrap.
- About, Contact, Structured Analysis Pipeline, and Matchup Analyzer dark intro panels use the new 28ch panel heading measure with balanced wrap.
- The CTA section heading uses the 28ch panel heading measure rather than the previous `max-w-3xl` (48rem) so the heading wraps into a deliberate 2 line composition.

Astro and component direction:

- Measure utilities are centralized in `src/styles/global.css`. Pages avoid ad hoc inline `max-w-[...]` measure hacks.
- Where a page-specific heading needs a custom font size, it still applies a shared `.measure-*` utility for the width constraint.

## May 15 Section Intro Measure And Rhythm Refinement

The earlier text composition pass tuned the intros too tight. This refinement widens intro measures so a typical section intro reads as one to three calm lines on desktop, and adds a small breathing gap between section header blocks and the content that follows.

Updated measure targets:

- Hero lead copy: 58ch (about 580px at the hero body font).
- Section intro: 76ch (about 700px to 720px at the section intro body font).
- Page hero intro: 72ch (about 700px to 730px at the slightly larger page intro font).
- Long form body copy: 64ch.
- Dark panel copy (technical / CTA): 58ch.
- Card body copy: 42ch (container almost always wins, so this just stops capping the slightly wider card variants).
- Footer brand copy: 40ch.
- Footer tagline: 40ch.
- Footer legal line: 44ch.
- Helper text: 34ch.

Updated header-to-content spacing:

- Standard `section-shell__header`: `clamp(2.25rem, 3.6vw, 3.15rem)` margin-bottom (about 36px to 50px).
- Page `section-shell__header--page`: `clamp(2.55rem, 4.2vw, 3.55rem)` (about 41px to 57px) so the page hero introduction lands with deliberate space before the first card grid.
- Compact `section-shell__header--compact`: `clamp(1.9rem, 2.8vw, 2.5rem)` (about 30px to 40px).

Wrapping direction stays unchanged: headings use `text-wrap: balance`, paragraphs use `text-wrap: pretty`, copy uses `hyphens: none`, and the wider intro measure lets pretty wrap settle into one to three lines rather than four to six short fragments.

Mobile behavior is unchanged. Mobile section intros remain bounded by the site shell container, not by the ch token, so the calm vertical reading rhythm at narrow widths is preserved.

## May 15 Section Rhythm And Footer Composition Direction

This refinement formalized the section header rhythm and simplified the footer composition.

Section header rhythm direction:

- Each section header is one composed block: eyebrow, then heading, then intro paragraph. The inner stack uses 1.25rem of vertical rhythm so the three elements read together rather than as separate paragraphs.
- A consistent block-end margin separates the header from cards, panels, grids, or CTA content. Targets land in the brief range: 24 to 32px on mobile, 28 to 40px on tablet, 32 to 48px on desktop. Page hero headers run slightly taller, compact section headers run tighter.
- The header is now a flex column with logical spacing so the rhythm survives even if a consumer drops the inline margin utility.
- A latent bug in SectionShell was using class={...} with an array, which Astro joined with commas. Switching to class:list ensured the rhythm variants actually applied for the first time.

Solution Examples intro direction:

- Both the homepage section and the dedicated Solution Examples page now share the intro: Reusable patterns for structured workflows and clearer implementation. The shared statement reduces dissonance and lands as one calm line on desktop.

Footer composition direction:

- The footer carries one brand statement, not two. The bottom row tagline was removed so the brand blurb and the copyright row are the only text blocks in the footer.
- Brand blurb: Practical AI and software engineering for clearer workflows.
- Bottom row: only the copyright line. At desktop the row hosts the copyright on the left and nothing on the right, which lets the footer close with a quiet beat instead of two competing prose statements.

## May 15 Mobile Nav Primary Action Direction

The mobile nav Contact item is now treated as the primary mobile action, not just another chip.

Visual direction:

- Below the sm breakpoint (640px), Contact uses a filled deep navy pill with white text, inset highlight, and a calm layered shadow. This makes the full row span obvious and gives mobile visitors a clear, premium primary action.
- At sm and above, Contact returns to the same light chip styling as the other nav items so the flex-wrap tablet nav and the desktop horizontal nav stay calm and balanced.
- When the visitor is on /contact, the active state wins on every breakpoint. The pill renders in the soft blue active style and still spans the full row on mobile.

Implementation direction:

- The mobile-nav-shell grid uses default justify-items (stretch) so col-span items naturally fill their cell.
- Mobile nav links use inline-flex items-center justify-center so labels render centered inside the full width pill.
- The Contact link carries a .mobile-nav-contact class. A dedicated CSS rule below 639px sets grid-column: 1 / -1 and justify-self: stretch so the geometry is robust regardless of Tailwind utility ordering.

## May 15 Mobile Contact Centering Direction (revision)

The earlier direction treated mobile Contact as a filled primary action. After visual review that treatment felt out of step with the rest of the calm chip nav. The revised direction:

- Mobile Contact uses the same chip styling as the other mobile nav items (Services, Products, Solution Examples, About).
- Mobile Contact spans both columns of the third row but is rendered at single-column width via width: calc(50% - 0.25rem), then centered with justify-self: center, so the third row is balanced and the empty cell never reads as awkward space.
- Hover, focus visible, and current page states match the rest of the mobile nav. On /contact the chip shows the same soft blue active treatment as any other route highlight.

Footer composition direction (revision):

- The footer grid widens its left column at lg and above so the brand blurb has enough room to land on one line.
- --measure-footer was widened from 40ch to 64ch so short brand statements can sit on one line on desktop. Mobile still wraps naturally because the container is narrower than the measure.
- The bottom row keeps only the copyright line. The brand blurb above carries the single brand impression.

## May 17 Reusable UI/UX Skill

The senior UI/UX judgment used across the recent Jera refinement passes is now captured in a reusable Claude Code skill at .claude/skills/product-ui-design-architect.

Doctrine:

- The skill provides reusable frontend design judgment (design posture, text rhythm, section spacing, modal and form quality, mobile navigation, footer composition, accessibility, launch readiness).
- The jera-vault provides Jera specific truth (brand direction, copy rules, repo boundaries, decision history, launch goals).
- When the skill and the vault disagree, the vault wins.

Working method for future Jera UI passes:

- Invoke the official frontend-design skill for broad visual and creative direction.
- Invoke product-ui-design-architect for refinement discipline and QA.
- Read only the jera-vault docs the task needs.
- Record meaningful design, copy, UX, or launch readiness changes back into the jera-vault.
- Add a lesson to the skill only when it is reusable across projects. Jera specific lessons stay in the vault.

## May 17 Design Source Research Workflow

The product-ui-design-architect skill now includes a responsible design
source research workflow that can feed future Jera design passes.

How it works:

- A miner script collects public GitHub API metadata and a small set of
  config and style files into a generic design source library. It does
  not clone repos, scrape HTML, or download large files.
- A selector script filters that library against Jera's own docs
  (design direction, public copy rules, current slice) plus a use case,
  and writes a Jera specific design source brief.
- The brief is inspiration and pattern research only. It never authorizes
  copying components, layouts, or code. Jera builds original work.

How it influences Jera design direction:

- The selector scores sources against Jera signals: calm, senior,
  premium, light theme, navy, enterprise, modernization, plus the Astro
  and Tailwind stack and the accessibility and static output constraints.
- Sources that lean neon, flashy, or heavily animated are penalized
  because the Jera context asks for calm and restrained motion.
- The brief is a research aid used before a design pass, not a launch
  gate. The Luminous Technical visual system and the jera-vault remain
  the source of truth. A mined source never overrides Jera direction.

## May 17 Service Copy Compression

A project-aware editorial pass compressed verbose service and solution
example descriptions. The Luminous Technical visual system, the section
rhythm, and the measure tokens were unchanged.

Direction confirmed:

- Service and solution example descriptions are short statements, not
  comma-heavy lists. Aim for roughly 9 to 13 words and one clear idea.
- A four item list inside one description should drop to three concrete
  terms or fewer.
- Remove redundant qualifier tails (for example, a trailing "with
  patterns suited to the existing system" after the sentence already
  said "existing applications").
- The service description field feeds three rendered places (overview
  card, detail panel intro, homepage services card). Compress the field
  once at the content source rather than patching each surface.
- Prefer better copy over widening a measure. The measure tokens stayed
  the same; the copy got shorter.

## May 17 About Page Voice

The About page voice was loosened from stiff and corporate toward calm,
human, and lightly witty, without becoming cute or hypey.

Voice direction confirmed for About:

- Headlines may carry a small, dry human note (for example "messy, useful
  work" or "parts of work that refuse to stay simple"). Keep it light and
  never gimmicky.
- MetricCard values may be short phrases rather than single words when
  the phrase reads as a confident statement (for example "AI that earns
  its keep"). The card value keeps text-balance so it composes cleanly.
- Body copy stays practical and concrete: real workflows, not slideware.
- The pass was copy and text rhythm only. Layout and components were not
  changed.

## May 17 Editorial Systems Pass

Recurring verbose-intro wrapping was addressed as a system, not a page.

Direction confirmed:

- Prominent section and page intros carry one idea, avoid comma-heavy
  service lists, and stay short enough to render as one or two calm lines
  on desktop. Cards and panels carry the detail.
- When the same wrapping problem recurs across pages, the fix is the copy
  pattern and the project copy rule, not per-page CSS. The measure tokens
  and section rhythm were not changed in this pass.
- The build copy check now prints an advisory for long or comma-heavy
  intros so the issue is caught at build time rather than discovered
  visually page by page.

## May 17 Inquiry Modal Polish

The inquiry modal was refined as a small product experience: calmer
headline scale, intentional form grouping, a softer footer, and a send
icon that matches the action.

Direction confirmed:

- A modal headline is sized as a modal heading, not a page hero. Keep it
  short and cap the font size below the page hero scale.
- Forms read better as visible groups. Quiet uppercase scanning labels
  (Contact details, Project details) group fields without heavy dividers.
  Each input keeps its own real label; the group labels are aria-hidden
  visual aids.
- Footers and action areas use soft faded hairlines, not hard
  edge-to-edge rules, and use whitespace or a column gap instead of a
  vertical divider line.
- A primary action icon depicts the action. Submit and send use a send
  or paper-plane icon, never a checkmark.

## May 18 Modal Text Composition Direction

The inquiry modal headline and the inquiry modal intro are separate
composition objects and use separate, named text measures. This
supersedes the modal measure note in the May 15 Text Composition
Direction section (which set the modal intro to 50ch).

Direction confirmed:

- The modal headline and the modal intro must never share one measure.
  The headline is a short, strong statement; the intro is a supporting
  paragraph. They have different jobs and different ideal line lengths.
- The headline uses a narrow measure (--measure-modal-heading, 24ch) so
  it reads as a compact modal heading.
- The intro uses a distinctly wider measure (--measure-modal-intro,
  64ch) so a two-sentence intro composes as two calm lines on desktop,
  not a narrow column of cramped fragments. 50ch was too narrow and is
  retired.
- The shared modal header wrapper must not silently cap the intro. Its
  max-width is wide enough (46rem) that each text element is governed by
  its own measure, not by the wrapper.
- The intro keeps text-wrap: balance. At the 64ch measure, balance lands
  the line break after the opening question rather than stranding the
  next sentence's first word on line one.
- Awkward intro wrapping in a modal is treated as a measure problem
  first. Fix the measure before trimming copy. Do not shorten good copy
  to compensate for a bad measure.
