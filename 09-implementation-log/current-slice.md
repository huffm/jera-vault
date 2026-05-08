# Current Slice

## Slice Name

Contact Email Cleanup And CTA Behavior Polish

## Goal

Replace placeholder contact emails, make contact CTAs route intentionally, keep the site static for v1, and document the future contact form direction.

## Website Changes

- Updated the shared site config email to `support@jeratechnologies.com`.
- Added `contactMailtoSubject` to the shared site config.
- Added a shared `contactMailtoHref` for email CTAs.
- Changed the Contact page `Email Jera Technologies` button to use `mailto:support@jeratechnologies.com?subject=Project%20Conversation%20with%20Jera%20Technologies`.
- Updated footer email links to use the same shared mailto behavior.
- Updated header, hero, and CTA section contact links to route to `/contact`.
- Updated page level primary contact CTAs to route to `/contact`.
- Left the site static and did not add Resend, serverless functions, Turnstile, or the Vercel adapter.

## Vault Changes

- Updated `02-website/current-site-state.md`.
- Updated `02-website/site-map.md`.
- Updated `07-content-rules/public-copy-rules.md`.
- Replaced this implementation log with the current slice details.

## Design Decisions

- Keep the existing Contact page layout and visual system.
- Avoid adding a form surface until there is a backend implementation plan.
- Keep the primary action simple and reliable for launch.

## Positioning Decisions

- Contact copy remains business facing and practical.
- The site continues to position Jera Technologies as a software engineering company that builds practical AI enabled products, automation systems, enterprise modernization solutions, and decision support applications.
- Structured Analysis Pipeline and Matchup Analyzer remain the public product names.
- DAI and internal method terms were not reintroduced into public copy.

## Build Result

Build passes.

Command used from `C:\Users\trolo\source\repos\jera-workspace\jera-site`:

`npm run build`

Copy check passes.

Command used from `C:\Users\trolo\source\repos\jera-workspace\jera-site`:

`npm run copy-check`

Additional source and generated HTML searches found no retired placeholder email addresses or placeholder domains.

The only source match for `synthesis` is the CSS property `font-synthesis-weight`, not public method copy.

## Remaining TODOs

- Add approved product screenshots or interface previews.
- Replace the placeholder social sharing image with a final brand approved image when available.
- Run one final Vercel preview smoke test after deployment.
- Add a real contact form later if mailto becomes insufficient.

## Recommended Next Slice

Deploy a Vercel preview and smoke test the live contact links, redirects, sitemap, metadata, and mobile header behavior.
