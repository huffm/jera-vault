# 0005 Component Responsive Surface System

## Status

Accepted

## Date

May 12, 2026

## Context

The public site already had a strong Luminous Technical direction, but a few component display details still felt awkward before Vercel preview. Product card metadata dots were visually detached from the labels, broad page intro copy wrapped too early on desktop, and some light cards needed a more refined premium surface without making the site colorful or flashy.

The site also reuses cards in different grid widths. A card used in a two column desktop grid and the same card used in a narrower mobile stack should not depend only on viewport breakpoints.

## Decision

Use a small component display system built from global CSS utilities and Astro component markup:

- `surface-label` for calm metadata pills.
- `surface-label__dot` for inline signal dots.
- `pearl-surface` for selected premium light surfaces.
- `soft-surface` for ordinary cards that need polish without iridescence.
- `pearl-panel` for selected product, solution, service detail, metric, and modal surfaces.
- `iridescent-edge` for restrained edge light on selected panels.
- `soft-surface-glow` for selected dark panels and CTA panels.
- Separate copy measure utilities for hero, page, section, panel, and card contexts.
- Container query behavior for product, service, and feature cards.

The label dot belongs inside the label treatment. Decorative dots should never float at the far right of a card unless they represent a real status layout with a clear semantic purpose.

The pearl treatment should stay subtle: warm off white, pale blue white, soft silver, and very low opacity aqua or lavender corner highlights. It should not animate in v1.

## Implementation Notes

- Product cards, metric cards, service detail panels, solution detail panels, and the inquiry modal can use `pearl-panel`.
- Ordinary feature and service cards should generally use `soft-surface` so the pearl treatment does not appear everywhere.
- Dark panels keep deep navy but can use the same `surface-label` structure in a dark variant.
- Selected dark panels and CTA panels can use `iridescent-edge` and `soft-surface-glow` at low intensity.
- Page and hero copy measures should be wider than card copy measures.
- Card copy should remain tighter for scanning.
- Component container queries should remain simple and local to reusable cards.
- No React, Preact, interactive island, or backend contact form is needed for this system.

## Copy And Visual Boundaries

- Keep labels muted and product-like.
- Use bright blue only for active navigation, focus states, and tiny signal dots.
- Do not add fake proof, fake claims, fake metrics, or client references.
- Preserve public product naming: Structured Analysis Pipeline and Matchup Analyzer.
- Do not expose DAI or restricted internal method terms in public copy.

## Consequences

Positive:

- Product and service cards feel more mature and intentional.
- Metadata labels now have a consistent structure.
- Page intros can breathe on desktop without making card copy too wide.
- Pearlescent surfaces add refinement while preserving Luminous Technical.
- Cards adapt better when reused at different widths.

Tradeoffs:

- Some display behavior now lives in global CSS utilities rather than only Tailwind class strings.
- Container query use should stay restrained so the system remains easy to reason about.

## QA Result

Responsive QA checked 360, 390, 430, 768, 1024, 1280, and 1440 widths across Home, Services, Products, Structured Analysis Pipeline, Matchup Analyzer, Solution Examples, About, and Contact.

Results:

- No horizontal overflow.
- Header and active navigation stable.
- Product card label dots no longer float at card edges.
- Footer and contact email wrap safely.
- Services overview-to-detail rhythm remains connected.
- `npm run build` passes.
- `npm run copy-check` passes.

## May 12 Update

The surface system was refined during the UI/UX polish pass:

- Pearl effects are now more selective.
- `soft-surface` handles ordinary cards.
- `pearl-panel` and `iridescent-edge` are reserved for stronger product, solution, CTA, and inquiry surfaces.
- The effect remains static, low opacity, readable, and restrained.
- Automated responsive QA checked 58 route-width and modal cases with 0 failures.
