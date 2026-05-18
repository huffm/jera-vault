# Current Slice

## Slice Name

Premium Design Architecture Pre-Launch Pass

## Goal

Make the Jera Technologies public site feel more polished, more intentional, more trustworthy, and more product quality so it reads as a top-dollar independent software studio. Keep the existing positioning, the Astro static delivery model, and the simplified inquiry experience.

## May 15 Premium Design Architecture Pass

This pass acted as a senior refinement of the Luminous Technical system, not a redesign.

Implemented changes:

- Reorganized the global CSS token system into named groups for text, brand anchors, pearl detail, hairlines, borders, elevation, radii, layout, and the focus ring.
- Introduced a three step elevation scale (`--shadow-soft`, `--shadow-card`, `--shadow-lift`) plus a dedicated `--shadow-dark` for technical panels and a refined `--shadow-glow`.
- Added `--color-border-soft` and `--color-border-strong` tokens and a `--ring-color` token for focus visible.
- Added body level `font-feature-settings: "ss01", "cv11", "kern"` and `font-optical-sizing: auto` plus slight negative tracking on display headings, the homepage H1, the modal title, and the section, panel, and card heading utilities.
- Added a shared `.hairline` and `.hairline--dark` divider utility plus a `.tabular-nums` utility used by step counters, metric values, and the dark capability tiles.
- Refined the iridescent edge treatment with softer right and bottom borders so the utility cannot produce a doubled line.
- Disabled `iridescent-edge::after` on the inquiry modal panel so the right edge artifact is fully resolved regardless of scrollbar gutter behavior.
- Refined the button system. Primary uses a deeper vertical gradient with inset highlight and layered shadow. Secondary layers an inset highlight on a soft hairline border. Dark uses an inset highlight on a darker outer shadow. All buttons gained a 200ms cubic bezier hover and a small `:active` settle.
- Refined the header lockup so the JT mark carries a subtle radial highlight, and the brand subtitle uses a slightly larger mobile measure so `Practical AI & Software Engineering` wraps deliberately. Active nav uses a stronger blue border and a calm translucent fill.
- Refined the footer with a soft top hairline, the same JT mark treatment, tighter heading tracking, and a clean wrap behavior for the contact email at every width.
- Refined the hero with three corner glows, a small focus / approach / output trust strip, and a calmer workflow artifact with tabular numeral step counters.
- Refined cards: feature, service, and process cards carry an inline top hairline; product cards use the shared label only; metric card uses `text-wrap: balance` on the value; process step pairs the counter with a fading hairline lead in; dark product panel uses `01 / 02 / 03 - Capability` lead ins on its capability tiles.
- Applied the requested inquiry modal copy exactly. Refined the entrance animation, the SVG cross close icon, the SVG check submit icon, focus visible style across fields, the action area divider, and the desktop two-column action layout with the CTA left and the email helper right.
- Renamed the homepage product portfolio eyebrow from `Product portfolio` to `Product lab` to match the brand direction of describing surfaced work as Jera built products and product lab work.
- Replaced About metric values `Focus / AI` and `Approach / Build` with `Focus / Applied AI` and `Method / Structured`.
- Expanded `check-public-copy.mjs` with the additional restricted phrases from the launch brief (`public positioning`, `recruiters`, `future consulting prospects`, `built to feel credible`, `broad enough`, `fake agency`, `AI Application Engineering`, `Applied AI Engineering`, `jerattechnologies.com`, `client's system`, `internal workflow`).

Validation:

- `npm run build` passed and produced 9 static pages.
- `npm run copy-check` passed across 9 generated HTML files with the expanded restricted term list active.
- `npm run preview` served the build at `http://localhost:4322/`.
- Home, Services, Products, Structured Analysis Pipeline, Matchup Analyzer, Solution Examples, About, and Contact all returned 200 on the preview server.
- The inquiry modal was rechecked at 390px x 900px, 768px x 900px, and 1280px x 900px. The headline wraps cleanly at each size, the CTA and the fallback email remain visible at 390px x 900px, no right edge artifact remains, and no horizontal overflow was detected.
- Console errors and warnings were 0 across the previewed routes.

Remaining Vercel preview QA:

- Deploy a Vercel preview.
- Recheck the modal and the eight public pages at 390px, 768px, and 1280px on the live preview.
- Confirm the mailto handoff opens the expected mail client from the live preview.
- Confirm the native select popup appearance in the target browsers.
- Smoke test contact links, redirects, metadata, sitemap, and console output on the live preview.

## Earlier Slice Notes

The earlier UI/UX polish slice notes are retained below for historical context. The premium design architecture pass kept all of those decisions in force and refined them.

## Original Slice Name

High-Level UI/UX Polish, Copy Refinement, And Inquiry Experience Design Pass

## Original Goal

Make the public Astro site feel more mature, crafted, welcoming, product-quality, and intentionally designed before Vercel preview without rebuilding the site or adding backend risk.

## May 15 Inquiry Modal Form Quality Pass

This pass focused only on the Jera Technologies inquiry modal before Vercel preview.

Implemented changes:

- Removed the odd double line on the modal right edge by softening the modal-specific iridescent overlay and removing the always reserved scrollbar gutter.
- Updated the inquiry category options to `Applied AI`, `Enterprise Modernization`, `Workflow Automation`, `Architecture & Integration`, `Decision Support Systems`, `Product Strategy`, and `Not Sure Yet`.
- Updated the final modal headline to `Rough idea, stubborn workflow, or modernization effort?`.
- Updated the final modal intro to `Send over the shape of it, even if it is still messy. Jera Technologies will help turn it into a practical next step.`
- Updated the message label to `What needs attention?` and the placeholder to describe a workflow, legacy system, modernization effort, product idea, integration, or decision process that needs improvement.
- Replaced the fallback helper with `Prefer a direct email?` and `Send a short note to:`.
- Confirmed the fallback email is `support@jeratechnologies.com`.
- Improved text wrapping with balanced headline wrapping and prettier supporting copy wrapping where supported.
- Reworked the footer so desktop uses CTA left and direct email helper right, while mobile stacks cleanly with a visible CTA and fallback email.
- Kept the native select for accessibility and styled the closed state with a calmer border, focus ring, and aligned chevron.
- Documented the native select limitation: the open option list is browser and OS controlled, so a custom dropdown was not added for this launch.
- Replaced the retired public service label with `Applied AI` while preserving the existing stable slug.

Validation:

- `npm run build` passed and generated 9 static pages.
- `npm run copy-check` passed across 9 generated HTML files.
- Generated output and public site source no longer include the retired service label, retired engineering variant, retired fallback helper, or typo contact email.
- `npm run preview` served successfully at `http://127.0.0.1:4321/`.
- Modal screenshots were checked at 390px by 900px, 768px by 900px, and 1280px by 900px.
- The CTA and fallback email remain visible at 390px by 900px.
- No horizontal overflow was detected in the checked modal viewports.
- Escape close, outside click close, focus return, and native invalid form behavior still pass.

Remaining Vercel preview QA:

- Deploy a Vercel preview.
- Recheck the modal at 390px, 768px, and 1280px widths on the preview URL.
- Confirm native select popup appearance in target browsers.
- Confirm mailto handoff on the live preview.
- Smoke test contact links, redirects, metadata, sitemap, and console output.

## May 14 Public Copy And UX Refinement

This pass refined public copy and the inquiry experience without changing the site architecture or visual system.

Implemented changes:

- Changed the header subtitle from `Applied software engineering` to `Practical AI & Software Engineering`.
- Let the header subtitle wrap cleanly under the brand on mobile.
- Removed internal About page positioning language about public credibility, recruiters, future consulting prospects, and broad client-specific work.
- Kept the About section heading `Calm engineering for complex systems`.
- Rewrote the About operating principle cards so they explain practical AI, enterprise judgment, and product minded delivery in public-facing language.
- Completed a public copy sweep for internal-sounding terms including `public positioning`, `recruiters`, `future consulting prospects`, `built to feel credible`, `broad enough`, `showcase`, `lab`, and `fake agency`.
- Replaced public `client's system` wording with `existing system`.
- Replaced public `internal workflow` wording with `operational workflow`.
- Simplified the inquiry modal to project category, name, email, company, and message fields.
- Updated inquiry modal copy to use `Tell us what you are trying to build`, a warmer short intro, and the primary CTA `Send inquiry`.
- Preserved the mailto draft behavior and fallback email link.
- Tightened modal spacing, field sizing, focus states, placeholder copy, and mobile layout while keeping the pearl panel aesthetic.

Validation:

- `npm run build` passed after the sandboxed run failed with `spawn EPERM` and the command was rerun outside the sandbox.
- `npm run copy-check` passed across 9 generated HTML files.
- Generated HTML contains the new header subtitle and inquiry modal copy.
- Generated HTML does not contain the targeted internal public copy terms from this pass.

## May 14 Responsive UI Refinement Addendum

This addendum refined layout rhythm, responsive typography, detail panels, and the inquiry modal after visual inspection at mobile, tablet, and desktop widths.

Implemented changes:

- Reduced desktop nav chip density at tablet widths so the header has more room before the wide desktop CTA appears.
- Widened mobile page and section heading measures to reduce awkward heading fragments without adding brittle manual line breaks.
- Added a shared `detail-panel` system for Services and Solution Examples.
- Changed Services detail panels so outcome cards use the full panel width, with two columns on small tablet widths and three columns on desktop.
- Changed Solution Examples detail panels so pattern cards use the full panel width, with two columns from small tablet upward.
- Tightened inquiry modal width, height, field spacing, textarea height, and action spacing so the CTA and fallback email stay visible on common mobile and desktop viewports.
- Added inquiry trigger event delegation for current and future project CTAs.
- Added native validity checking and mailto body sanitization for inquiry form fields.
- Updated Products page copy to avoid portfolio and credibility framing in favor of direct product language.

Responsive QA:

- Checked `/`, `/about/`, `/services/`, `/products/`, `/solution-examples/`, `/contact`, `/products/structured-analysis-pipeline/`, and `/products/matchup-analyzer/`.
- Checked 390px, 768px, and 1280px widths.
- No horizontal overflow was detected on any checked route or width.
- Inquiry modal was checked at 390px by 900px and 1280px by 900px.
- The modal fits both checked viewports, focuses the project category field, and keeps the primary CTA visible.
- Built output was served with `npm run preview` and checked again at 390px, 768px, and 1280px across the same public routes.
- Preview modal checks passed at 390px by 900px and 1280px by 900px.

Validation:

- `npm run build` passed and generated 9 static pages.
- `npm run copy-check` passed across 9 generated HTML files.
- Generated HTML search found no targeted internal copy terms or restricted product exposure terms.

## Website Changes

- Refined homepage hero copy to `Practical software for structured AI workflows`.
- Reworked the workflow model heading to `A practical path from idea to usable software`.
- Widened and separated page heading, page intro, section intro, panel copy, and card copy measures.
- Reduced section heading aggressiveness so desktop headings do not become narrow text towers.
- Kept headings balanced and paragraph wrapping pretty where supported.
- Rewrote the homepage services intro to avoid the awkward `decision support software` line break.
- Rewrote footer brand copy to feel cleaner, warmer, and less generic.
- Changed `Authentication And Integration Work` to `Authentication & Integration Work`.
- Changed public `Automation And Integration` service copy to `Automation & Integration`.
- Reworked About copy so the page is company-first rather than centered on Malcolm by name.
- Preserved broad, client-flexible service positioning and broad Enterprise Modernization language.

## Pearl Surface Refinements

- Split the surface system into `soft-surface`, `pearl-panel`, `iridescent-edge`, and `soft-surface-glow`.
- Kept ordinary cards calmer with `soft-surface`.
- Used `pearl-panel` and `iridescent-edge` selectively on product cards, service and solution detail panels, metric cards, and the inquiry modal.
- Added subtle iridescent edge and soft glow treatments to selected dark product and CTA panels.
- Kept pearl effects static, low opacity, readable, and restrained.
- Avoided neon gradients, rainbow shimmer, heavy glassmorphism, and busy backgrounds behind text.

## Inquiry Popup Decision

Implemented Option A.

The site now has a polished accessible inquiry modal that submits through mailto instead of a backend.

Fields:

- Project category.
- Name.
- Email.
- Company.
- Message.

Behavior:

- `Discuss a project` opens the modal when JavaScript is available.
- Project/contact CTAs that point to `/contact` open the modal when JavaScript is available.
- Contact navigation still routes to `/contact`.
- The Contact page includes an inquiry trigger and direct email fallback.
- Submission opens a mailto draft to `support@jeratechnologies.com`.
- The modal supports Escape close, click-outside close, a close button, focus entry, and focus return.
- No React, Preact, Astro island, or backend form service was added.

## About And Footer Refinements

About:

- Public copy now says Jera Technologies is led with a focus on practical software, structured workflows, and product-minded engineering.
- The dark About panel now says `Led with a focus on practical software and structured workflows`.
- The page no longer uses `Malcolm leads...` as the public lead framing.

Footer:

- Brand copy now reads as practical product and modernization support rather than a generic agency line.
- Footer email remains `support@jeratechnologies.com`.
- Footer wrapping remains clean across narrow widths.

## Responsive QA Findings

Checked routes:

- `/`
- `/services/`
- `/products/`
- `/products/structured-analysis-pipeline/`
- `/products/matchup-analyzer/`
- `/solution-examples/`
- `/about/`
- `/contact`

Checked widths:

- 360px
- 390px
- 430px
- 768px
- 1024px
- 1280px
- 1440px

Results:

- Automated responsive QA ran 58 route-width and modal checks with 0 failures.
- No horizontal scrolling was detected.
- Header remained stable.
- Active navigation remained correct.
- Major headings stayed within accepted line counts.
- Intro copy used wider desktop measures.
- Solution example headings were clean, including `Authentication & Integration Work`.
- About copy is company-first.
- Footer brand copy and email wrapping are clean.
- Pearl effects remain subtle and readable.
- Inquiry modal works on mobile and desktop.
- Contact fallback remains clear.
- CTA panels do not feel oversized after spacing adjustments.
- Browser console checks reported no errors or warnings.

## Build Result

Build passes.

Command used from `C:\Users\trolo\source\repos\jera-workspace\jera-site`:

`npm run build`

The build generated 9 static pages.

## Copy Check Result

Copy check passes.

Command used from `C:\Users\trolo\source\repos\jera-workspace\jera-site`:

`npm run copy-check`

Generated HTML was also searched for:

- `support@yourtechnologies.com`
- `hello@jeratechnologies.com`
- `help@yourtechnologies.com`
- `yourtechnologies.com`
- `DAI`
- `retrieval`
- `evaluation`
- `synthesis`
- `betting model`
- `prediction engine`
- `profit`
- `Malcolm leads`
- `Authentication And Integration Work`

No matches were found across generated HTML.

## Remaining TODOs

- Deploy a Vercel preview.
- Smoke test the deployed preview URL, redirects, metadata, sitemap, contact links, inquiry modal, active navigation, and responsive layout.
- Add approved product screenshots or interface previews when available.
- Replace the placeholder social sharing image with a final brand approved image when available.
- Consider a backend contact form only if mailto becomes insufficient after preview feedback.

## Recommendation

The site is ready for Vercel preview after this UI/UX polish and inquiry experience pass.

## May 15 Text Composition Pass

Focused follow up to the premium design architecture pass. This pass introduced a shared text composition system and applied it across the public site so words sit deliberately rather than stretching to container width.

Implemented changes:

- Added measure tokens on `:root` for display, page heading, section heading, panel heading, card heading, lead, intro, copy, panel, card, helper, footer, legal, and tagline.
- Added a `.measure-*` utility family plus `.balance-text` and `.pretty-text`.
- Refactored the existing measure classes (`section-copy`, `section-copy-measure`, `page-copy`, `page-copy-measure`, `hero-copy-measure`, `panel-copy-measure`, `card-copy-measure`, `copy-measure`, `section-title`, `page-heading`) to point at the new tokens. The largest fix was section and page intro measure, which dropped from 62 to 64rem (about 80 to 95 ch) to 56ch.
- Removed the default max-inline-size on `.panel-heading` and `.card-heading`. Components apply `.measure-panel-heading` (28ch) and `.measure-card-title` (22ch) explicitly where a deliberate wrap is needed.
- Switched the measure system to `max-inline-size` with `hyphens: none` and `overflow-wrap: break-word`.
- Applied the new system across the Hero, CTA section, dark product panel, About and Contact dark panels, Structured Analysis Pipeline and Matchup Analyzer hero panels, Services and Solution Examples detail panels, the Footer, and the Inquiry modal.
- Reduced one redundant phrase in the Contact panel description (`enterprise workflow modernization` to `enterprise modernization`).

Validation:

- `npm run build` passed and produced 9 static pages.
- `npm run copy-check` passed across 9 generated HTML files.
- `npm run preview` served the build at `http://localhost:4323/`.
- Manual visual QA covered Home, Services, Products, Structured Analysis Pipeline, Matchup Analyzer, Solution Examples, About, and Contact at 390px, 768px, 1280px, and 1440px.
- Measure spot checks at 1440px: section intros at approximately 522px (56ch), section titles at approximately 487px (24ch), CTA panel heading at approximately 638px (2 balanced lines). The homepage section intro `Jera Technologies focuses on products and business systems that make complex workflows easier to operate, inspect, and improve.` now wraps to 2 lines instead of running edge to edge.
- Inquiry modal was rechecked at 390x900 and 1280x900. Title wraps balanced, intro wraps to a pretty multi line shape, the CTA and the fallback email remain visible, and there is no right edge artifact.
- No horizontal overflow detected at any tested width.
- Console errors and warnings remained 0.

Remaining Vercel preview QA:

- Deploy a Vercel preview and recheck the same widths.
- Recheck the inquiry modal at 390px, 768px, and 1280px on the preview URL.
- Confirm mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in the target browsers.
- Smoke test contact links, redirects, metadata, sitemap, and console output.

## May 15 Section Intro Measure And Rhythm Pass

Follow up to the text composition pass after visual review showed section intros wrapping too narrowly (the homepage `Each product shows how Jera turns complex workflows into structured software, reviewable outputs, and business facing experiences.` line breaking into too many short fragments).

Implemented changes:

- Widened intro measure tokens. `--measure-intro` 56ch to 76ch. New `--measure-page-intro` at 72ch for page heroes. `--measure-lead` 50ch to 58ch. `--measure-copy` 60ch to 64ch. `--measure-panel` 52ch to 58ch. `--measure-card` 38ch to 42ch. `--measure-footer` 38ch to 40ch. `--measure-tagline` 38ch to 40ch.
- Repointed `.page-copy` and `.page-copy-measure` at the new `--measure-page-intro` so page hero intros target a slightly tighter ch count than section intros (since they render at a larger font size and the target pixel width is the same).
- Added a `.measure-page-intro` utility class for explicit application.
- Bumped `section-shell__header` margin bottom across the three variants. Standard now lands roughly 36px to 50px below the intro, page hero 41px to 57px, and compact 30px to 40px.

Validation:

- `npm run build` passed and produced 9 static pages.
- `npm run copy-check` passed across 9 generated HTML files.
- `npm run preview` served at `http://localhost:4324/`.
- Section intros at 1440px and 1280px both render at approximately 708px wide and wrap to 2 lines, landing inside the 680px to 760px target.
- Mobile (390px) and tablet (768px) intros remain container bound and still read as natural mobile paragraphs.
- No horizontal overflow at any tested width.
- Console errors and warnings remained 0.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in the target browsers.
- Smoke test contact links, redirects, metadata, sitemap, and console output.

## May 15 Editorial Compression Pass

Focused editorial pass after the visual and layout work. Verbose section intros, list-heavy descriptions, and repeated subject phrases were compressed so the public copy reads calm and deliberate.

Files changed:

- src/pages/index.astro: hero copy, what Jera builds intro, product lab intro, services intro, decision artifact dark panel description, workflow model intro, CTA description, Modernized Enterprise Workflows build card description.
- src/pages/services/index.astro: hero intro and CTA description.
- src/pages/products/index.astro: hero intro, process intro, CTA description.
- src/pages/products/structured-analysis-pipeline.astro: dark intro panel description, workflow intro, what it demonstrates intro, CTA description.
- src/pages/products/matchup-analyzer.astro: dark intro panel description, workflow intro, what it demonstrates intro, CTA description.
- src/pages/solution-examples/index.astro: hero intro and CTA description.
- src/pages/about.astro: hero intro, founder panel description, operating principles intro, CTA description.
- src/pages/contact.astro: hero intro, dark panel description.
- src/components/sections/HeroSection.astro: hero copy paragraph.
- src/components/layout/Footer.astro: brand description.
- src/config/site.ts: default SEO meta description.
- src/content/services/ai-application-engineering.mdx: description.
- src/content/services/automation-and-integration.mdx: description.
- src/content/services/decision-support-systems.mdx: description.
- src/content/services/enterprise-modernization.mdx: description.
- src/content/services/product-experience-buildout.mdx: description.
- src/content/solution-examples/ai-decision-artifact-system.mdx: description.
- src/content/solution-examples/data-pipeline-modernization.mdx: description.
- src/content/solution-examples/enterprise-modernization-patterns.mdx: description.

Editorial moves applied:

- Removed leading Jera Technologies from sentences that did not need a subject.
- Replaced six-item lists with two or three concrete phrases.
- Replaced business facing experiences and AI enabled workflows where a stronger phrase fit.
- Shortened CTAs to direct verbs followed by the offer (Bring..., Turn..., Define..., Organize..., Shape...).
- Differentiated the footer brand description from the bottom row tagline so they no longer read as near duplicates.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served at http://localhost:4325/.
- At 1440px: hero copy 580px and 2 lines. Section intros 708px and 1 to 2 lines. The previously flagged sentences (Each product shows... and Jera Technologies helps shape...) now render as one line each.
- At 1280px and 768px: intros sit comfortably inside the container, no horizontal overflow.
- At 390px: clean mobile stacking, no awkward orphan words.
- Console errors and warnings remained 0.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in target browsers.
- Smoke test contact links, redirects, metadata, sitemap, and console output.

## May 15 Section Rhythm And Footer Composition Pass

Implemented changes:

- Switched SectionShell from class={headerClass} to class:list={headerClass}. This was a latent bug: the section header variants had been rendered as comma joined class strings and the margin rules were never matching. The fix lets the section header rhythm tokens actually apply.
- Refactored .section-shell__header into a flex column with > * + * margin cascade so the eyebrow + heading + intro stack stays consistent.
- Tuned margin-block-end clamps to land within the brief targets: standard (1.85rem to 3rem), page (2.1rem to 3.15rem), compact (1.55rem to 2.35rem).
- Updated the homepage Solution Examples intro and the Solution Examples page hero intro to share the same short statement: Reusable patterns for structured workflows and clearer implementation.
- Replaced the footer brand blurb with: Practical AI and software engineering for clearer workflows.
- Removed the bottom row footer tagline so the footer closes with the brand blurb above and a single copyright line.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served at http://localhost:4326/.
- Header margin spot checks at 390px (29.6px), 768px (30.7px), and 1440px (48px standard, 37.6px compact). All inside the brief target ranges of 24 to 32 mobile, 28 to 40 tablet, 32 to 48 desktop.
- Footer brand blurb renders as one line on desktop and a tight two line wrap on mobile, with no horizontal overflow and no competing tagline.
- Console errors and warnings remained 0.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in target browsers.
- Smoke test contact links, redirects, metadata, sitemap, and console output.

## May 15 Mobile Nav + Composition Verification Pass

Diagnosed and fixed the mobile nav Contact item. The pill was geometrically full row in every prior pass (verified via offsetWidth and elementFromPoint), but the bg-white at 65% opacity on the warm header made the right half visually disappear. The user's reported bug was a contrast artifact, not a layout bug.

Implemented changes:

- src/components/layout/Header.astro:
  - Removed justify-items-start from the mobile nav grid so col-span cells stretch naturally.
  - All mobile nav links now use inline-flex items-center justify-center for centered labels inside full width pills.
  - Contact carries a mobile-nav-contact class and a dedicated state class. Below sm, Contact is a deep navy filled pill with white text, inset highlight, and a layered shadow. At sm and above, Contact returns to the light chip style.
  - Active state still wins over the dark Contact treatment.
- src/styles/global.css:
  - Added .mobile-nav-shell .mobile-nav-contact { grid-column: 1 / -1; justify-self: stretch; } below 639px so the spanning is robust.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served at http://localhost:4328/.
- Mobile nav verified at 390px and 430px. Contact pill renders as a clearly distinct primary action spanning the full row.
- Tablet (700px) and desktop (768px, 1280px, 1440px) nav layout unchanged.
- Active state verified on /contact. Pill renders in soft blue active treatment and still spans full row on mobile.
- Modal spot checked at 1280x900. Copy, dialog semantics, focus handling, and mailto behavior preserved.
- No horizontal overflow at any tested width. Console errors and warnings remained 0.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in target browsers.
- Smoke test contact links, redirects, metadata, sitemap, and console output.

## May 15 Mobile Contact Centering + Footer Line Pass

Implemented changes:

- src/styles/global.css:
  - Replaced the dark navy primary treatment for the mobile Contact pill with a geometry-only rule. .mobile-nav-shell .mobile-nav-contact at max-width: 639px now uses grid-column: 1 / -1, justify-self: center, and width: calc(50% - 0.25rem) so Contact matches the other nav chips in size and sits centered in the third row.
  - --measure-footer widened from 40ch to 64ch so the footer brand blurb can sit on one line at desktop without being capped early.
- src/components/layout/Footer.astro:
  - Footer grid changed from lg:grid-cols-[0.96fr_1.04fr] to lg:grid-cols-[minmax(0,1.18fr)_minmax(0,0.82fr)] so the left brand column has more horizontal room.
- src/components/layout/Header.astro:
  - The mobile nav logic now hands Contact the standard activeNavClass / inactiveMobileNavClass like every other chip. The mobile-nav-contact CSS hook handles the centering geometry below sm. At sm and above the CSS rule does not apply and Contact behaves like the other chips.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served at http://localhost:4329/.
- Mobile nav verified at 390px and 430px: Contact matches the other chips in styling and width and sits centered in the third row.
- /contact verified at mobile: chip shows soft blue active treatment.
- Footer brand blurb verified on one line at 1280px (519px width) and 1440px. Two natural lines on mobile.
- Inquiry modal opens, title reads correctly, close button works.
- No horizontal overflow at any tested width. Console clean.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in target browsers.
- Smoke test contact links, redirects, metadata, sitemap, and console output.

## May 17 Reusable UI/UX Skill Creation Pass

Created a generic, project scoped Claude Code skill that captures the senior UI/UX judgment developed across the recent Jera refinement passes.

Implemented:

- New skill at .claude/skills/product-ui-design-architect (generic, reusable, not Jera specific).
- SKILL.md with valid YAML frontmatter and concise guidance, including: use the official frontend-design skill alongside it, read only the relevant references, treat project docs as the source of truth, do not override project identity, update project docs after meaningful changes, route reusable lessons to the skill and project lessons to the vault, no dependencies without approval, prefer simple maintainable changes.
- Twelve reference files: design-principles, vault-integration, project-profile-template, text-rhythm, section-spacing, modal-and-form-quality, mobile-navigation, footer-composition, accessibility-checklist, launch-readiness, lessons-learned, example-project-profile-jera.
- scripts/README.md describing candidate future QA scripts (none written yet).
- Four examples: good-section-header, good-footer, good-modal, anti-patterns.

Boundaries respected:

- Anthropic's official frontend-design skill was not modified.
- No DAI repos were touched.
- No site code changed and nothing was deployed.

How the loop compounds:

- Future reusable UI/UX lessons go into the skill's references/lessons-learned.md.
- Jera specific lessons stay in jera-vault.
- The skill's example-project-profile-jera.md links the generic skill to the jera-vault doc paths and the dai-workspace boundary.

## May 17 Design Source Research Workflow Pass

Extended the generic product-ui-design-architect skill with a responsible
design source research workflow. No Jera site code changed in this pass.

Created in the skill:

- scripts/design_source_miner.py: collects public GitHub API metadata and
  a small set of config and style files into references/design-source-
  library.md. Standard library only, caches responses, reads an optional
  GITHUB_TOKEN, drops to lower-volume mode without one. Does not clone,
  scrape HTML, or download large files.
- scripts/design_source_selector.py: filters the library against project
  docs and an optional use case with transparent weighted keyword scoring,
  and writes references/project-design-source-brief.md. No API calls, no
  embeddings.
- scripts/.gitignore: ignores .cache/, *.tmp, __pycache__/, *.pyc.
- references/design-source-workflow.md: documents the mine, select, design
  pass, document, route-lessons loop.

Updated in the skill:

- SKILL.md: added the design source research workflow note and reference.
- scripts/README.md: documented both scripts, GITHUB_TOKEN, cache
  behavior, responsible use, and example commands.
- references/vault-integration.md: documented how project docs drive
  source selection.
- references/launch-readiness.md: noted design source briefs are optional
  research aids, not launch gates.
- references/lessons-learned.md: added reusable lessons on treating design
  research as inspiration only and keeping selection project driven.
- references/example-project-profile-jera.md: added example selector
  inputs for Jera.

Validation:

- Both scripts pass python -m py_compile.
- Miner test run (--max-repos 3 --per-query 2 --min-stars 500) collected 3
  permissively licensed sources and wrote design-source-library.md.
- Selector run against jera-vault/02-website/design-direction.md,
  jera-vault/07-content-rules/public-copy-rules.md, and
  jera-vault/09-implementation-log/current-slice.md wrote
  project-design-source-brief.md with Jera signals detected across all six
  signal groups.
- references/design-source-library.md and references/project-design-
  source-brief.md both generated.

Boundaries respected:

- Anthropic's official frontend-design skill was not modified.
- No DAI repos were touched.
- No git was initialized at the workspace root.
- Nothing was deployed.

## May 17 Service Copy Compression Pass

Project-aware editorial pass using frontend-design for visual judgment and
product-ui-design-architect for text rhythm and project vault integration.

Vault docs read: current-site-state.md, design-direction.md,
public-copy-rules.md, current-slice.md. Skill references applied:
text-rhythm, section-spacing, footer-composition, vault-integration,
launch-readiness.

Implemented changes (jera-site):

- src/pages/services/index.astro: compressed the Services hero intro.
- src/content/services/ai-application-engineering.mdx: compressed
  description.
- src/content/services/enterprise-modernization.mdx: compressed
  description.
- src/content/services/decision-support-systems.mdx: compressed
  description.
- src/content/services/product-experience-buildout.mdx: compressed
  description.
- src/content/solution-examples/ai-decision-artifact-system.mdx:
  compressed description.
- src/content/solution-examples/authentication-and-integration-work.mdx:
  compressed description.

No CSS or component changes. The section rhythm and measure tokens from
earlier passes already produce correct spacing; compressing the copy was
the right fix rather than touching layout.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served at http://localhost:4330/.
- Rendered QA: Services detail panel intros are one line each at 1280px;
  the Services hero intro is one line; Solution Examples intros are one or
  two calm lines; homepage service cards are a tidy two lines.
- No horizontal overflow at 390px, 430px, 768px, 1280px, 1440px on Home,
  Services, Products, Structured Analysis Pipeline, Matchup Analyzer,
  Solution Examples, About, and Contact.
- Mobile Contact nav remains the centered uniform chip, readable.
- Inquiry modal opens, fits, and renders correctly at 430px.
- Console errors and warnings remained 0.

Skill lessons:

- No new reusable lesson was added. This pass reinforced the existing
  product-ui-design-architect lessons "Compress copy before adjusting
  measure" and "Intros are not feature lists", which already cover it.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in target browsers.
- Smoke test contact links, redirects, metadata, sitemap, console output.

## May 17 About Page Voice Pass

Copy and text rhythm pass on the About page using frontend-design for
voice judgment and product-ui-design-architect for text rhythm and
project vault integration. Vault docs read: current-site-state.md,
design-direction.md, public-copy-rules.md, current-slice.md.

Implemented changes (jera-site):

- src/pages/about.astro: applied the new About copy direction. Page
  heading, page intro, dark card heading and body, both MetricCard values
  and bodies, operating principles heading and intro, and all three
  principle card bodies were rewritten to a calmer, more human, lightly
  witty voice. No layout or component changes.

The page now reads down to earth and product minded without hype. The
wit is light (messy work, not slideware, AI that earns its keep).

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served at http://localhost:4331/.
- About inspected at 390px, 768px, 1280px, 1440px.
- The h1 wraps to a clean 2 lines at 768px and up.
- MetricCard values render as balanced short headings.
- No horizontal overflow at any inspected width.
- No restricted internal copy in generated HTML. Console clean.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the About page at the same widths.
- Confirm mailto handoff, native select popup, contact links, redirects,
  metadata, sitemap, and console output on the live preview.

## May 17 Editorial Systems Pass

Project-aware editorial systems pass using frontend-design for voice and
product-ui-design-architect for text rhythm, copy rules, and vault
integration.

Vault docs read: 02-website/current-site-state.md,
02-website/design-direction.md, 07-content-rules/public-copy-rules.md,
09-implementation-log/current-slice.md. Skill references applied:
references/text-rhythm.md, references/section-spacing.md,
references/vault-integration.md, references/lessons-learned.md.

Implemented changes (jera-site):

- src/pages/solution-examples/index.astro: compressed the hero intro, the
  CTA description, and five verbose pattern card descriptions.
- src/content/solution-examples/*.mdx: compressed all four solution
  example descriptions.
- src/pages/about.astro: compressed the page intro and the operating
  principles intro.
- src/pages/index.astro: updated the homepage Solution examples section
  intro to match the Solution Examples page.
- src/content/products/dai.mdx and matchup-analyzer.mdx: compressed the
  two product hero descriptions that the new advisory flagged.
- scripts/check-public-copy.mjs: added a warning-only advisory for long
  or comma-heavy prominent intros. It never fails the build.

Updated jera-vault:

- 07-content-rules/public-copy-rules.md: added a standing "Prominent
  Section Intro Rule".

Updated the skill:

- .claude/skills/product-ui-design-architect/references/lessons-learned.md:
  added the reusable lesson "Recurring awkward wrapping is an editorial
  systems issue".

No CSS, component, or layout changes. The measure tokens and section
rhythm from earlier passes were already correct; the fix was copy.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed; intro rhythm advisory reports all prominent
  intros concise.
- npm run preview served at http://localhost:4332/.
- Rendered QA at 390px, 768px, 1280px: Solution Examples detail intros
  one line each, About intros clean, product hero intros concise, no
  horizontal overflow, console clean.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff, native select popup, contact links, redirects,
  metadata, sitemap, and console output on the live preview.

## May 17 Inquiry Modal Polish Pass

Focused modal UX and copy rhythm pass using frontend-design for visual
judgment and product-ui-design-architect for modal and form quality,
text rhythm, and accessibility.

Vault docs read: 02-website/current-site-state.md,
02-website/design-direction.md, 07-content-rules/public-copy-rules.md,
09-implementation-log/current-slice.md. Skill references applied:
references/modal-and-form-quality.md, references/text-rhythm.md,
references/accessibility-checklist.md, references/vault-integration.md.

Implemented changes (jera-site):

- src/components/inquiry/InquiryModal.astro: new headline and intro copy,
  the "Send project details to:" fallback helper, two aria-hidden group
  labels (Contact details, Project details), and a send / paper-plane
  CTA icon replacing the checkmark.
- src/styles/global.css: reduced the modal headline scale to a
  modal-appropriate size, added the .inquiry-form__group-label style,
  replaced the action area hard top border with a soft faded hairline,
  removed the vertical divider on the direct email helper, and loosened
  footer spacing for desktop and mobile.

Updated the skill:

- references/lessons-learned.md: added three reusable lessons (a modal
  heading is not a page hero; soft hairlines over mechanical dividers;
  CTA icons should match the action's meaning).

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed; intro rhythm advisory clean.
- npm run preview served at http://localhost:4333/.
- Modal QA at 390, 430, 768, 1280, 1440 (x900): clean headline wrap,
  natural intro, correct message label, visible CTA, uncramped footer,
  clean direct email fallback, no right edge artifact, no horizontal
  overflow.
- Escape close and focus return verified. Console clean.

Remaining Vercel preview QA carried forward:

- Recheck the modal on the deployed preview at the same widths.
- Confirm the mailto handoff and the native select popup behavior.
- Smoke test contact links, redirects, metadata, sitemap, console.

## May 18 Inquiry Modal Intro Microcopy And Wrap Pass

A final microcopy and text rhythm refinement on the inquiry modal intro.
No redesign, no form structure change, no accessibility change, no
dependency change. Skills used: frontend-design for voice judgment,
product-ui-design-architect for text rhythm and modal quality.

Vault docs read: 02-website/current-site-state.md,
08-decisions/0006-inquiry-form-experience.md,
07-content-rules/public-copy-rules.md,
09-implementation-log/current-slice.md.

Copy change (src/components/inquiry/InquiryModal.astro):

- Intro from "Modernization effort, product concept, or strange little
  system problem? Send over the shape of it. Jera Technologies will help
  turn it into a practical next step." to "Modernization effort, product
  concept, or strange little system problem? Send the rough shape. We'll
  help turn it into a practical next step."
- Removing the literal "Jera Technologies" from the intro removes the
  company-name line break that read as unpolished, and "We'll" keeps the
  tone warm and down to earth.
- The headline "Rough idea or stubborn workflow?" is unchanged.

Wrap fix (src/styles/global.css):

- .inquiry-modal__description changed from text-wrap: pretty to
  text-wrap: balance. With pretty the intro still broke awkwardly at
  390px: the article "a" dangled at the end of a line, separated from
  "practical next step." pretty only optimizes the last few lines to
  avoid an orphan; it does not even the body of the paragraph. balance
  evens every line. The intro is only three to four lines, well inside
  the browser balancing cap.

Rendered QA (npm run preview, modal at x900):

- 390px: intro four even lines, the question ends cleanly at line 2, the
  second sentence is lines 3 and 4, no dangling article. Headline two
  lines. CTA and fallback email visible.
- 430px: same four-line shape, clean.
- 768px: intro three even lines, headline two lines, CTA and fallback
  visible.
- 1280px and 1440px: intro three even lines, no awkward break.
- No "Jera Technologies" company-name wrapping at any width.
- No horizontal overflow at any width. Escape close and focus return
  verified. Console errors and warnings 0.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed; intro rhythm advisory clean.

Skill update:

- product-ui-design-architect references/lessons-learned.md gained the
  lesson "For short prominent blocks, balance beats pretty".
- references/text-rhythm.md wrapping guidance updated: prefer
  text-wrap: balance for short prominent paragraphs (modal intros, hero
  subcopy), and a note that pretty is not a stronger balance.

## May 18 Inquiry Modal Intro Measure Composition Pass

A composition fix for the inquiry modal intro. The earlier microcopy and
wrap pass improved the intro but left it constrained too narrowly: the
intro was capped at max-inline-size: 50ch, far too tight for a
two-sentence intro, so it still rendered as cramped fragments. This pass
fixes the measure system, not the copy. The headline and intro copy are
both unchanged. No form structure, accessibility, or dependency change.

Skills used: frontend-design for voice and composition judgment,
product-ui-design-architect for modal quality and text rhythm.

Vault docs read: 02-website/current-site-state.md,
02-website/design-direction.md, 07-content-rules/public-copy-rules.md,
08-decisions/0006-inquiry-form-experience.md,
09-implementation-log/current-slice.md. Skill references read:
modal-and-form-quality.md, text-rhythm.md, lessons-learned.md,
vault-integration.md.

Root cause:

- .inquiry-modal__title and .inquiry-modal__description already had
  separate max-inline-size values (24ch and 50ch), but 50ch is a
  helper-text width, not an intro width. A roughly 138-character intro
  at 50ch wraps to three or four cramped fragments.
- The shared header wrapper .inquiry-modal__header also capped both the
  title and the intro at max-width: 43rem, a secondary ceiling.

Measure changes (src/styles/global.css):

- Added two named tokens so the separation is an explicit system:
  --measure-modal-heading: 24ch and --measure-modal-intro: 64ch.
- .inquiry-modal__title now uses var(--measure-modal-heading). The
  headline measure is unchanged in value (24ch), now named.
- .inquiry-modal__description now uses width: 100% and
  max-inline-size: var(--measure-modal-intro) (64ch, up from 50ch).
- .inquiry-modal__header max-width widened from 43rem to 46rem so the
  wider intro measure is never clipped by the header wrapper. The title
  keeps its own 24ch cap, so widening the wrapper does not affect it.
- The intro keeps text-wrap: balance. At the 64ch measure, balance lands
  the line break after the opening question ("...system problem?") and
  keeps the second sentence whole on line two. text-wrap: pretty was
  tested at the same measure and rejected: it greedily filled line one
  and stranded the verb "Send" at the end of it.

Rendered QA (npm run preview, modal at x900):

- 1280px: intro two lines. Line 1 "Modernization effort, product
  concept, or strange little system problem?" Line 2 "Send the rough
  shape. We'll help turn it into a practical next step." Matches the
  brief's QA target.
- 1440px: identical two-line composition.
- 768px: intro two lines, same break.
- 430px and 390px: intro four even lines, bounded by the panel width
  (the 64ch token does not bind at mobile), no cramped fragments.
- Headline stays a clean two lines ("Rough idea or" / "stubborn
  workflow?") at every width.
- CTA visible, footer and direct email readable, no horizontal overflow,
  no right edge artifact. Escape close and focus return to the trigger
  verified. Console errors and warnings 0.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed; intro rhythm advisory clean.

Skill update:

- references/lessons-learned.md gained "A modal heading and its intro
  need separate measures".
- references/modal-and-form-quality.md gained a "Text composition"
  section on separate heading and intro measures.
- references/text-rhythm.md measure guidance gained a note that a
  heading and its intro need separate measures even inside a modal.

Remaining Vercel preview QA carried forward:

- Recheck the modal on the deployed preview at 390, 430, 768, 1280, 1440.
- Confirm the mailto handoff and the native select popup behavior.
- Smoke test contact links, redirects, metadata, sitemap, console.
