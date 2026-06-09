# Current Site State

## Date

May 26, 2026

## Current Slice

Second principal-level design review of the homepage atmosphere. The viewport-anchored atmosphere system remains intact and the page reads coherent top to bottom. The one remaining issue — the top still reading slightly too white, most visible at narrow widths — was traced to the base field gradient carrying its warmest, palest stop at the very top while the cool soft-blue only arrived mid-viewport. The fix carried the cool soft-blue pearl up to the top stop (with a warm pearl note returning only at the footer), and cooled the html/overscroll colour and the sticky header tint to match, so the hero now sits in soft blue atmosphere instead of a flat warm white. No ambient-glow change and no section wash bands.

## May 26 Clean Pearl Base (corrects the warm pearl pass below)

The warm pearl restoration over-warmed into a cream/brown parchment cast
that read older and less premium. This pass moves the base to a clean,
near-white, faintly cool pearl; keeps blue only as barely-visible corner
ambient; and gives cards a directional, light-catching edge plus a
restrained iridescent sheen. Where it conflicts with the warm pearl pass
below, this wins.

What changed (`jera-site`):

- `src/styles/global.css`:
  - Body base → clean cool pearl `#fbfcfe 0% → #f5f8fc 52% → #f9fbfd 100%` (no warm/beige stops).
  - `--color-background` `#f7f5ef` → `#f6f8fb`; `--color-surface` `#fffdfa` → `#fcfdff`.
  - `body::before` ambient lowered to barely-visible soft blue corner light (blue `0.085`, cyan `0.055`, lavender `0.04`, navy floor `0.045`); no central haze.
  - `--color-card-edge` softened `rgba(86,132,184,0.22)` → `rgba(96,140,190,0.16)`; `--color-card-edge-strong` → `rgba(96,140,190,0.3)`.
  - `.soft-surface` reworked: crisp white interior, **directional** edge light (bright top-left inset rim, faint cool bottom-right inset), restrained aqua (TR) + lavender (BL) corner sheen, layered `--shadow-soft`.
- `src/components/layout/Header.astro`: header tint `rgba(247,245,239,0.82)` → `rgba(248,250,253,0.82)`.
- `src/components/seo/SEO.astro`: `theme-color` `#f7f5ef` → `#f6f8fb`.
- FeatureCard/ServiceCard/ProcessStep still use `--color-card-edge` (unchanged from prior pass). ProductCard/MetricCard keep `pearl-panel`+`iridescent-edge`. `technical-panel` dark anchors unchanged.

Why: warm off-white at field scale reads beige/parchment, not premium. Clean pearl base first; blue/cyan as edge light; iridescence as a material finish on select surfaces only.

Verification (rendered this pass):

- `npm run build` passed (9 pages); `npm run copy-check` passed, intro advisory clean.
- Browser QA at 1440px (hero, What Jera builds cards, Product lab), 390px (hero/nav), and Contact at 1440px: clean pearl base, no cream/brown cast, dark panels contrast cleanly, cards read as material with subtle edge light. Console 0 errors / 0 warnings. No horizontal overflow at 1440 (1425/1425) or 390 (375/375).

## May 26 Warm Pearl Restoration (corrects the stop-order pass below)

On review the stop-order pass read blue-washed: stacked on the May 21/22
ambient field it made the whole page blue and lost the warm pearl
identity. This pass restores warm pearl as the base and demotes blue to
soft corner ambient + premium card edge light. Where it conflicts with
the stop-order pass, this wins.

What changed (`jera-site`):

- `src/styles/global.css`:
  - `--color-background` back to warm `#f7f5ef`.
  - Body base field back to warm pearl `#faf8f3 0% → #f6f2e9 52% → #f7f5ef 100%` (no blue field).
  - `body::before` ambient demoted to soft blue *corner* light: blue top-left `0.10`, cyan top-right `0.07`, lavender mid-right `0.045`, navy floor `0.05`; the central blue haze radial (`46% 22%`) is removed.
  - Pearl tokens lowered to `aqua 0.10` / `lavender 0.07`.
  - New `--color-card-edge` (`rgba(86,132,184,0.22)`) and `--color-card-edge-strong`.
  - `.soft-surface` now: clean white interior (`#ffffff`), refined cool border (`--color-card-edge`), an inset white rim (`inset 0 0 0 1px rgba(255,255,255,0.55)`) so the edge catches light, plus the layered `--shadow-soft`.
- `src/components/layout/Header.astro`: header tint back to warm `rgba(247,245,239,0.82)`.
- `src/components/cards/FeatureCard.astro`, `ServiceCard.astro`, `ProcessStep.astro`: inline border token switched from `--color-border` to `--color-card-edge` so the premium edge is not overridden.
- ProductCard and MetricCard keep `pearl-panel` + `iridescent-edge` (iridescent material is theirs); no change.

Why:

- Warm pearl is Jera's material identity; blue is an accent. Premium depth comes from surface design (card edges, layered shadows, iridescent finish on select cards) and soft corner ambient, not from washing the field blue.

Verification status:

- `npm run build` passed (9 static pages). `npm run copy-check` passed; intro rhythm advisory clean.
- Rendered browser QA at 1440/1150/390 and overflow/console checks were NOT completed this pass (dev-server review was interrupted). Pending before sign-off: confirm warm pearl reads correctly, cards show the premium edge, no horizontal overflow at 390px, console clean, and Products/Contact coherence.

## May 26 Base Field Stop-Order Correction

This pass was a focused colour-order correction surfaced by rendered QA, not a redesign.

What changed:

- `src/styles/global.css`:
  - `--color-background` cooled from `#f7f5ef` to `#edf0f6` (html/overscroll backing).
  - Body base field gradient changed from `#efede7 0% → #e9edf5 46% → #edf0f6 70% → #efede7 100%` to `#e9edf5 0% → #e7ebf3 42% → #edf0f6 72% → #f1efe9 100%` so the soft blue-white owns the top and warmth returns only at the footer close.
- `src/components/layout/Header.astro`: sticky header tint cooled from `rgba(247,245,239,0.78)` to `rgba(237,240,246,0.78)` so the header strip matches the cooled top.
- `body::before` / `body::after` viewport-anchored ambient layers untouched. No section wash bands. No layout, spacing, copy, or component-logic changes (colour values only).

Why:

- The hero, where the brand wants soft blue atmosphere and navy anchors, was the palest/warmest point of the page. On narrow viewports the rem-anchored corner glows under-cover the hero, so the warm base field showed through as a flat marketing-white fold. Fixing the stop order at the shared base-field primitive resolves it globally without touching the working atmosphere model.

Validation:

- Homepage reviewed before/after at 1440px (hero, seam into What Jera builds, Product lab, dark decision panel, CTA/footer), 1150px (hero), and 390px (hero/nav, deep section).
- Products page reviewed at 1440px and 390px as a coherence cross-check.
- No console errors or warnings; no horizontal overflow at 1440px (1425/1425), 1150px (1135/1135), or 390px (375/375) on home and products.
- `npm run build` passed (9 static pages). `npm run copy-check` passed; intro rhythm advisory clean.

## May 22 Atmosphere Depth Rebalance

This pass was a focused correction from rendered QA, not a redesign.

What changed:

- `src/styles/global.css` now uses a slightly cooler, more even base field gradient.
- `body::before` ambient glows were rebalanced globally:
  - stronger blue top-left glow,
  - stronger cyan top-right glow,
  - a subtle central blue haze to carry atmosphere through the hero/content seam,
  - a slightly clearer lavender mid-right note,
  - slightly reduced navy floor opacity to keep the lower page calm.
- No section-local wash bands were added.
- No section structure, card layout, copy, or component logic was changed.

Why:

- The prior composition was coherent but still a little pale at the top compared to the richer middle/lower composition.
- The fix needed to happen at shared atmosphere primitives, not per-section styling, to preserve the global composition model.

Validation:

- Homepage reviewed at wide desktop, 1150px, and 390px.
- Products page reviewed at desktop and mobile as a coherence cross-check.
- Playwright console/overflow probe:
  - home 1600px: no console warnings/errors, no horizontal overflow.
  - home 1150px: no console warnings/errors, no horizontal overflow.
  - home 390px: no console warnings/errors, no horizontal overflow.
  - products 390px: no console warnings/errors, no horizontal overflow.
- `npm run build` passed (9 static pages).
- `npm run copy-check` passed.

## Implemented Stack

- Astro
- TypeScript
- Tailwind CSS 4 through `@tailwindcss/vite`
- MDX
- Astro content collections
- `@astrojs/sitemap`

## Implemented Pages

- Home
- Services
- Products
- Structured Analysis Pipeline
- Matchup Analyzer
- Solution Examples
- About
- Contact

## Implemented Components

- Header
- Footer
- SEO
- HeroSection
- SectionShell
- FeatureCard
- ProductCard
- ServiceCard
- MetricCard
- ProcessStep
- CTASection
- DarkProductPanel
- InquiryModal

## Current Design State

The site uses the Luminous Technical visual system. The current refinement keeps the warm light base, dark product panels, restrained blue and cyan accents, corner anchored glows, and structured enterprise presentation.

This slice tightened the homepage hero headline, reduced header crowding at tablet widths, wrapped mobile navigation instead of allowing horizontal overflow, and made small screen buttons fill the available width.

Contact behavior remains static and launch ready. Project CTAs use a lightweight vanilla JavaScript inquiry modal when JavaScript is available, while retaining `/contact` and mailto fallbacks. The modal opens a mailto draft instead of pretending to submit to a backend.

The header subtitle now reads `Practical AI & Software Engineering`. The subtitle is visible under the Jera Technologies brand mark and uses a mobile-safe wrap measure so it can resolve cleanly on narrow screens.

The About page no longer includes internal positioning language about public credibility, recruiters, future consulting prospects, or broad client-specific work. The operating principles now describe practical software delivery, structured AI workflows, modernization work that respects existing systems, and product-minded delivery in public-facing language.

The public-facing copy sweep found and removed the remaining internal About sentence, replaced a public `client's system` service phrase with `existing system`, and changed `internal workflow` in product CTA copy to `operational workflow`.

The inquiry modal was simplified and refined. It now uses one project category dropdown, name, email, company, and message fields. The final title is `Rough idea, stubborn workflow, or modernization effort?`, the intro is `Send over the shape of it, even if it is still messy. Jera Technologies will help turn it into a practical next step.`, the primary CTA is `Send inquiry`, and the fallback remains a direct email path.

The May 15 inquiry modal polish pass fixed the odd right edge artifact by softening the modal-specific iridescent overlay and removing the always reserved scrollbar gutter. The panel keeps the pearl/glass feel without showing a duplicate right-side line.

The final inquiry category labels are `Applied AI`, `Enterprise Modernization`, `Workflow Automation`, `Architecture & Integration`, `Decision Support Systems`, `Product Strategy`, and `Not Sure Yet`.

The fallback email copy now reads `Prefer a direct email?` followed by `Send a short note to:`. The fallback email remains `support@jeratechnologies.com`.

The modal headline uses balanced wrapping and the intro plus email helper use prettier wrapping where supported. The footer now uses a clearer action hierarchy: the primary CTA sits on the left at desktop widths, the direct email helper sits on the right, and the footer stacks cleanly on mobile with a subtle divider. The native select remains in place for accessibility, with a calmer closed state, visible focus ring, and aligned chevron. The open dropdown list remains browser and OS controlled, so it was not replaced with a custom dropdown for launch.

The mobile header now uses an explicit desktop CTA display rule so the large `Discuss a project` button cannot appear below wide desktop. Mobile and narrow tablet users see readable branding and wrapped navigation chips with Contact emphasized.

The footer email link can wrap safely on very narrow screens, and the bottom footer text has sensible max widths.

This slice added route driven active navigation. Header links now use the current Astro pathname to set the active state, including nested product routes. Active, hover, and focus visible styles are separated so a clicked link does not remain visually selected after the route changes.

Responsive spacing was tightened across mobile cards, CTA panels, and solution example content. Mobile heading scales now use more deliberate clamps so narrow pages avoid awkward word stacking while keeping a premium tone.

The current slice separates page hero typography from standard section intro typography. Page level headings now use a wider `page-heading` treatment and semantic `h1` output through `SectionShell`, while normal section headings keep the more compact `section-title` rhythm.

The Services page heading now renders as a deliberate two to three line desktop composition rather than a narrow stacked column. Mobile heading scale was reduced so long page titles remain readable on narrow screens.

This slice further reduced the hero, page, panel, and section heading scale so the site reads as more premium and less heavy. Major public headings now avoid terminal periods when they function as title statements. The global font stack uses native system UI fonts with Apple system fonts first where available, without importing or bundling external font files.

The narrow mobile nav now uses an intentional two column chip grid with Contact spanning the full width. Active nav state and `aria-current="page"` remain route driven.

The mature product surface pass refined the site toward a quieter, more editorial version of Luminous Technical. Bright cyan and electric blue usage was reduced across labels, cards, panels, and hero artifact details. Stronger blue is now reserved for active navigation, focus states, small signal dots, and restrained highlights.

Product cards now read more like product surfaces than generic content cards. They use a muted category pill, clear product title, short description, concise capability points, and a consistent CTA rhythm. The Products page hero now uses the headline `Structured software products for clearer decisions` to communicate product discipline without implying client work or exposing internal method details.

Dark product panels keep the deep navy direction, but their label treatment, internal spacing, gradients, and capability cards are calmer and more integrated with the rest of the site.

No framework island was added in this slice. The site remains static and launch ready, with only minimal vanilla JavaScript for the inquiry modal. A future Capability Explorer may be considered after preview feedback if it helps visitors understand service fit without adding unnecessary interaction.

The Enterprise Modernization service copy was refined so it is more technically credible without sounding tied to a single stack. Public copy now emphasizes existing application improvement, stronger application architecture, improved backend architecture, cleaner frontend patterns, integration flows, authentication and access patterns, business logic preservation, workflow modernization, and systems that are easier to maintain and extend.

The homepage and related public copy were polished to reduce stiff phrasing. The product portfolio section now uses `Jera built products with clear engineering direction`, with supporting copy that explains how Jera turns complex workflows into structured software, reviewable outputs, and business facing experiences. Similar wording updates were made across service previews, product pages, and solution examples to keep copy concise, natural, and less clunky.

The homepage hero H1 was reduced slightly and widened so it balances better against the following section heading. The hero visual artifact uses `Structured Delivery System` and separates the status pill from the card heading so the title does not wrap awkwardly.

The repeated solution tile description was replaced with specific pattern descriptions for source context, data intake, authentication, access, API integration, operational documentation, application structure, business logic preservation, and incremental modernization. Service outcome cards now also use specific descriptions instead of repeated filler copy.

The Vercel readiness pass confirmed the site remains static, buildable, and ready for preview deployment. Generated route files exist for all public routes, production metadata uses `https://jeratechnologies.com`, the sitemap excludes the retired DAI route, and contact links use `support@jeratechnologies.com`.

During responsive smoke testing, the homepage mobile hero showed an overflow risk caused by the hero grid relying on implicit mobile grid columns. The hero grid now explicitly uses one mobile column and `min-w-0` on both hero columns so the H1, body copy, and `Structured Delivery System` artifact surface have stable mobile wrapping.

The appearance refinement pass tightened the site rhythm before preview. `SectionShell` now supports explicit spacing variants so page heroes, standard sections, compact sections, and tight follow-on sections can use deliberate vertical rhythm instead of repeating one large padding value everywhere.

The Services page overview and detailed service panels now live in one connected section. The overview cards use a balanced desktop grid with the final two cards centered, and the first Applied AI detail panel follows the overview at a controlled distance instead of after a disconnected empty band.

Card and panel surfaces were refined across Services, Products, Solution Examples, About, and Contact. Card padding is slightly tighter, internal dividers sit closer to content, CTA spacing is less oversized, dark product panels use calmer internal spacing, and labels now lean more slate than bright cyan.

The homepage hero H1 was reduced slightly again, the hero pair now top-aligns on desktop, and the desktop hero padding was trimmed so the first viewport feels more intentional. Page hero padding was also reduced so route introductions start sooner while preserving the premium Luminous Technical feel.

The footer and CTA section spacing were tightened. Footer labels now use muted slate rather than bright blue, and the contact email remains safe to wrap on narrow widths.

The component display polish pass fixed loose decorative dots on product and card labels. Product card metadata no longer uses a separated right-edge dot. Cards and dark panels now use a shared `surface-label` treatment with an inline signal dot, muted border, soft translucent background, and restrained slate text.

Text measure is now separated by context. Page headings and hero copy use wider desktop measures than card copy, section introductions support broader readable lines, and card descriptions stay compact. Major headings continue to use balanced wrapping, while paragraphs use prettier wrapping where supported.

A reusable `pearl-surface` utility now provides a subtle premium surface treatment with warm off white, pale blue white, silver, and very low opacity aqua or lavender corner light. The effect is static, readable, and applied selectively to customer facing cards and detail panels.

Card and panel responsiveness now includes simple component container queries for product, service, and feature cards. These adjust label density, heading scale, and card copy measure based on available component width rather than only viewport width.

The Services page spacing remains connected after the component pass. The overview grid continues to flow into the Applied AI detail panel with measured spacing instead of a disconnected empty band.

## Current Positioning Reflected

The site positions Jera Technologies as a software engineering services company that builds practical AI enabled products, automation systems, enterprise modernization solutions, and decision support applications.

The DAI product direction is softened publicly as the Structured Analysis Pipeline. The public page uses `/products/structured-analysis-pipeline/` and describes the product as a reviewable analysis system rather than leading with the internal DAI name.

The Matchup Analyzer is positioned as a Jera built decision support application for structured sports matchup analysis.

## Current Build State

Build passes with the project npm build script:

`npm run build`

The public copy exposure check also passes:

`npm run copy-check`

The May 15 inquiry modal validation confirmed:

- `npm run build` passes and produces 9 static pages.
- `npm run copy-check` passes across 9 generated HTML files.
- Generated output and public site source no longer include the retired service label, retired engineering variant, typo contact email, or retired fallback helper wording.
- Preview QA checked the modal at 390px by 900px, 768px by 900px, and 1280px by 900px.
- The modal has no horizontal overflow at the checked sizes.
- The primary CTA and direct email fallback are visible at 390px by 900px.
- Escape close, outside click close, focus return, and native invalid form behavior remain intact.

The generated HTML was checked for public exposure of `DAI`, retrieval, evaluation, synthesis, betting model, prediction engine, guaranteed picks, profit, private scoring rules, internal prompt logic, and cognitive architecture language. No matches remain in generated HTML.

Sitemap generation now uses `https://jeratechnologies.com` and excludes the retired `/products/dai/` fallback route.

Contact email is now `support@jeratechnologies.com`.

The contact mailto subject is `Project Conversation with Jera Technologies`.

Route validation confirms:

- Home has no active nav item.
- Services highlights Services.
- Products and product detail routes highlight Products.
- Solution Examples highlights Solution Examples.
- About highlights About.
- Contact highlights Contact.
- `/products/dai/` continues to redirect to `/products/structured-analysis-pipeline/`.
- Vercel has permanent redirects configured for both `/products/dai` and `/products/dai/`.

Current route review confirms each public page exposes one main page heading:

- Home.
- Services.
- Products.
- Structured Analysis Pipeline.
- Matchup Analyzer.
- Solution Examples.
- About.
- Contact.

Generated heading validation confirms no terminal periods remain in public `h1`, `h2`, or `h3` headings.

The mature surface pass confirmed:

- Products page active navigation highlights Products.
- Services page active navigation highlights Services.
- Header and mobile navigation remain stable after visual refinements.
- Public HTML does not expose restricted internal product terms.
- Contact email remains `support@jeratechnologies.com`.

The appearance refinement QA confirmed:

- Responsive checks covered `/`, `/services/`, `/products/`, `/products/structured-analysis-pipeline/`, `/products/matchup-analyzer/`, `/solution-examples/`, `/about/`, and `/contact/`.
- Widths checked were 360, 390, 430, 768, 1024, 1280, and 1440.
- No horizontal overflow was detected.
- Header layout remains stable.
- Active navigation remains correct on all non-home routes.
- Footer wrapping and the contact email remain safe.
- Services overview to detail spacing measures approximately 32px on narrow mobile, 36px at 768px, and 40px from 1024px through 1440px.

The component display polish QA confirmed:

- Responsive checks covered `/`, `/services/`, `/products/`, `/products/structured-analysis-pipeline/`, `/products/matchup-analyzer/`, `/solution-examples/`, `/about/`, and `/contact/`.
- Widths checked were 360, 390, 430, 768, 1024, 1280, and 1440.
- No horizontal overflow was detected.
- Header layout remains stable and active navigation remains route correct.
- Product and card label dots are integrated inside label treatments and no longer float at card edges.
- Hero and page intro copy use wider desktop measures.
- Services overview to detail spacing still measures approximately 32px on mobile, 36px at 768px, and 40px from 1024px through 1440px.
- Footer wrapping and the contact email remain safe.
- In-app browser spot checks loaded Services and Products with no console errors.

The final build and copy checks for this pass confirmed:

- `npm run build` passes and produces 9 static pages.
- `npm run copy-check` passes across generated HTML.
- A generated HTML exposure search found no matches for retired placeholder emails, placeholder domains, `DAI`, retrieval, evaluation, synthesis, betting model, prediction engine, or profit language.

The May 14 public copy and inquiry pass confirmed:

- `npm run build` passes and produces 9 static pages.
- `npm run copy-check` passes across 9 generated HTML files.
- Generated HTML contains `Practical AI & Software Engineering`, `Tell us what you are trying to build`, project category, company, and `Send inquiry`.
- Generated HTML has no matches for the targeted internal public copy terms: `Applied software engineering`, `public positioning`, `recruiters`, `future consulting prospects`, `built to feel credible`, `broad enough`, `showcase`, `lab`, `fake agency`, `client's system`, or `internal workflow`.

The May 14 responsive UI refinement addendum confirmed:

- Header navigation now uses slightly tighter tablet spacing while preserving the `Practical AI & Software Engineering` subtitle and the wide desktop CTA.
- Mobile page and section heading measures were widened slightly so long headings wrap more naturally without manual line breaks.
- Services and Solution Examples detail panels now use a shared `detail-panel` pattern. Each panel gives the summary copy a readable measure, then lays outcome cards across the available panel width instead of squeezing them into narrow side columns.
- The inquiry modal panel is wider on desktop, more compact vertically, and uses `100dvh` sizing so the CTA and fallback email stay reachable on mobile and desktop.
- Inquiry triggers are handled through document level event delegation so future project CTAs can open the same modal without adding new listener code.
- The mailto draft now checks native form validity and sanitizes one line fields before building the email body.
- Responsive route QA covered Home, About, Services, Products, Solution Examples, Contact, Structured Analysis Pipeline, and Matchup Analyzer at 390px, 768px, and 1280px.
- No horizontal overflow was detected on any checked route or width.
- Modal QA confirmed the inquiry panel fits at 390px by 900px and 1280px by 900px, focuses the project category field on open, and keeps the primary CTA visible.
- Built output was served with `npm run preview` and rechecked at 390px, 768px, and 1280px across the same public routes.
- Preview modal QA confirmed the project category focus target, panel fit, and visible action row at 390px and 1280px.
- `npm run build` passes and produces 9 static pages.
- `npm run copy-check` passes across 9 generated HTML files.
- Generated HTML source checks have no matches for the targeted internal copy terms or restricted product exposure terms.

The Vercel readiness pass confirmed:

- Generated route files exist for Home, Services, Products, Structured Analysis Pipeline, Matchup Analyzer, Solution Examples, About, and Contact.
- Canonical URLs use `https://jeratechnologies.com`.
- Open Graph metadata exists.
- Twitter metadata exists.
- Theme color is set.
- Placeholder social image output exists at `/social-card.svg`.
- `vercel.json` contains permanent redirects for the retired DAI route.
- Generated HTML does not contain retired placeholder emails, restricted public terms, or named stack narrowing.

## May 15 Premium Design Architecture Pass

This pass refined the Luminous Technical system into a more cohesive, intentional, and product quality presentation without redesigning the site, adding dependencies, or changing the underlying positioning.

Global system refinements:

- Reorganized CSS tokens into named groups for text, brand anchors, pearl detail, hairlines/borders, elevation, radii, and layout.
- Introduced a three step elevation scale (`--shadow-soft`, `--shadow-card`, `--shadow-lift`) with consistent inset highlights and softer outer shadows, plus a dedicated `--shadow-dark` for technical panels.
- Added `--color-border-soft` and `--color-border-strong` tokens so hairlines and dividers can vary without ad hoc rgba values.
- Standardized focus visible styling to a 2px ring at `rgba(45,97,183,0.55)` with a 3px offset, applied through `:focus-visible`, buttons, and inquiry inputs.
- Refined the body background with an added subtle lavender bottom left glow so corner anchors balance rather than crowd one side.
- Added a `.hairline` and `.hairline--dark` utility for inline soft dividers used in cards and footers.
- Added a `.tabular-nums` utility for numbered step counters and metric values.

Typography refinements:

- Added `font-feature-settings: "ss01", "cv11", "kern"` and `font-optical-sizing: auto` on the body for slightly tighter, more refined renderings on supported platforms.
- Applied slight negative letter spacing on display headings: page heading (-0.016em), section title (-0.012em), panel heading (-0.014em), card heading (-0.008em), and the homepage H1 (-0.02em).
- Tightened the eyebrow letter spacing to 0.04em and surface labels to 0.06em so small uppercase metadata feels deliberate.
- Refined the inquiry modal title scale (clamp 2rem to 2.78rem) with -0.018em tracking so the long question headline lands as a more confident statement.

Surface refinements:

- Iridescent edge treatment now uses softer right and bottom border opacities so the right edge cannot read as a second line, particularly on the inquiry modal panel. The modal panel explicitly opts out of `iridescent-edge::after` to remove any chance of a duplicated edge artifact next to the scrollbar gutter.
- Pearl panel, pearl surface, and soft surface gradients were rebalanced toward warmer off white anchors with slightly more restrained aqua and lavender corner light.
- Technical panel gradient picked up a quiet lavender corner light so dark product panels feel a touch more iridescent without becoming flashy.
- `subtle-lift` now uses a custom cubic bezier for a calmer rise and applies `--shadow-lift` plus a softer blue border on hover.

Button refinements:

- Primary button uses a deeper vertical gradient with inset highlight and shadow, plus a hover elevation that strengthens the shadow without changing color.
- Secondary button now layers a soft inset highlight, a calm hairline border, and a small drop shadow so it reads as a real product surface in light mode.
- Dark button uses a soft inset highlight and a darker outer shadow so it sits naturally on technical panels.
- All buttons gained a slight letter spacing tightening and a `:active` settle.

Header and footer refinements:

- The JT brand mark now uses a subtle radial inner highlight on top of the deep navy ground so the lockup feels more premium without bringing back bright cyan.
- Brand text uses tighter letter spacing for the wordmark and a slightly larger subtitle measure (`max-w-[12.25rem]`) so `Practical AI & Software Engineering` resolves into a more deliberate two line wrap on mobile.
- Active navigation chips now use a slightly stronger blue accent border (`rgba(45,97,183,0.32)`) and a calmer translucent fill (`rgba(45,97,183,0.08)`) so the active state reads clearly without competing with the brand mark.
- Footer adds a top hairline that softly fades on both ends, picks up the same JT mark treatment, and uses tighter heading uppercase tracking (0.08em).

Hero refinements:

- Hero composition now anchors three corner glows (blue top right, blue muted bottom left, lavender mid right) so the page feels atmospheric without using busy decoration.
- Added a small focus / approach / output tabular trust strip below the hero CTAs so the first viewport carries a quiet structural statement.
- Hero artifact tiles now show an inset bordered step counter using tabular numerals, a softer hover, and a calmer artifact title color.

Card refinements:

- Feature, Service, and Process cards now carry a top inline hairline that anchors the card's visual weight at the top edge without adding a heavy border.
- Product card metadata bar uses the shared `surface-label` only and removes any decorative dot drift toward the card edge.
- Metric card scaled down its value type (1.7rem mobile, 2rem desktop) with text balance so longer values like `Applied AI` and `Structured` resolve cleanly.
- Process step gained a number to hairline lead in so the step counter sits on a connected line rather than floating alone.
- Dark product panel reworks each capability tile with a `01 / 02 / 03 — Capability` lead in so the dark panel reads as a designed capability grid rather than uniform pill text.

Inquiry modal refinements:

- Exact requested copy applied: eyebrow `Project Inquiry`, headline `Rough idea, stubborn workflow, or modernization effort?`, intro `Send over the shape of it, even if it is still messy. Jera Technologies will help turn it into a practical next step.`, message label `What needs attention?`, placeholder `What's the situation?`, fallback heading `Prefer a direct email?`, helper `Send a short note to:`, and contact email `support@jeratechnologies.com`.
- The right edge double line artifact was fully resolved by disabling the modal panel's iridescent overlay (`.inquiry-modal__panel.iridescent-edge::after { display: none }`), so the panel's own border, inset highlight, and pearl gradient carry the polish.
- Modal headline uses `text-wrap: balance`; the intro, fallback note, and email line use `text-wrap: pretty` for cleaner desktop and mobile wraps.
- Modal panel uses a calm fade plus a soft 240ms rise animation so it lands like a small product surface, and the animation is suppressed under `prefers-reduced-motion`.
- The close button now uses a real SVG cross icon and a calmer hover state. It sits at a slightly smaller tap target (2.5rem desktop, 2.15rem mobile) to feel less heavy at the top right.
- The send inquiry button switched to a clean check icon to reinforce that submission opens an email draft, not a backend submit.
- Native select is preserved with a calmer focus ring and the same chevron and grid mark icons.
- Submit handler now uses `checkValidity` before `reportValidity`, so the native invalid focus path is retained while keeping `novalidate` on the form for finer control.
- Document level inquiry trigger delegation, Escape close, outside click close, focus return, focus trap, and the prepared mailto behavior were preserved.

Page level polish:

- Homepage product portfolio eyebrow renamed from `Product portfolio` to `Product lab`, matching the brand direction of describing the surfaced work as Jera built products and product lab work.
- Services and Solution Examples detail panel headings switched from non semantic `font-[720]` to standard `font-[700]` with -0.014em tracking and a slightly more readable body measure.
- About replaced the awkward `Focus / AI` and `Approach / Build` metric values with `Focus / Applied AI` and `Method / Structured`, with refined supporting copy.

Accessibility:

- Focus visible ring is now consistent across navigation, buttons, form fields, and links.
- Reduced motion preference cancels all transitions and animations including the modal entrance.
- All decorative gradients, glows, and divider strokes carry `aria-hidden`.
- Active navigation continues to expose `aria-current="page"`.
- Modal preserves `role="dialog"`, `aria-modal="true"`, labelled by the title, described by the intro, Escape close, outside click close, focus return, focus trap, visible focus states, and a labeled close button with an inline SVG cross.
- Touch targets on mobile remain above 40px for nav chips, buttons, and the modal close.

Astro and component decisions:

- No framework island, animation library, or runtime dependency was added.
- Shared button, surface label, pearl panel, iridescent edge, soft surface, hairline, and tabular numerals were used across components rather than scattered one-off hacks.
- The `check-public-copy.mjs` script gained additional restricted terms (`public positioning`, `recruiters`, `future consulting prospects`, `built to feel credible`, `broad enough`, `fake agency`, `AI Application Engineering`, `Applied AI Engineering`, `jerattechnologies.com`, `client's system`, `internal workflow`).

Validation:

- `npm run build` passes and produces 9 static pages.
- `npm run copy-check` passes across 9 generated HTML files including the expanded restricted term list.
- Local `npm run preview` served the build at `http://localhost:4322/`.
- Home, Services, Products, Structured Analysis Pipeline, Matchup Analyzer, Solution Examples, About, and Contact returned 200 on the preview server.
- The inquiry modal was rechecked at 390px x 900px, 768px x 900px, and 1280px x 900px. The headline wraps cleanly, the CTA and fallback email remain visible at every size, no right edge artifact remains, and no horizontal overflow was detected.
- Console errors and warnings were both 0 across the previewed routes.

Remaining Vercel preview QA:

- Deploy a Vercel preview and recheck the same widths and modal sizes against the live URL.
- Confirm the mailto handoff opens the expected mail client from the live preview.
- Confirm the native select popup appearance in the target browsers.
- Recheck contact links, redirects, metadata, sitemap, and console output on the deployed preview.

## Launch Review Needed

- Deploy a Vercel preview and smoke test the live preview URL.
- Recheck the inquiry modal on the Vercel preview at 390px, 768px, and 1280px widths.
- Confirm the native select open dropdown appearance in target browsers, accepting that the popup list is browser and OS controlled.
- Confirm the mailto handoff opens the expected email client or browser handler from the live preview.
- Add real product screenshots or interface previews when available.
- Replace the placeholder social sharing image with a final brand approved image when available.
- Add a real contact form in a later slice if needed.

## May 12 UI/UX Polish Pass

This pass refined customer-facing composition rather than rebuilding the site.

Implemented refinements:

- Homepage hero headline now reads `Practical software for structured AI workflows`.
- The workflow model heading now reads `A practical path from idea to usable software`, reducing stacked desktop rhythm.
- Page, section, intro, panel, and card measures were widened or separated so broad positioning copy no longer wraps like narrow card text.
- Paragraphs and headings continue to use `text-wrap: pretty` and `text-wrap: balance` where appropriate.
- Footer brand copy was rewritten to feel cleaner and warmer under the logo.
- About copy is now company-first: the public page says Jera Technologies is led with a focus on practical software, structured workflows, and product-minded engineering.
- `Authentication And Integration Work` is now `Authentication & Integration Work`.
- `Automation And Integration` is now `Automation & Integration`.
- Pearl surface utilities were split into calmer `soft-surface`, selected `pearl-panel`, `iridescent-edge`, and `soft-surface-glow` treatments.
- The pearl effect remains static, restrained, low opacity, and used primarily on product cards, solution/service detail panels, CTA panels, product panels, and the inquiry modal.

Inquiry experience:

- `Discuss a project`, `Contact Jera Technologies`, and matching project CTAs open an accessible inquiry modal when JavaScript is available.
- The modal includes project category, name, email, company, and message fields.
- Submission opens a mailto draft to `support@jeratechnologies.com` with the selected fields in the email body.
- The modal supports Escape close, click-outside close, close button, focus return, and a visible fallback email link.
- No backend form service was added.

Responsive QA:

- Checked `/`, `/services/`, `/products/`, `/products/structured-analysis-pipeline/`, `/products/matchup-analyzer/`, `/solution-examples/`, `/about/`, and `/contact`.
- Checked 360, 390, 430, 768, 1024, 1280, and 1440 widths.
- Automated responsive QA ran 58 checks with 0 failures.
- No horizontal scrolling was detected.
- Header remained stable.
- Active navigation remained correct.
- Footer and contact email wrapping remained clean.
- Inquiry modal passed mobile and desktop checks, including field count, fallback mailto, Escape close, and no horizontal overflow.

Build and copy check:

- `npm run build` passes and generates 9 static pages.
- `npm run copy-check` passes across generated HTML.
- Generated HTML search found no matches for retired placeholder emails, placeholder domains, `DAI`, retrieval, evaluation, synthesis, betting model, prediction engine, profit, `Malcolm leads`, or `Authentication And Integration Work`.

Preview recommendation:

- The site is ready for Vercel preview.
- Remaining launch items are Vercel preview deployment, live preview smoke testing, final social image, and approved product screenshots or interface previews when available.

## May 15 Text Composition Pass

This pass focused only on how text sits on the page across the public site. The premium visual system, brand direction, and inquiry behavior were unchanged.

Root cause identified:

- Section and page intro paragraphs were running at `max-width: 62rem` and `max-width: 64rem`, roughly 992px and 1024px of measure. At typical body font sizes that is 80 to 95 characters per line, which is well past the comfortable 50 to 65 character reading range and produced the stretched, awkward break patterns described in the brief (for example, the homepage `Software systems for structured work` intro).

Shared measure system introduced in `src/styles/global.css`:

- New character based tokens on `:root`: `--measure-display`, `--measure-page-heading`, `--measure-section-heading`, `--measure-panel-heading`, `--measure-card-heading`, `--measure-lead`, `--measure-intro`, `--measure-copy`, `--measure-panel`, `--measure-card`, `--measure-helper`, `--measure-footer`, `--measure-legal`, `--measure-tagline`.
- New utility classes mapped to those tokens: `.measure-display`, `.measure-heading`, `.measure-page-heading`, `.measure-panel-heading`, `.measure-card-title`, `.measure-lead`, `.measure-intro`, `.measure-copy`, `.measure-panel`, `.measure-card`, `.measure-helper`, `.measure-footer`, `.measure-legal`, `.measure-tagline`, plus `.balance-text` and `.pretty-text`.
- All measure values are expressed in `ch` so they scale with the rendered font, applied through `max-inline-size` rather than `max-width` to respect logical writing modes.
- All copy classes now set `hyphens: none` and use `overflow-wrap: break-word` on headings so long words still break gracefully if needed but the default flow does not split words.

Existing measure classes were refactored to point at the new tokens instead of large rem values:

- `.section-copy` and `.section-copy-measure`: 62rem to `var(--measure-intro)` (56ch).
- `.page-copy` and `.page-copy-measure`: 64rem to `var(--measure-intro)` (56ch).
- `.hero-copy-measure`: 46rem to `var(--measure-lead)` (50ch).
- `.panel-copy-measure`: 44rem to `var(--measure-panel)` (52ch).
- `.card-copy-measure`: 34rem to `var(--measure-card)` (38ch).
- `.copy-measure`: 38rem to `var(--measure-copy)` (60ch).
- `.section-title`: 27ch to `var(--measure-section-heading)` (24ch).
- `.page-heading`: 32ch to `var(--measure-page-heading)` (24ch).
- `.panel-heading`: removed the default max-inline-size; consumers explicitly apply `.measure-panel-heading` (28ch) where they need a deliberate two line wrap.
- `.card-heading`: removed the default max-inline-size; card containers already constrain card titles.

Heading and intro improvements applied to components and pages:

- Hero copy moved from `hero-copy-measure` to `measure-lead pretty-text` plus a small font size refinement.
- Hero workflow artifact heading switched from `max-w-[20rem]` to `max-w-[20ch]` so the dark artifact title scales with the artifact's font.
- CTA section panel heading now uses `panel-heading measure-panel-heading` for a deliberate 2 line composition. Description scaled down a touch and uses `pretty-text`.
- Dark product panel heading and description follow the same pattern.
- About, Contact, Structured Analysis Pipeline, and Matchup Analyzer dark intro panels apply `panel-heading measure-panel-heading` and `panel-copy-measure pretty-text`.
- Services and Solution Examples detail panel headings now use `measure-section-heading` plus `text-balance` and their intro paragraphs use `measure-intro pretty-text` with consistent 1.02rem leading.

Footer composition:

- Brand descriptive paragraph: `max-w-[32rem]` to `measure-footer pretty-text` (38ch).
- Bottom row copyright now uses `measure-legal pretty-text` (44ch).
- Bottom row tagline now uses `measure-tagline pretty-text` (38ch).
- Contact email link continues to wrap safely at narrow widths via `break-all` on mobile and `whitespace-nowrap` from large desktop up.

Inquiry modal composition:

- Title: `max-width: 30ch` to `max-inline-size: 26ch` with `overflow-wrap: break-word`. Balanced wrapping preserved.
- Description: `max-width: 54ch` to `max-inline-size: 50ch`.
- Fallback helper block: `max-width: 28rem` to `max-inline-size: var(--measure-helper)` (34ch).
- All other modal behavior, copy, dialog semantics, focus handling, and mailto behavior were preserved.

Validation:

- `npm run build` passed and produced 9 static pages.
- `npm run copy-check` passed across 9 generated HTML files.
- `npm run preview` served the build at `http://localhost:4323/`.
- Home, Services, Products, Structured Analysis Pipeline, Matchup Analyzer, Solution Examples, About, and Contact were inspected at 390px, 768px, 1280px, and 1440px.
- Measure spot checks at 1440px: section intros render at approximately 522px (the 56ch token), section titles at approximately 487px (24ch), the homepage hero H1 at approximately 607px under its inline 22ch cap, and the CTA panel heading at approximately 638px wrapping to 2 balanced lines. The previously stretched homepage section intro `Jera Technologies focuses on products and business systems that make complex workflows easier to operate, inspect, and improve.` now wraps to 2 lines instead of running edge to edge.
- The inquiry modal was rechecked at 390x900 and 1280x900. Title wraps balanced, intro wraps to a pretty 3 line shape, the CTA and the fallback email remain visible at every checked size, and there is no right edge artifact.
- No horizontal overflow was detected at any tested width.
- Console errors and warnings were both 0 across the previewed routes.

Remaining Vercel preview QA:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff opens the expected mail client.
- Confirm native select popup appearance in target browsers.
- Recheck contact links, redirects, metadata, sitemap, and console output on the deployed preview.

## May 15 Section Intro Measure And Rhythm Pass

The text composition pass introduced earlier in the day overcorrected section and page intros: measures landed around 56ch which produced narrow newspaper-column wrapping (the homepage `Each product shows how Jera turns complex workflows into structured software, reviewable outputs, and business facing experiences.` line broke into too many short fragments at desktop).

This follow up pass widened the intro measures so they read as one to three calm lines on desktop, and added a small spacing bump between the section header block and the content that follows.

Measure token updates (`:root` in `src/styles/global.css`):

- `--measure-intro`: 56ch to 76ch.
- `--measure-page-intro`: new token at 72ch (page hero intros sit at a slightly larger font, so a slightly tighter ch count lands the same target pixel width).
- `--measure-lead`: 50ch to 58ch.
- `--measure-copy`: 60ch to 64ch.
- `--measure-panel`: 52ch to 58ch.
- `--measure-card`: 38ch to 42ch (card body copy is still container bounded; this just removes the unintentional cap on slightly wider cards).
- `--measure-footer`: 38ch to 40ch.
- `--measure-tagline`: 38ch to 40ch.

Utility updates:

- `.page-copy` and `.page-copy-measure` now point at `--measure-page-intro`.
- New `.measure-page-intro` utility added.
- All other utilities follow the updated tokens automatically.

Spacing updates (`section-shell__header` family):

- Standard: `clamp(1.85rem, 3vw, 2.6rem)` to `clamp(2.25rem, 3.6vw, 3.15rem)`.
- Page hero: `clamp(2.15rem, 3.8vw, 3rem)` to `clamp(2.55rem, 4.2vw, 3.55rem)`.
- Compact: `clamp(1.55rem, 2.5vw, 2.15rem)` to `clamp(1.9rem, 2.8vw, 2.5rem)`.

This lands the gap between section intro and the following card or panel grid in the 32px to 50px range across viewports, which sits inside the brief's target 32px to 48px window for standard sections and reads a touch more deliberate for page heroes.

Validation:

- `npm run build` passed and produced 9 static pages.
- `npm run copy-check` passed across 9 generated HTML files.
- `npm run preview` served the build at `http://localhost:4324/`.
- Measure spot checks at 1440px: homepage section intros render at approximately 708px and 2 lines (target was 680px to 760px). The previously narrow `Each product shows...` intro now reads as 2 calm lines instead of 3 to 4 short fragments. Hero copy lands at 580px and 3 lines. Dark panel copy renders at 492px to 520px and 2 to 3 lines.
- Mobile and tablet pages were rechecked at 390px and 768px. Section intros are container bound (about 656px at 768px and ~330px at 390px) and continue to read cleanly.
- No horizontal overflow at any tested width.
- Console errors and warnings remained 0.

## May 15 Editorial Compression Pass

This pass focused on copy, not layout. Verbose section intros and laundry list sentences were compressed into short, intentional statements. The visual system was unchanged.

Approved homepage edits:

- Hero copy compressed to: Practical AI and software engineering for teams turning complex work into clearer, usable systems.
- What Jera builds intro compressed to: Products and business systems that make complex work easier to run, inspect, and improve.
- Product lab intro compressed to: Focused product work for structured workflows, review, and decision support.
- Services intro compressed to: Focused services for clearer workflows, stronger systems, and usable software.
- Decision artifact dark panel description compressed to: Workflows that keep inputs visible, organize analysis, and deliver outputs people can actually review.
- Workflow model intro compressed to: Gather signals, structure the work, support review, and deliver software people can use.
- Homepage CTA description compressed to: Bring a workflow, modernization effort, or decision system that needs to become usable software.
- Modernized Enterprise Workflows build card description compressed to: Stronger architecture, cleaner integrations, and workflows that are easier to extend.

Footer:

- Brand description compressed to: Practical AI and software engineering for teams turning complex work into usable systems.
- Bottom row tagline preserved as: Practical software for structured workflows and clearer decisions.
- Site default meta description compressed to a single product oriented sentence ending in the four areas of work.

Page hero and CTA edits:

- Services hero intro: Engineering support for complex workflows, automation, and AI enabled ideas that need to become usable software.
- Services CTA: Bring a workflow, product idea, or modernization effort that needs clear engineering direction.
- Products hero intro: Owned product work focused on practical engineering and reviewable workflows.
- Products process intro: Complex workflows shaped into structured, reviewable, and usable software.
- Products CTA: Turn a technical idea, operational workflow, or AI enabled process into usable software.
- About hero intro: Practical software and structured workflows, led with product minded engineering.
- About founder panel description: Applied AI, systems architecture, enterprise modernization, and product minded delivery.
- About operating principles intro: Practical delivery, structured AI workflows, and modernization that respects existing systems and people.
- About CTA: Bring a workflow, product idea, or modernization effort that needs structure.
- Contact hero intro: Bring the workflow, system, or product idea you want to improve.
- Contact dark panel description: Best fit for applied AI, modernization, automation, and decision support work.
- Structured Analysis Pipeline panel description, workflow intro, what it demonstrates intro, and CTA all shortened (see current-slice.md for the verbatim before and after table).
- Matchup Analyzer panel description, workflow intro, what it demonstrates intro, and CTA all shortened.
- Solution Examples hero intro: Reusable patterns Jera can structure and build for real workflows.
- Solution Examples CTA: Define the workflow, architecture, and implementation path.

MDX content collection descriptions:

- All five service descriptions had the leading Jera Technologies subject removed and the trailing detail list trimmed.
- Decision Artifact System, Data Pipeline Modernization, and Enterprise Modernization Patterns descriptions were tightened. Authentication & Integration Work was left as is, already concise.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served the build at http://localhost:4325/.
- Spot checks at 1440px: home section intros now render at approximately 708px and fit in 1 to 2 calm lines.
- 1280px and 768px rendered the compressed sentences inside their respective container widths with no horizontal overflow.
- 390px showed clean mobile stacking with no orphan single word last lines.
- Console errors and warnings remained 0.

## May 15 Section Rhythm And Footer Composition Pass

This pass tightened the section header rhythm and simplified the footer so the public site reads as a calmer, more composed final brand impression.

Section header rhythm refinements:

- SectionShell.astro was using class={headerClass} on the header div with an array value, which Astro serialized as comma-separated. The selectors .section-shell__header, .section-shell__header--page, and .section-shell__header--compact were silently never matching. Switching to class:list={headerClass} makes the variants actually apply, so the targeted margin tokens land for the first time.
- Refactored .section-shell__header into a flex column with a > * + * cascade that mirrors the existing mt-5 utility, so the eyebrow + heading + intro stack stays consistent even if a consumer omits the inline utility class.
- Tuned the margin-block-end clamps so intros sit at the brief target spacing:
  - Standard clamp(1.85rem, 4vw, 3rem): roughly 30px mobile, 31px tablet, 48px desktop.
  - Page clamp(2.1rem, 4.4vw, 3.15rem): roughly 34px mobile, 34px tablet, 50px desktop.
  - Compact clamp(1.55rem, 3vw, 2.35rem): roughly 25px mobile, 23px tablet, 38px desktop.

Solution Examples intro copy:

- Home page solution examples intro changed from a descriptive sentence about reusable patterns and implementation paths to: Reusable patterns for structured workflows and clearer implementation.
- Solution Examples page hero intro changed from a sentence about reusable patterns Jera can structure and build to the same statement: Reusable patterns for structured workflows and clearer implementation.

Footer composition:

- Brand blurb compressed to: Practical AI and software engineering for clearer workflows. Renders as a single, calm line at every tested width.
- Bottom row tagline removed entirely. The bottom row now carries only the copyright on the left, which lets the footer close with a quiet, single intent. The brand blurb above carries the brand impression.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served the build at http://localhost:4326/.
- Spot checks confirmed the section header margin-block-end now resolves to 29.6px on mobile, 30.7px on tablet, 37.6px on the compact page hero on Services, and 48px on standard sections at 1280px and 1440px. These match the brief target ranges.
- The footer renders the brand blurb as a single line at desktop and a tight two line wrap at narrow mobile widths.
- No horizontal overflow at any tested width.
- Console errors and warnings remained 0.

## May 15 Mobile Nav + Composition Verification Pass

This pass diagnosed and fixed the mobile nav Contact bug and verified the section rhythm and footer composition were holding after the previous passes.

Mobile nav Contact diagnosis:

- The Contact link was geometrically full row at mobile widths (offsetWidth = 358px at 390px viewport, grid-column: span 2 / span 2, parent width = 358px). The bug the user reported was a low contrast artifact, not a layout bug. The bg-white at 65% opacity on the warm off white header background made the right half of the Contact pill nearly invisible, so it visually appeared to sit in the left column.

Mobile nav Contact fix:

- Switched all mobile nav links from a div level inline-flex (which was previously block, with the inline justify-center having no effect) to inline-flex items-center justify-center so labels render centered inside their full width cells.
- Removed justify-items-start from the mobile nav grid so col-span-2 cells stretch naturally.
- Gave the mobile Contact pill an obvious primary action treatment: filled deep navy background, white text, inset highlight, and a layered shadow. The treatment resets at the sm breakpoint and above, where Contact returns to the light chip style for the flex-wrap tablet layout and the desktop horizontal nav.
- Active state still wins over the dark Contact treatment: when the visitor is on /contact, the mobile pill renders in the soft blue active style, signalling current page. The pill still spans the full row in that state.
- Added a class level CSS rule .mobile-nav-shell .mobile-nav-contact { grid-column: 1 / -1; justify-self: stretch; } at max-width: 639px so the spanning is robust even if a Tailwind utility ordering changes.

Section rhythm and footer:

- After the build the previous pass section rhythm landed correctly. At 1440px standard sections render 48px between intro and content; at 390px they render 29.6px; both inside the brief target ranges.
- Footer brand blurb (Practical AI and software engineering for clearer workflows.) renders as a single line on desktop and a clean two line wrap on mobile. Bottom row now carries only the copyright on the left.

Inquiry modal:

- Spot checked at 390x900 and 1280x900. Copy, dialog semantics, close icons, focus handling, mailto behavior all preserved. No right edge artifact.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served the build at http://localhost:4328/.
- Mobile nav at 390 and 430 showed Contact as a clearly distinguishable dark primary pill spanning the full row, with Services/Products and Solution Examples/About above in a 2 column grid.
- Tablet (700px) and desktop (1280px, 1440px) nav unchanged.
- No horizontal overflow at any tested width.
- Console errors and warnings remained 0.

## May 15 Mobile Contact Centering + Footer Line Pass

Two launch blocking polish issues were fixed in this pass.

Mobile Contact pill correction:

- The previous dark navy primary treatment was rolled back. Per direction, mobile Contact now matches the other nav chips in color and width and sits centered in the third row, since it is the only item in its row.
- The CSS rule .mobile-nav-shell .mobile-nav-contact below 639px now uses:
  - grid-column: 1 / -1 so the cell spans both columns of the third row.
  - justify-self: center so the item sits in the center of that row.
  - width: calc(50% - 0.25rem) so the chip matches the width of the other nav chips (which sit at one column wide, minus half of the 0.5rem column gap).
- The chip uses the same inactiveMobileNavClass styling as the other nav chips. On /contact the activeNavClass applies and the chip renders in the soft blue active treatment, matching how the other chips behave on their own routes.
- All hover, focus visible, and current page states are now the same as the rest of the mobile nav.

Footer brand blurb one line fix:

- The footer brand column was widened from lg:grid-cols-[0.96fr_1.04fr] to lg:grid-cols-[minmax(0,1.18fr)_minmax(0,0.82fr)] so the left brand block has more horizontal room at lg and above.
- --measure-footer was widened from 40ch to 64ch so the blurb (Practical AI and software engineering for clearer workflows.) can extend across the new column width without being capped early.
- The blurb now renders as one line at 768px, 1280px, and 1440px (measured width 519px). Mobile (390px) still wraps naturally over two lines, bounded by the container.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served the build at http://localhost:4329/.
- Mobile nav at 390px and 430px: Contact sits centered in the third row with the same chip styling and width as the other nav items.
- On /contact at 390px the mobile Contact chip shows the soft blue active treatment, matching the other chips' active behavior.
- Footer brand blurb on one line at 1280px and 1440px. Two natural lines on mobile.
- Desktop nav at 1280px unchanged: Services / Products / Solution Examples / About / Contact horizontal row plus the Discuss a project header CTA.
- Inquiry modal opens, the headline reads correctly, and the close button works.
- No horizontal overflow at any tested width. Console errors and warnings remained 0.

Remaining Vercel preview QA carried forward:

- Deploy a Vercel preview and recheck the same widths.
- Confirm mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in target browsers.
- Smoke test contact links, redirects, metadata, sitemap, and console output.

## May 17 Reusable UI/UX Skill Creation

A project scoped Claude Code skill was created to make future UI/UX refinement passes consistent and compounding.

What was created:

- A new skill at .claude/skills/product-ui-design-architect inside jera-workspace.
- It is a generic, reusable skill. It is not Jera specific. Jera appears only as an example project profile inside the skill.
- It complements Anthropic's official frontend-design skill rather than modifying it. The official skill was not edited.
- It encodes reusable senior UI/UX judgment: design posture, text rhythm, section spacing, modal and form quality, mobile navigation, footer composition, accessibility, and launch readiness.
- It supports project vault integration: the skill provides reusable judgment, the project vault provides project specific truth, and the vault wins on conflicts.
- It supports a compounding lesson loop. Reusable cross project lessons go into the skill's references/lessons-learned.md. Project specific lessons stay in the jera-vault.

Skill structure:

- SKILL.md with valid YAML frontmatter.
- references/ with design-principles, vault-integration, project-profile-template, text-rhythm, section-spacing, modal-and-form-quality, mobile-navigation, footer-composition, accessibility-checklist, launch-readiness, lessons-learned, and example-project-profile-jera.
- scripts/README.md documenting future QA scripts (none written yet).
- examples/ with good-section-header, good-footer, good-modal, and anti-patterns.

How it is used for Jera:

- references/example-project-profile-jera.md shows how Jera connects to the skill, including the jera-vault doc paths and the dai-workspace boundary.
- Future Jera UI passes should invoke both frontend-design and product-ui-design-architect, read the relevant jera-vault docs as the source of truth, and record meaningful changes back into the vault.

No site code changed in this pass. No DAI repos were touched. No deployment was performed.

## May 17 Service Copy Compression Pass

A project-aware editorial pass compressed verbose service and solution
example descriptions so prominent copy renders cleanly. No CSS or
component changes were needed; the section rhythm and measure system from
earlier passes held.

Copy changes:

- Services hero intro: "Engineering support for complex workflows,
  automation, and AI enabled ideas that need to become usable software."
  to "Engineering support for workflows, automation, and AI ideas that
  need usable software."
- Enterprise Modernization service description: "Improvements to existing
  applications, integrations, and architecture, with patterns suited to
  the existing system." to "Modernization for existing applications,
  integrations, and access patterns."
- Decision Support Systems service description: "Decision support that
  structures signals, preserves context, and produces artifacts people
  can inspect." to "Decision systems that keep signals, context, and
  reviewable artifacts clear."
- Applied AI service description: "AI enabled applications that organize
  analysis, workflow, clear outputs, and human review." to "AI enabled
  applications that organize analysis, review, and clear outputs."
- Product Experience Buildout service description: "Technical workflows
  shaped into clear interfaces, useful product flows, and production
  ready web experiences." to "Technical workflows shaped into clear
  interfaces and production ready experiences."
- Decision Artifact System solution example description: "Structuring AI
  supported work around evidence, analysis, clear outputs, and human
  review." to "Structuring AI supported work around evidence, analysis,
  and human review."
- Authentication & Integration Work solution example description: "A
  practical pattern for improving secure access flows, integrations, and
  connected workflows." to "Improving secure access flows, integrations,
  and connected workflows."
- Automation & Integration and the remaining solution example
  descriptions were left as-is; they already read cleanly.

Each service description feeds the overview ServiceCard, the Services
detail panel intro, and the homepage services section card, so one
compression fixes all three rendered locations.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served the build at http://localhost:4330/.
- Services detail panel intros render as one calm line each at 1280px.
- The Services hero intro renders as one line.
- Solution Examples detail panel intros render as one line (three) and
  two calm lines (Enterprise Modernization Patterns).
- Homepage service cards render the compressed copy at a tidy two lines.
- No horizontal overflow at 390px, 430px, 768px, 1280px, or 1440px on any
  inspected page.
- The inquiry modal still opens, fits, and renders correctly at 430px.
- Console errors and warnings remained 0.

## May 17 About Page Voice Pass

A copy and text rhythm pass on the About page. No layout or component
changes; the existing SectionShell, technical panel, MetricCard, and
FeatureCard structure was kept. The page reads more down to earth and
slightly witty while staying credible for a senior independent software
studio.

About copy changes:

- Page heading: "A software engineering company with product discipline"
  to "Software engineering for messy, useful work".
- Page intro: "Practical software and structured workflows, led with
  product minded engineering." to "Jera Technologies builds practical AI
  and software systems for teams trying to make complex work easier to
  see, run, and improve."
- Dark card heading: "Led with a focus on practical software and
  structured workflows" to "Built for the parts of work that refuse to
  stay simple".
- Dark card body: "Applied AI, systems architecture, enterprise
  modernization, and product minded delivery." to "Applied AI,
  modernization, automation, and product delivery shaped around real
  workflows, not slideware."
- Focus card value: "Applied AI" to "AI that earns its keep". Body: to
  "Tied to real workflows, useful outputs, and review paths people can
  trust."
- Method card value: "Structured" to "Messy ideas, cleaner paths". Body:
  to "Translate complex technical ideas into software people can operate,
  maintain, and explain."
- Operating principles heading: "Calm engineering for complex systems" to
  "Calm engineering for complicated systems".
- Operating principles intro: to "The work stays practical: understand
  the workflow, protect what already works, and make the next version
  easier to use."
- Principle 1 body trimmed to "AI starts with the workflow, the output
  people need, and the review path around it."
- Principle 2 body: to "Modernization respects the existing system, the
  users, and the business rules behind it."
- Principle 3 body: to "Useful software needs clear screens, steady
  workflow paths, and maintainable structure."

The tone stays calm, senior, and practical. The wit is light (messy work,
not slideware, AI that earns its keep) and never gimmicky. No paid client
work is implied. No overclaiming. No fake agency language. DAI language
stays internal.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 generated HTML files.
- npm run preview served the build at http://localhost:4331/.
- The About h1 wraps to a clean 2 lines at 768px, 1280px, and 1440px.
- The MetricCard values "AI that earns its keep" and "Messy ideas,
  cleaner paths" render as balanced short headings inside their cards.
- No horizontal overflow at 390px, 768px, 1280px, or 1440px.
- Cards still feel balanced. No restricted internal copy in generated
  HTML. Console errors and warnings remained 0.

## May 17 Editorial Systems Pass

A project-aware editorial systems pass. The recurring verbose-intro and
awkward-line-break problem was treated as a system issue, not a per-page
tweak: the copy pattern was fixed across pages, a standing copy rule was
added, and the build copy check now flags long or comma-heavy intros.

Solution Examples copy:

- Hero intro: "Reusable patterns for structured workflows and clearer
  implementation." to "Practical patterns for clearer systems."
- Decision Artifact System description: to "AI supported work organized
  around evidence and review."
- Data Pipeline Modernization description: to "Cleaner data movement
  with reviewable reporting paths."
- Authentication & Integration Work description: to "Cleaner access
  flows and safer integrations."
- Enterprise Modernization Patterns description: to "Stronger structure
  for systems already in use."
- CTA description: to "Turn a pattern into a clear plan for working
  software."
- Tightened five pattern card descriptions (Data intake, Role and access
  workflow design, API integration, Application structure, Incremental
  modernization).

About copy:

- Page intro: to "Practical AI and software for teams making complex
  work easier to see and run."
- Operating principles intro: to "Start with the workflow. Keep what
  works. Make the next version easier to use."

Site-wide:

- Homepage Solution examples section intro updated to match the Solution
  Examples page: "Practical patterns for clearer systems."
- The build copy check advisory then flagged two verbose product hero
  intros. Both were compressed:
  - Structured Analysis Pipeline description: to "An AI enabled workflow
    that turns complex information into reviewable decision work."
  - Matchup Analyzer description: to "Structured workflow design for
    sports matchup review and clear decision artifacts."
- All other prominent intros were already concise from earlier passes
  and were left unchanged.

Tooling:

- scripts/check-public-copy.mjs gained an advisory pass that flags
  prominent section and page intros over 120 characters or with more
  than three commas. It is warning only and never fails the build.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed; the intro rhythm advisory reports all
  prominent intros are concise.
- npm run preview served the build at http://localhost:4332/.
- Solution Examples detail panel intros render as one clean line each.
- About intros render cleanly at 390px and 1280px.
- Product hero intros are now concise.
- No horizontal overflow at 390px, 768px, or 1280px on inspected pages.
- Console errors and warnings remained 0.

## May 17 Inquiry Modal Polish Pass

A focused modal UX and copy rhythm pass on the inquiry modal. No other
part of the site changed except the shared modal CSS.

Modal copy revision:

- Headline: "Rough idea, stubborn workflow, or modernization effort?" to
  "Rough idea or stubborn workflow?"
- Intro: "Send over the shape of it, even if it is still messy. Jera
  Technologies will help turn it into a practical next step." to
  "Modernization effort, product concept, or strange little system
  problem? Send over the shape of it. Jera Technologies will help turn it
  into a practical next step."
- Email fallback helper: "Send a short note to:" to "Send project
  details to:"
- Message label confirmed correct as "What needs attention?" (the
  reported "What eeds attention?" typo was not present in source; it was
  a stale render).
- Eyebrow, project category options, fallback heading, and email were unchanged.
  The current message placeholder is `What's the situation?`.

Form hierarchy refinement:

- The form now reads as four intentional groups: Project category,
  Contact details, Project details, then Submit or direct email.
- Two quiet uppercase scanning labels were added: "Contact details"
  before the name field and "Project details" before the message field.
  They are aria-hidden visual aids; every input keeps its own real label.

CTA icon decision:

- The submit icon was changed from a checkmark to a send / paper-plane
  icon. A checkmark reads as "confirmed"; the action is sending an
  inquiry, so the icon now depicts sending.

Footer action area refinement:

- The hard top border on the action area was replaced with a soft faded
  hairline (a gradient that fades at both ends).
- The vertical divider between the CTA and the direct email helper was
  removed; the desktop column gap separates them now.
- Spacing was loosened so the footer no longer feels cramped on desktop
  or mobile.
- The direct email fallback keeps a warm, helpful tone.

Headline sizing:

- The modal headline font size was reduced from clamp(2rem, 3.6vw,
  2.78rem) to clamp(1.8rem, 2.7vw, 2.3rem) so it reads as a modal
  heading, not a page hero, and wraps into a calm two lines.

Accessibility confirmation:

- Dialog semantics, Escape close, outside click close, focus return,
  focus trap, visible focus states, native validity, and per-input
  labels are all preserved. Escape close and focus return were verified
  in preview.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed; intro rhythm advisory clean.
- npm run preview served the build at http://localhost:4333/.
- Modal QA at 390, 430, 768, 1280, and 1440 (x900): headline wraps
  cleanly as two lines, intro reads naturally, "What needs attention?"
  is spelled correctly, the CTA is visible, the footer is not cramped,
  the direct email fallback reads cleanly, no right edge artifact, no
  horizontal overflow.
- Escape closes the modal and focus returns to the trigger.
- Console errors and warnings remained 0.

Remaining Vercel preview QA:

- Recheck the modal on the deployed preview at the same widths.
- Confirm the mailto handoff opens the expected mail client.
- Confirm the native select popup is acceptable in target browsers.

## May 18 Inquiry Modal Intro Microcopy And Wrap Pass

A final microcopy and text rhythm refinement on the inquiry modal intro.
The modal design, the form structure, the accessibility behavior, and
the mailto handoff are unchanged.

The modal intro now reads "Modernization effort, product concept, or
strange little system problem? Send the rough shape. We'll help turn it
into a practical next step." The previous intro named "Jera Technologies"
literally, which broke the company name across lines in rendered QA. The
intro no longer names the company; "We'll" keeps the tone warm. The
headline "Rough idea or stubborn workflow?" is unchanged.

The modal intro paragraph switched from text-wrap: pretty to
text-wrap: balance so every line is evened rather than only the last
few. This removed a dangling article ("a") that pretty left at the end
of a line at 390px.

Rendered QA at 390, 430, 768, 1280, and 1440 (x900) confirmed the intro
wraps to even lines with no company-name break and no dangling article,
the headline stays a clean two lines, the CTA and the fallback email are
visible, and there is no horizontal overflow. Escape close and focus
return were verified. Console errors and warnings remained 0.
npm run build and npm run copy-check passed.

## May 18 Inquiry Modal Intro Measure Composition Pass

A follow-up composition fix. The microcopy and wrap pass above improved
the intro but it still rendered as cramped fragments, because the intro
was constrained too narrowly (max-inline-size: 50ch, a helper-text
width). This pass fixes the modal text composition system. The headline
and intro copy, the form structure, the accessibility behavior, and the
mailto handoff are all unchanged.

The modal headline and the modal intro now use separate, named text
measures. The headline uses --measure-modal-heading (24ch, compact). The
intro uses the new --measure-modal-intro token at 64ch, up from 50ch.
The shared modal header wrapper max-width was widened from 43rem to 46rem
so it no longer clips the wider intro measure; the headline keeps its
own 24ch cap. The intro keeps text-wrap: balance, which at 64ch lands
the line break after the opening question.

The intro problem was a measure problem, not a copy problem. A
two-sentence intro in a 50ch measure can only wrap to cramped fragments;
the fix is a wider intro measure, not shorter copy.

Rendered QA at 390, 430, 768, 1280, and 1440 (x900): at 768, 1280, and
1440 the intro composes as two calm lines (line one ends after the
opening question, line two carries the second sentence); at 430 and 390
it is four even lines bounded by the panel width. The headline stays a
clean two lines. CTA visible, footer and direct email readable, no
horizontal overflow, no right edge artifact. Escape close and focus
return verified. Console errors and warnings 0. npm run build and
npm run copy-check passed.

## May 21 Color Depth And Iridescence Pass

Addressed the note that the site read too white and slightly
undercolored. The pass added color depth, soft section separation, and a
more present pearl finish while keeping the light theme, navy anchors,
soft blue accents, card layout, and restrained product feel intact. The
iridescence remains a quiet surface refinement, not the concept.

Files changed (jera-site):

- src/styles/global.css: deeper body background wash (stronger corner
  glows + cooler four-stop linear gradient); raised pearl aqua and
  lavender tokens; new `--wash-blue` / `--wash-aqua` / `--wash-lavender`
  and `--color-section-wash-edge` tokens; new `--shadow-lift-glow` token;
  new full-bleed `.section-shell--wash` variant with a faded top
  hairline; tinted `soft-surface` corner light and higher base opacity;
  `subtle-lift` hover now uses the glow shadow with a slightly stronger
  blue border; new `.card-topline` utility (faint blue).
- src/components/sections/SectionShell.astro: added a `surface`
  (`plain` | `wash`) prop; wash applies to light shells only.
- src/pages/index.astro: `surface="wash"` on Product lab and Solution
  examples sections.
- src/pages/products/index.astro: `surface="wash"` on the "How Jera
  builds products" process section.
- src/components/cards/FeatureCard.astro, ServiceCard.astro,
  ProcessStep.astro: replaced the inline neutral top hairline with the
  shared `.card-topline` utility.
- src/components/layout/Footer.astro: soft blue/aqua closing wash instead
  of flat white.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 HTML files; intro rhythm advisory
  clean.
- Rendered QA against the dev server at 1150px and 390px on Home,
  Services, Products, Solution Examples, and Contact (plus the inquiry
  modal).
- Desktop: washed Product lab and Solution examples bands read as clear,
  calm section transitions; plain and washed sections alternate with the
  dark panels breaking them up; feature/service cards show the faint blue
  topline and lift off the cooler field; the products process section
  separates cleanly from the product grid above.
- Mobile (390px): tinted bands are visible and calm; documentElement
  scrollWidth equals clientWidth (no horizontal overflow).
- Inquiry modal: pearl panel, headline, intro, form groups, Send inquiry
  CTA, and direct email fallback all render correctly with no right edge
  artifact (the modal opts out of the iridescent overlay and was
  unaffected).
- Console errors and warnings: 0.

No copy changed. No dependencies added. No DAI repos touched. The site
remains static and launch ready.

## May 21 Page Atmosphere Composition Correction

The color-depth pass above was corrected the same day. It had added
isolated `section-shell--wash` bands, which made the homepage feel
visually split: a flat-white top (hero through What Jera builds) and a
colored lower zone, with an abrupt transition. Root cause: the page
background was distributed across the full document height, so the blue
mid-stops pooled on the lower-middle of a long page while the hero stayed
pale; the washes reinforced "color only lower." This correction replaced
the local treatment with one art-directed global atmosphere.

Files changed (jera-site):

- src/styles/global.css: replaced the document-height body background
  with an even, calm pearl base; moved the colored atmosphere into a
  fixed, full-viewport ambient layer (`body::before`, blue top-left, cyan
  top-right, faint lavender mid-right, low navy floor glow) so every
  screen shares the same lighting; moved the faint grid texture to a
  second fixed layer (`body::after`); refined `soft-surface` to a cleaner,
  brighter white so cards read as surfaces inside the lit field.
- src/pages/index.astro: removed `surface="wash"` from Product lab and
  Solution examples.
- src/pages/products/index.astro: removed `surface="wash"` from the
  process section.
- src/components/sections/HeroSection.astro: tightened hero bottom padding
  so the gap into What Jera builds is no longer a blank white void.

The `section-shell--wash` prop and CSS remain in the codebase but are
unused on the homepage; the global atmosphere is the intended fix for a
"too white" page, not isolated bands.

Validation:

- npm run build passed and produced 9 static pages.
- npm run copy-check passed across 9 HTML files; intro advisory clean.
- Rendered QA against the dev server at 1440px, 1150px, and 390px on the
  homepage (hero, hero-to-content seam, a deep section) and the products
  page. The ambient lighting renders identically at the top and in deep
  sections, so the page reads as one coherent composition with no split
  and no abrupt colored band. The hero left is lit, not flat white.
- Note: a Playwright full-page screenshot mis-renders a fixed background
  (it paints only in the first stitched viewport), so per-viewport
  captures at multiple scroll positions were used to judge the fixed
  ambient. The fixed pseudo-element technique was chosen over
  background-attachment: fixed for iOS Safari reliability.
- Mobile (390px): documentElement scrollWidth equals clientWidth (no
  horizontal overflow); hero and nav read clean and lit.
- Console errors and warnings: 0.

No public copy changed. No dependencies added. No DAI repos touched.
