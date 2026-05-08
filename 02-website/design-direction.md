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
