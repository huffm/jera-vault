# 0001 Use Astro For Marketing Site

## Status

Accepted

## Context

Jera Technologies needs a focused public website that can present company positioning, services, products, solution examples, and contact information.

The first version should be fast, maintainable, and content friendly.

## Decision

Use Astro for the initial marketing site.

## Rationale

Astro is a strong fit for a content driven website with mostly static pages. It supports clean page structure, Markdown friendly content workflows, fast performance, and straightforward deployment.

## Consequences

- The site can start simple and grow over time.
- Content from this vault can map cleanly into pages and components.
- Product pages and solution examples can be built as structured content.
- Interactive product demos can be added later if needed.

## Slice 1 Result

Astro is now implemented in `jera-site` with Tailwind CSS 4 through `@tailwindcss/vite`, MDX, Astro content collections, and sitemap support.
