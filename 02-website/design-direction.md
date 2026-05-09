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
