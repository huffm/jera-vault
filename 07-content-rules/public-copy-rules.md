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
- Reviewable decision support outputs.
- AI assisted review workflows.
- Analysis and evaluation workflows.
- Human review.
- Decision support.

Avoid exposing internal method terms on public pages unless Malcolm explicitly approves them for launch.

## Product Language

Products should feel credible and business facing. They should demonstrate what Jera Technologies can build through its engineering services.

## Sports Product Language

The Matchup Analyzer should be described as a product lab prototype for sports matchup review and compact decision support briefs. Do not center the product around gambling, picks, guaranteed predictions, betting advantage, or profits.

## Current Website Copy Check

Slice 1 public site copy was checked for restricted public terms. The current website source does not use the restricted casual product or betting centered terms.

Internal truth boundaries remain in the vault rather than being displayed as public page copy.

## Public Exposure Reduction

Slice 2 reduced public exposure of internal method language.

Avoid leading public pages with:

- DAI
- Retrieval
- Synthesis
- Internal stage sequencing
- Prompt logic
- Scoring rules
- Internal cognitive architecture

Preferred public language:

- Structured analysis
- Signal gathering
- Reviewable outputs
- Structured decision support
- AI assisted review workflows
- Compact decision support briefs
- Productized software workflows
- Structured Analysis Pipeline
- Reviewable Analysis System

The generated HTML was checked after Slice 2 and does not expose `DAI`, retrieval, evaluation, or synthesis.

## Launch Copy Check

The site now includes a repeatable public copy exposure check:

`npm run copy-check`

The check scans generated HTML in `dist` for restricted public terms including DAI, internal stage language, private scoring rules, internal prompt logic, cognitive architecture, artifact terminology, betting model, prediction engine, guaranteed picks, and profit.

Run it after `npm run build` before preview deployment.

## Contact Copy And Links

The inquiry form is the single public contact path for v1 / soft launch.

Do not use retired placeholder email addresses or placeholder domains in public source, generated HTML, or vault launch notes.

Do not add a public `mailto:` fallback or expose the receiving inbox in client
source. The destination inbox is configured server-side through
`CONTACT_TO_EMAIL`.

Current v1 contact behavior:

- Header project CTA opens the inquiry modal when JavaScript is available and falls back to `/contact`.
- Contact navigation items route to `/contact`.
- Product, service, solution, and page level contact CTAs open the inquiry modal when JavaScript is available and fall back to `/contact`.
- The Contact page has an inquiry form trigger.
- Footer contact routes visitors to the inquiry path.

The v1 choice is intentional: the inquiry modal posts JSON to the Vercel
Function at `/api/inquiry`, with Turnstile, honeypot, server-side validation,
origin checks, and Resend delivery. The Astro site remains static; the function
is detected by Vercel independently of the static build.

Inquiry confirmation copy:

- Title: `Inquiry sent`
- Body: `Thanks. We’ll be in touch soon.`

Confirmation copy should stay calm, business appropriate, and short. Prefer
`We’ll be in touch soon` over highly personal first-person follow-up language.

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

`Jera built products with clear engineering direction`

## Tile Copy Specificity

Avoid repeating one generic sentence across multiple cards or tiles. Repeated filler makes the site feel generated even when the information is accurate.

Service outcome and solution example tiles should use descriptions that explain the specific pattern, outcome, or implementation concern.

Approved direction:

- Keep each tile short.
- Make each tile specific to the heading.
- Use practical software language.
- Avoid fake proof, fake client claims, and named stack narrowing.
- Preserve the broad enterprise modernization stance.

The repeated phrase `A reusable pattern that can support a practical software workflow` should not appear in public generated HTML.

## Component Display And Public Copy Pass

The component display polish pass did not add new public claims, client proof, metrics, testimonials, backend contact behavior, or restricted internal method language.

Public label direction:

- Labels should feel like calm interface metadata, not promotional badges.
- Use muted slate, muted blue gray, soft off white, subtle borders, and small signal dots.
- Avoid loud uppercase blue labels.
- Decorative dots must sit inline with the label, heading, or status element. Do not place loose decorative dots at the far edge of cards.

Public text measure direction:

- Page hero headings and intro copy may use wider desktop measures than card copy.
- Keep page headings balanced and editorial.
- Keep card copy compact and readable.
- Avoid narrow desktop text towers for broad positioning statements.

Current copy check result:

- `npm run copy-check` passed after the component display polish pass.
- Generated HTML search passed for retired placeholder emails, placeholder domains, `DAI`, retrieval, evaluation, synthesis, betting model, prediction engine, and profit language.
- Public email remains `support@jeratechnologies.com`.
- Contact mailto remains `mailto:support@jeratechnologies.com?subject=Project%20Conversation%20with%20Jera%20Technologies`.

## May 12 Public Copy Polish Rules

Current public heading and naming decisions:

- Use `Authentication & Integration Work`, not `Authentication And Integration Work`.
- Use `Automation & Integration`, not `Automation And Integration`.
- Keep About page copy company-first. Avoid public page framing such as `Malcolm leads...`.
- A subtle founder reference may be used elsewhere when useful, but the public About page should not read like a casual personal portfolio.
- Prefer `decision systems`, `decision applications`, or `decision support applications` when it improves line rhythm, while preserving the Decision Support Systems service name.
- Do not reintroduce DAI as public-facing product copy.

Inquiry copy rules:

- Do not claim the inquiry modal submits to a backend.
- Document the implementation internally as a mailto draft, but keep visitor-facing helper copy warm and direct.
- Keep `support@jeratechnologies.com` as the fallback email.
- Keep the subject `Project Conversation with Jera Technologies`.

Latest check result:

- `npm run build` passed on May 12, 2026.
- `npm run copy-check` passed across 9 generated HTML files.
- Generated HTML search found no retired placeholder emails, placeholder domains, `DAI`, retrieval, evaluation, synthesis, betting model, prediction engine, profit, `Malcolm leads`, or `Authentication And Integration Work`.

## May 14 Public Copy Refinement

Current header subtitle:

`Practical AI & Software Engineering`

About page rules:

- Do not expose internal positioning notes on public pages.
- Do not mention recruiters, future consulting prospects, or copy designed to feel credible.
- Keep the About page company-first and public-facing.
- Use operating principle copy that explains how Jera Technologies works in practical terms.

Approved About operating principle direction:

- Practical AI: AI work starts with the workflow, the output people need, and the review path around it.
- Enterprise judgment: modernization work respects existing architecture, integrations, access patterns, users, and business rules.
- Product minded delivery: delivery stays close to the people using the system, with clear screens, steady workflow paths, and maintainable software.

Copy sweep result:

- The internal About sentence using `public positioning`, `recruiters`, `future consulting prospects`, `built to feel credible`, and `broad enough` was removed from the public site.
- Public source no longer uses `client's system`; the Enterprise Modernization service now says `existing system`.
- Public product CTA copy now uses `operational workflow` instead of `internal workflow`.
- No public source matches remain for `showcase`, `lab`, or `fake agency` language.

Inquiry copy direction:

- The modal title is `Rough idea, stubborn workflow, or modernization effort?`.
- The intro is `Send over the shape of it, even if it is still messy. Jera Technologies will help turn it into a practical next step.`
- The CTA is `Send inquiry`.
- Do not use system-like helper text in the modal footer; the visible fallback should stay warm and direct.

May 15 inquiry copy update:

- Use `Applied AI` in the public inquiry categories and public service label.
- Final inquiry categories are `Applied AI`, `Enterprise Modernization`, `Workflow Automation`, `Architecture & Integration`, `Decision Support Systems`, `Product Strategy`, and `Not Sure Yet`.
- Message label should read `What needs attention?`.
- Message placeholder should read `What's the situation?`.
- Fallback copy should read `Prefer a direct email?` and `Send a short note to:`.
- Keep the email spelled exactly as `support@jeratechnologies.com`.
- Do not reintroduce the retired service label, retired engineering variant, retired fallback helper, or typo contact email.

Latest check result:

- `npm run build` passed on May 14, 2026.
- `npm run copy-check` passed across 9 generated HTML files.
- Generated HTML search found no matches for `Applied software engineering`, `public positioning`, `recruiters`, `future consulting prospects`, `built to feel credible`, `broad enough`, `showcase`, `lab`, `fake agency`, `client's system`, `internal workflow`, `DAI`, retrieval, evaluation, synthesis, betting model, prediction engine, guaranteed picks, or profit.
- `npm run build` and `npm run copy-check` passed again on May 15, 2026 after the inquiry modal polish.
- Generated output and public site source no longer include the retired service label, retired engineering variant, retired fallback helper, or typo contact email.

## May 14 Responsive UI Copy Addendum

The visual refinement pass did not introduce new client claims, agency language, internal strategy language, or private product terminology.

Product page copy direction:

- Prefer direct product language such as `Jera built products` or `these products`.
- Avoid `showcase` language.
- Avoid leaning on `credible` as a public proof substitute.
- Describe the product examples as structured, reviewable, and usable software.

Current changed product copy:

- Products metadata now says `Explore Jera Technologies products for structured analysis and decision support software.`
- Products page intro now says `Jera built products show practical engineering, reviewable workflows, and business facing software design.`
- Product process intro now says `These products show how complex workflows can become structured, reviewable, and usable software.`

Latest check result:

- `npm run build` passed on May 14, 2026 after the responsive UI refinement.
- `npm run copy-check` passed across 9 generated HTML files.
- Generated HTML search found no matches for the targeted internal copy terms, retired DAI public exposure terms, betting centered language, or fake agency language.

## May 15 Premium Design Pass Copy Audit

The premium design architecture pass kept public copy stable, refined a few specific labels, and broadened the automated copy exposure check.

Copy refinements landed in this pass:

- Homepage product portfolio eyebrow now reads `Product lab` rather than `Product portfolio`. This aligns the public language with the brand direction of describing the lab's surfaced work as Jera built products and product lab work, while still avoiding portfolio gallery framing.
- About `Focus / AI` and `Approach / Build` metric values were replaced with `Focus / Applied AI` and `Method / Structured` plus refined supporting copy, so the page no longer carries shout-word values that read as SaaS poster language.
- Inquiry modal copy was confirmed against the launch spec: eyebrow `Project Inquiry`, headline `Rough idea, stubborn workflow, or modernization effort?`, intro `Send over the shape of it, even if it is still messy. Jera Technologies will help turn it into a practical next step.`, message label `What needs attention?`, message placeholder `What's the situation?`, fallback heading `Prefer a direct email?`, fallback helper `Send a short note to:`, and fallback email `support@jeratechnologies.com`.

`check-public-copy.mjs` was expanded so the build pipeline blocks any regression of the named internal phrases:

- Internal method: `DAI`, `retrieval`, `evaluation`, `synthesis`, `private scoring rules`, `internal prompt logic`, `cognitive architecture`, `betting model`, `prediction engine`, `guaranteed picks`, `profit`.
- Internal positioning and agency language: `public positioning`, `recruiters`, `future consulting prospects`, `built to feel credible`, `broad enough`, `fake agency`.
- Retired service and engineering labels: `AI Application Engineering`, `Applied AI Engineering`.
- Retired contact email typo: `jerattechnologies.com`.
- Retired internal copy phrases: `client's system`, `internal workflow`.

Latest check result:

- `npm run build` passed on May 15, 2026 after the premium design architecture pass.
- `npm run copy-check` passed across the generated HTML with the expanded restricted term list active.

## May 15 Text Composition Copy Notes

The text composition pass focused on how copy renders, not on rewriting the words. One small copy adjustment landed where the rendered phrasing was slightly redundant.

Copy adjustments:

- Contact dark panel description previously read `Best fit conversations involve applied AI software, enterprise workflow modernization, automation, integrations, product buildout, or decision applications.` The phrase `enterprise workflow modernization` was reduced to `enterprise modernization` so the description matches the rest of the public service naming and wraps more naturally inside the 52ch panel measure.

No other public copy was changed in this pass. The headline statements, service summaries, product summaries, solution example summaries, About operating principles, and inquiry modal copy all remain on spec.

Heading and intro measure rules:

- Public section and page intros now flow inside a 56ch maximum measure. Headings sit inside 24ch (page and section) or 28ch (panel) maximums where they should compose into deliberate 2 to 3 line shapes.
- Card body copy, helper text, footer copy, and modal copy each have their own approved measure range.
- See `02-website/design-direction.md` `May 15 Text Composition Direction` for the full token table.

Validation:

- `npm run build` passed.
- `npm run copy-check` passed across the 9 generated HTML files.

## May 15 Editorial Compression Pass

Public copy was compressed to feel calmer and more deliberate. The edits trimmed laundry lists, removed repeated subject phrases, and brought most section intros under 18 words so they read as 1 to 2 lines on desktop.

Approved direction:

- Section intros generally 10 to 16 words.
- One clear idea per sentence. No category stacking.
- Avoid leading every sentence with the words Jera Technologies. The brand name should appear deliberately, not as a default.
- Replace AI enabled workflows and business facing experiences where a more specific phrase fits.
- Card descriptions stay short and concrete. Service and solution example descriptions in the content collection do the same job.

Footer direction (refresh):

- Brand description: Practical AI and software engineering for teams turning complex work into usable systems.
- Bottom row tagline preserved: Practical software for structured workflows and clearer decisions.
- The two lines now read as distinct statements rather than near duplicates.

Site meta description direction:

- The default SEO description compresses to a single intent sentence ending with the four areas of work (products, automation, modernization, decision support). This keeps the description under 160 characters while preserving the public service language.

The visual system, measure tokens, and section spacing rules introduced earlier in the day were unchanged. The editorial pass only changes the words on the page.

## May 17 Service Description Copy Rules

Clarified rules for service and solution example description fields in the
content collection:

- Keep each description to roughly 9 to 13 words and one clear idea.
- Avoid four item comma lists. Three concrete terms or fewer.
- Do not repeat a qualifier the sentence already implies (avoid "existing
  applications ... suited to the existing system").
- The description field is shared across the overview card, the detail
  panel intro, and the homepage services card. Edit it once at the MDX
  source; do not add per-surface overrides.
- Keep the calm, senior, practical, non-hype voice. Proper casing. Avoid
  public facing dashes where practical.

Current approved service descriptions:

- Applied AI: "AI enabled applications that organize analysis, review,
  and clear outputs."
- Enterprise Modernization: "Modernization for existing applications,
  integrations, and access patterns."
- Automation & Integration: "Automation across tools, data, and business
  processes, kept visible and easy to review."
- Decision Support Systems: "Decision support systems that keep signals,
  context, and review paths clear."
- Product Experience Buildout: "Technical workflows shaped into clear
  interfaces and production ready experiences."

Current approved solution example descriptions:

- Structured Decision Support System: "AI assisted analysis organized
  around evidence, human review, and clear recommendations."
- Data Pipeline Modernization: "Data movement and reporting workflows
  improved with practical automation."
- Authentication and Integration Modernization: "Safer access flows and
  more maintainable system connections."
- Enterprise Modernization Patterns: "Stronger architecture, business
  logic preservation, and integration planning for existing systems."

Latest check result:

- `npm run build` and `npm run copy-check` passed on June 18, 2026.
- No artifact terminology or other restricted internal terms appear in generated HTML.
- The intro rhythm advisory reports all prominent intros are concise.

## May 17 About Page Copy

Approved About page copy after the voice pass:

- Page eyebrow: "About Jera Technologies".
- Page heading: "Software engineering for messy, useful work".
- Page intro: "Jera Technologies builds practical AI and software systems
  for teams trying to make complex work easier to see, run, and improve."
- Dark card eyebrow: "Founder and Principal Engineer".
- Dark card heading: "Built for the parts of work that refuse to stay
  simple".
- Dark card body: "Applied AI, modernization, automation, and product
  delivery shaped around real workflows, not slideware."
- Focus card: "Focus" / "AI that earns its keep" / "Tied to real
  workflows, useful outputs, and review paths people can trust."
- Method card: "Method" / "Messy ideas, cleaner paths" / "Translate
  complex technical ideas into software people can operate, maintain, and
  explain."
- Operating principles heading: "Calm engineering for complicated
  systems".
- Operating principles intro: "The work stays practical: understand the
  workflow, protect what already works, and make the next version easier
  to use."
- Principle 1: "Practical AI" / "AI starts with the workflow, the output
  people need, and the review path around it."
- Principle 2: "Enterprise judgment" / "Modernization respects the
  existing system, the users, and the business rules behind it."
- Principle 3: "Product minded delivery" / "Useful software needs clear
  screens, steady workflow paths, and maintainable structure."

Voice rule clarified: a little dry wit is acceptable in public headings
when it stays calm and senior. Do not let it become cute, goofy, or
hypey. Do not imply paid client work. Do not overclaim. Keep DAI internal.

Latest check result: npm run build and npm run copy-check passed on
May 17, 2026. No restricted internal terms in generated HTML.

## June 18 Public Positioning Polish

A copy polish pass made the affected public language more natural and
grounded and less generic. Paired with the desktop typography rhythm
correction (see `02-website/design-direction.md`).

Changes landed:

- Header subtitle changed from `Practical AI & Software Engineering` to
  `Modern Systems & Decision Support`. Fits on one line in the brand
  subtitle box at 390px (187px in a 196px cap, no overflow).
- Homepage "What Jera builds" heading: `Practical systems for complex
  work` → `Software for complex work`. Body rewritten to
  `Workflow software, automation, modernization, and decision support for
  teams whose real process is messier than the diagram.`
- Product lab heading (homepage section and Product Lab page):
  `Product concepts grounded in real workflows` →
  `Product concepts from real workflow problems`. Body (both surfaces):
  `The product lab explores AI assisted review, automation, and decision
  support through prototypes tied to practical workflow problems.`
- Solution Examples page heading: `Solution patterns for complex software
  workflows` → `Solution patterns for complex workflows`. Body:
  `Examples of how Jera approaches AI assisted review, data movement,
  system access, and modernization with clear software patterns.`

Known tension to track: these new intros run ~124–133 characters and trip
the build's non-failing intro-rhythm advisory (and run against the
Prominent Section Intro Rule below, which prefers ≤110 chars). They were
adopted deliberately as approved positioning copy that reads as natural
sentences rather than terse category lists; the trade was made knowingly,
not by oversight. Revisit if the advisory noise becomes a problem.

Validation: `npm run build` and `npm run copy-check` passed; generated
HTML has no `decision artifact`, `artifact system`, `artifact engine`,
`applied AI software`, or betting/prediction language.

## June 18 Microcopy Alignment

A tiny follow-up pass tightened a few small brand/positioning lines after
the typography rhythm pass. No redesign, no full copy reopen.

- Header subtitle: `Workflow Systems & Decision Support` →
  `Applied AI & Software Solutions`. The existing responsive subtitle
  treatment remains unchanged: one line on desktop and a clean two-line
  wrap on mobile with no overflow.
- Footer brand line: `Practical AI and software engineering for clearer
  workflows.` → `Software systems for work that does not fit the
  template.` This supersedes the earlier fixed footer-line decisions (see
  `02-website/design-direction.md`). It carries a little understated
  personality, implies practical engineering without listing services,
  makes no client-work claim, and deliberately uses a different image from
  the homepage body ("messier than the diagram") so the two do not repeat.
  One line on desktop within the 64ch footer measure; wraps cleanly on
  mobile.
- Homepage Solution section heading: `Selected patterns for complex
  software work` → `Selected patterns for complex workflows`. Consistent
  with the Solution Examples page heading (`Solution patterns for complex
  workflows`) while staying distinct ("Selected" vs "Solution"), so the
  two surfaces align without being forced identical.

The `terms-to-use-and-avoid.md` contradiction was resolved: "applied AI
software" was removed from Preferred Terms, added to Restricted Terms, and
the replacement guidance now points to "AI enabled software" / "AI
assisted review workflows" / "structured AI workflows". "Applied AI" alone
remains acceptable as an inquiry category label.

Validation: `npm run build` and `npm run copy-check` passed; generated
HTML has no `applied AI software`, `decision artifact(s)`, `artifact
system/engine`, or betting/prediction language.

## Prominent Section Intro Rule

This rule exists because verbose intro copy kept reappearing on page
after page and degrading the visual quality of the site. Treat it as a
standing rule, not a one-off cleanup.

A prominent section or page intro (the paragraph that sits under an
eyebrow and heading, before cards, panels, or a grid) should usually:

- Carry one clear idea.
- Avoid laundry lists. Do not try to name every service or every
  capability in the intro sentence.
- Avoid comma-heavy service lists. More than about three commas in a
  prominent intro is a signal to rewrite.
- Stay short enough to render cleanly: aim for roughly 110 characters or
  fewer, and one or two calm lines on desktop.
- Let cards and panels carry the detail. The intro frames; the cards
  explain.
- Prefer better, shorter copy over widening or narrowing the text
  measure. A long sentence is a copy problem, not a layout problem.

Card body copy may carry more detail than an intro, but it should still
be concise. A four item comma list in a card description should usually
drop to three concrete terms or fewer.

The build copy check (npm run copy-check) now prints an advisory when a
prominent intro is long or comma-heavy. The advisory never fails the
build; it is a prompt to review the copy editorially.
