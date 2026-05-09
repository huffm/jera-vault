# Public Copy Rules

## Purpose

These rules keep Jera Technologies public copy accurate, credible, and consistent.

## Rules

- Write in a calm, senior, product minded tone.
- Keep copy concise and practical.
- Use proper casing.
- Avoid dashes in public facing copy where possible.
- Prefer concrete workflow language over broad AI claims.
- Describe products as Jera built products, owned products, product examples, or solution examples.
- Do not imply paid client work unless explicitly provided later.
- Do not invent clients, metrics, testimonials, revenue, adoption, or results.
- Keep employer related work high level and non sensitive.
- Do not expose private prompts, scoring rules, unreleased product strategy, or monetization details.

## AI Language

Use AI language only when it describes a real workflow or capability. Preferred framing:

- AI supported analysis.
- Structured AI workflows.
- Structured analysis.
- Signal gathering.
- Reviewable outputs.
- Reviewable decision artifacts.
- Human review.
- Decision support.

Avoid exposing internal method terms on public pages unless Malcolm explicitly approves them for launch.

## Product Language

Products should feel credible and business facing. They should demonstrate what Jera Technologies can build through its engineering services.

## Sports Product Language

The matchup analyzer should be described as a sports matchup analysis and decision support application. Do not center the product around gambling, picks, guaranteed predictions, or betting profits.

## Current Website Copy Check

Slice 1 public site copy was checked for restricted public terms. The current website source does not use the restricted casual product or betting centered terms.

Internal truth boundaries remain in the vault rather than being displayed as public page copy.

## Public Exposure Reduction

Slice 2 reduced public exposure of internal method language.

Avoid leading public pages with:

- DAI
- Retrieval
- Evaluation
- Synthesis
- Internal stage sequencing
- Prompt logic
- Scoring rules
- Internal cognitive architecture

Preferred public language:

- Structured analysis
- Signal gathering
- Reviewable outputs
- Clear decision artifacts
- Productized software workflows
- Structured Analysis Pipeline
- Reviewable Analysis System

The generated HTML was checked after Slice 2 and does not expose `DAI`, retrieval, evaluation, or synthesis.

## Launch Copy Check

The site now includes a repeatable public copy exposure check:

`npm run copy-check`

The check scans generated HTML in `dist` for restricted public terms including DAI, retrieval, evaluation, synthesis, private scoring rules, internal prompt logic, cognitive architecture, betting model, prediction engine, guaranteed picks, and profit.

Run it after `npm run build` before preview deployment.

## Contact Copy And Links

Use `support@jeratechnologies.com` for public contact email.

Do not use retired placeholder email addresses or placeholder domains in public source, generated HTML, or vault launch notes.

Use mailto links for v1 contact behavior. A backend contact form should only be added in a future implementation slice with explicit approval.

Current v1 mailto behavior:

- Header contact CTA routes to `/contact`.
- Contact navigation items route to `/contact`.
- Product, service, solution, and page level contact CTAs route to `/contact`.
- The Contact page email button uses the shared mailto link with a project conversation subject.
- Footer email uses the same shared mailto link.

The v1 choice is intentional: mailto keeps the public site static, simple, and launch ready while avoiding backend dependencies until they are needed.

Future contact form direction:

- Astro API route or Astro Action.
- Vercel deployment with the required runtime configuration.
- Vercel environment variables for the email delivery key and destination address.
- Resend for email delivery.
- Optional Cloudflare Turnstile for spam protection.

## Responsive QA Copy Result

The responsive systems QA slice did not introduce new public product claims.

Public naming remains:

- Structured Analysis Pipeline.
- Matchup Analyzer.

Generated public HTML was checked after build. Restricted internal method terms and retired placeholder contact domains were not found in generated page copy.

The only source match for `synthesis` is the CSS property `font-synthesis-weight`, which is typography configuration and not public product language.

## Heading Punctuation

Major public headings should generally avoid terminal periods when they read as title statements.

Apply this to:

- Page hero headings.
- Section headings.
- Large product or CTA panel headings.
- Large card headings when they function as labels.

Do not remove punctuation from normal paragraphs, descriptions, or explanatory body copy.

Generated public HTML was checked after the typography cleanup slice. No terminal periods remain in public `h1`, `h2`, or `h3` headings.

## Mature Product Surface Copy Notes

The mature product surface pass keeps public copy calm, product minded, and business facing.

Use quieter labels for page and card metadata. Prefer slate or muted blue treatments, subtle pills, or small signal markers over bright cyan uppercase labels.

Products may be described as:

- Jera built products.
- Owned product examples.
- Product portfolio entries.
- Structured software products.
- Reviewable analysis systems.
- Decision support workflows.

Do not describe these products as client work unless explicit client permission and project facts are provided later.

The current Products page headline is approved for public use:

`Structured software products for clearer decisions`

Generated public HTML was checked after this pass. Restricted internal method terms, retired product shorthand, betting centered language, and placeholder contact domains were not found.

## Public Copy Polish Notes

Prefer direct, natural phrasing over technically correct but stiff language.

Good public headings should:

- Be concise.
- Sound business facing and human.
- Avoid overexplaining internal method.
- Avoid negative framing unless needed for truth boundaries.
- Connect products to Jera engineering capability without sounding like a casual portfolio gallery.

Current approved homepage product heading:

`Jera built products with a clear engineering approach`
