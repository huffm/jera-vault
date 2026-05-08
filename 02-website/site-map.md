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

Purpose: Explain how Jera Technologies helps with AI application engineering, enterprise modernization, automation, integrations, and decision support software.

Core content:

- AI application engineering.
- Enterprise modernization.
- Automation and integration.
- Decision support applications.
- Product experience development.

## Products

Purpose: Showcase Jera built products, including the Structured Analysis Pipeline and the Matchup Analyzer.

Core content:

- Products overview.
- Structured Analysis Pipeline.
- Matchup Analyzer.
- Product philosophy.
- Link to solution examples where useful.

## Solution Examples

Purpose: Show selected work patterns and engineering approaches without implying client work where none exists.

Core content:

- Structured AI decision artifact system.
- Data pipeline modernization.
- Authentication and integration work.
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

The current Contact page uses `support@jeratechnologies.com`.

Contact CTA behavior:

- Header `Discuss a project` routes to `/contact`.
- Primary contact CTAs route to `/contact`.
- Contact navigation items route to `/contact`.
- The `Email Jera Technologies` button uses `mailto:support@jeratechnologies.com?subject=Project%20Conversation%20with%20Jera%20Technologies`.

The site remains static for v1. A full backend contact form is intentionally deferred.

## Redirects

The retired `/products/dai/` route redirects to `/products/structured-analysis-pipeline/`.

Implementation notes:

- `vercel.json` defines a permanent redirect for Vercel preview and production deployment.
- A quiet local fallback page exists so local browser QA also lands on the current public product route.
- The retired route is excluded from the sitemap.
- Public navigation and public product links should use `/products/structured-analysis-pipeline/`.

## Launch Metadata

The site uses `https://jeratechnologies.com` as the production domain for canonical URLs, Open Graph URLs, and sitemap output.

## Future Contact Form Direction

A later slice may add a real contact form using:

- Astro API route or Astro Action.
- Vercel on demand rendering through the Vercel adapter.
- Resend for email delivery.
- Vercel environment variables for `RESEND_API_KEY` and `CONTACT_TO_EMAIL`.
- Optional Cloudflare Turnstile for spam protection.

Do not add this backend until the launch site needs it.
