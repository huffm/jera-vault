# 0004 Interactive Islands Strategy

## Status

Deferred for v1.

## Decision

Do not add an interactive island during the mature product surface design pass.

## Context

The site is an Astro marketing site intended to stay fast, static, and launch ready. The current content already explains Jera Technologies, its services, and its product portfolio without requiring interaction.

A small Capability Explorer could be useful later, especially on the Home or Services page, but it should only be added if it improves visitor understanding.

## Rationale

- Avoid adding interaction just to use Astro.
- Preserve static launch readiness.
- Keep this pass focused on typography, product cards, labels, dark panels, and public copy restraint.
- Avoid adding Preact, React, or new JavaScript unless the interaction clearly earns its place.
- Revisit after preview feedback if visitors need a guided way to map business needs to Jera capabilities.

## Future Option

A later slice may add a small accessible Capability Explorer with:

- AI Application Engineering.
- Enterprise Modernization.
- Automation And Integration.
- Decision Support Systems.
- Product Experience Buildout.

The island should use buttons with a clear selected state, minimal JavaScript, no heavy animation, and no dependency on the interaction to understand the site.
