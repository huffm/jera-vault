# Site Map

The initial Jera Technologies website should be concise, business facing, and easy to scan.

## Primary Navigation

1. Home
2. Services
3. Products
4. Solution Examples
5. About
6. Contact

## Home

Purpose: Quickly explain what Jera Technologies does, what types of software it builds, and why the product portfolio demonstrates real engineering capability.

Core content:

- Company positioning.
- Service categories.
- Product portfolio summary.
- Selected solution examples.
- Clear contact path.

## Services

Purpose: Explain how Jera Technologies helps with Applied AI, enterprise modernization, automation, integrations, and decision support software.

Core content:

- Applied AI.
- Enterprise modernization.
- Automation and integration.
- Decision support applications.
- Product experience development.

## Products

Purpose: Present Jera product lab concepts and prototypes, including the Structured Analysis Pipeline and the Matchup Analyzer.

Core content:

- Product lab overview.
- Structured Analysis Pipeline.
- Matchup Analyzer.
- Product philosophy.
- Link to solution examples where useful.

## Solution Examples

Purpose: Show selected work patterns and engineering approaches without implying client work where none exists.

Core content:

- Structured decision support system.
- Data pipeline modernization.
- Authentication and integration modernization.
- Template for future examples.

## About

Purpose: Present Jera Technologies and Malcolm's role credibly.

Core content:

- Founder / Principal Software Engineer.
- Product minded software engineering.
- AI adjacent engineering direction.
- Enterprise systems and practical product delivery.

## Contact

Purpose: Give a direct path for business conversations.

Core content:

- Short contact message.
- Email or form.
- Services of interest.
- Product discussion option.

## Current Route Implementation

Implemented current routes:

- `/`
- `/services/`
- `/products/`
- `/products/structured-analysis-pipeline/`
- `/products/matchup-analyzer/`
- `/solution-examples/`
- `/about/`
- `/contact/`

The current Contact page uses the secure inquiry form and does not expose the receiving inbox in public source.

Contact CTA behavior:

- Header `Discuss a project` routes to `/contact`.
- Primary contact CTAs route to `/contact`.
- Contact navigation items route to `/contact`.
- Contact actions open the inquiry form and fall back to `/contact` when JavaScript is unavailable.

The Astro site is static, with inquiry submission handled by the `/api/inquiry` Vercel Function.

## Redirects

The retired `/products/dai/` route redirects to `/products/structured-analysis-pipeline/`.

Implementation notes:

- `vercel.json` defines permanent redirects for both `/products/dai` and `/products/dai/` for Vercel preview and production deployment.
- A quiet local fallback page exists so local browser QA also lands on the current public product route.
- The retired route is excluded from the sitemap.
- Public navigation and public product links should use `/products/structured-analysis-pipeline/`.

## Launch Metadata

The site uses `https://jeratechnologies.com` as the production domain for canonical URLs, Open Graph URLs, and sitemap output.

Current launch metadata status:

- Default title and description are generated through the shared SEO component.
- Canonical URLs use `https://jeratechnologies.com`.
- Open Graph title, description, URL, image, and image alt text are present.
- Twitter card, title, description, and image metadata are present.
- Theme color is set.
- Placeholder social image output exists at `/social-card.svg`.
- Sitemap output uses `https://jeratechnologies.com`.
- `/products/dai/` is excluded from the sitemap.

## Current Contact Form Direction

The contact path is now the secure inquiry form:

- Static Astro site plus the root Vercel Function at `/api/inquiry`.
- Resend for email delivery.
- Cloudflare Turnstile for spam protection.
- Vercel environment variables for `PUBLIC_FORM_ENABLED`,
  `PUBLIC_TURNSTILE_SITE_KEY`, `TURNSTILE_SECRET_KEY`, `RESEND_API_KEY`,
  `CONTACT_TO_EMAIL`, `CONTACT_FROM_EMAIL`, and `CONTACT_ALLOWED_ORIGINS`.

See `02-website/inquiry-endpoint-deployment.md` for deployment and production
origin allowlist details.
