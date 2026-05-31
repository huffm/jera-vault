# 0006 Inquiry Form Experience

## Status

Accepted

## Date

May 12, 2026

## Context

The public site needs a more refined project inquiry experience before Vercel preview, but it should remain static and launch ready. There is no approved backend form service yet, and the site should not imply that messages are submitted to an API when they are not.

The inquiry flow should help Jera Technologies understand the visitor's general project category and message while staying easy to fill out on mobile and desktop.

## Decision

Use a lightweight accessible inquiry modal implemented with Astro markup and minimal vanilla JavaScript.

The modal opens from project-oriented CTAs such as `Discuss a project`, `Contact Jera Technologies`, and related service/product CTAs when JavaScript is available. Fallback links continue to route to `/contact` or mailto.

The modal fields are:

- Project category.
- Name.
- Email.
- Company.
- Message.

Submission opens a prepared mailto draft to `support@jeratechnologies.com` using the subject `Project Conversation with Jera Technologies`. The body includes the selected field values and visitor message.

The current modal title is `Rough idea, stubborn workflow, or modernization effort?`. The intro is `Send over the shape of it, even if it is still messy. Jera Technologies will help turn it into a practical next step.` The primary CTA reads `Send inquiry`, and the form still opens a mailto draft.

May 15 form quality refinement:

- The right edge artifact was resolved by softening the modal-specific iridescent overlay and removing the always reserved scrollbar gutter.
- The final project category options are `Applied AI`, `Enterprise Modernization`, `Workflow Automation`, `Architecture & Integration`, `Decision Support Systems`, `Product Strategy`, and `Not Sure Yet`.
- The message label is `What needs attention?`, with a placeholder that invites a workflow, legacy system, modernization effort, product idea, integration, or decision process that needs improvement.
- The fallback copy is `Prefer a direct email?` and `Send a short note to:`
- The fallback email remains `support@jeratechnologies.com`.
- The headline uses balanced wrapping and the supporting copy uses prettier wrapping where supported.
- The footer uses a clearer hierarchy with the primary CTA on the left and direct email helper on the right at desktop widths, then a clean stacked layout on mobile.
- The native select remains in place. Its closed state is styled to match the modal, but the open dropdown list remains controlled by the browser and operating system.

May 14 UI refinement:

- Inquiry triggers now use document level event delegation, so new CTAs with the trigger attribute inherit modal behavior without adding one-off JavaScript.
- The modal panel is wider on desktop, more compact vertically, and capped with `100dvh` based sizing for better mobile browser behavior.
- Field spacing, input height, textarea height, placeholder contrast, select placeholder color, and CTA spacing were tuned so the form feels less cramped and less oversized.
- Native form validity is checked before the mailto draft is built.
- One line fields are sanitized to remove line breaks before they are inserted into the email body.
- The message field is trimmed before it is inserted into the email body.

## Accessibility Notes

- The modal uses `role="dialog"` and `aria-modal="true"`.
- The modal is labelled by its heading and described by its intro paragraph.
- Escape closes the modal.
- Clicking outside the panel closes the modal.
- The close button has an accessible label.
- Focus moves into the modal on open and returns to the triggering element on close.
- The form keeps a visible fallback email link.
- The select remains native for keyboard support, assistive technology support, and native form validity.

## Boundaries

- Do not add React or Preact.
- Do not add a backend form submission service in this slice.
- Do not claim the form sends successfully.
- Do not remove the mailto fallback.
- Keep the site static and Vercel preview ready.

## Consequences

Positive:

- The inquiry experience feels more intentional than a plain email link.
- Visitors can identify the project category and provide contact context before opening the email draft.
- Launch remains low risk because no backend dependency is introduced.
- The contact path remains accessible without JavaScript.

Tradeoffs:

- Visitors still need a local email client or browser email handler for the final send action.
- A real backend form may be needed later if mailto creates friction.

## QA Result

Previous responsive QA checked the modal at 390px and 1280px and confirmed modal open behavior, mailto fallback, Escape close, no horizontal overflow, and no console errors.

The May 14 implementation check confirmed:

- `npm run build` passed.
- `npm run copy-check` passed across 9 generated HTML files.
- Generated HTML includes the simplified five-field modal: project category, name, email, company, and message.
- Generated HTML includes the current title, intro, and `Send inquiry` CTA.
- Responsive route QA checked the modal at 390px by 900px and 1280px by 900px.
- The modal fits within both checked viewports.
- Focus moves to the project category field on open.
- The primary CTA remains visible on desktop and mobile.
- No horizontal overflow was detected during route QA at 390px, 768px, or 1280px.
- The built output was also served with `npm run preview`; modal checks passed at 390px by 900px and 1280px by 900px.

The next preview smoke test should recheck the modal visually at mobile and desktop widths after deployment.

The May 15 preview check confirmed:

- `npm run build` passed and generated 9 static pages.
- `npm run copy-check` passed across 9 generated HTML files.
- Generated output and public site source no longer include the retired service label, retired engineering variant, retired fallback helper, or typo contact email.
- Local `npm run preview` served successfully at `http://127.0.0.1:4321/`.
- Modal screenshots were checked at 390px by 900px, 768px by 900px, and 1280px by 900px.
- The CTA and fallback email are visible at 390px by 900px.
- No horizontal overflow was detected at the checked modal sizes.
- Escape close, outside click close, focus return, and native invalid form behavior still pass.

Remaining Vercel preview QA:

- Recheck the same modal sizes on the deployed Vercel preview URL.
- Confirm the native select open dropdown appearance is acceptable in target browsers.
- Confirm the mailto handoff works from the live preview.
- Recheck contact links, redirects, metadata, sitemap, and console output on the preview URL.

## May 15 Premium Design Architecture Pass

The premium design pass kept the inquiry modal architecture unchanged. It refined surface quality, the right edge artifact, the icon language, the entrance animation, and the action area without changing the field set or the mailto behavior.

Surface and edge:

- The modal panel explicitly disables the iridescent overlay (`.inquiry-modal__panel.iridescent-edge::after { display: none }`). The pearl gradient, the panel border, and the inset top highlight carry the polish on their own.
- This was the cleanest way to guarantee that the right edge cannot read as a duplicated line under any scrollbar behavior or browser, instead of repeatedly chasing border-color variants.
- Modal panel borders were softened on the right and bottom of the underlying `iridescent-edge` utility too, so any other component that uses the utility also benefits without exposing a double line.

Animation:

- The backdrop fades in over 180ms.
- The panel rises 8px and settles to scale 1 over 240ms with a `cubic-bezier(0.2, 0.7, 0.2, 1)` ease.
- Both animations are cancelled under `prefers-reduced-motion`.

Icons and microcopy:

- The close button now uses an inline SVG cross icon at a slightly smaller tap target (2.5rem desktop, 2.15rem mobile) so the corner reads as polished rather than oversized.
- The submit button switched from a send arrow to a check icon, reinforcing that submission opens an email draft.
- Field labels gained 0.012em tracking and stronger hover borders on inputs, textarea, and select.

Form behavior:

- The form is now `novalidate` at the element level, but the submit handler calls `checkValidity()` and `reportValidity()` so the native invalid focus and message path is retained.
- The mailto handoff remains unchanged.
- Document level inquiry trigger delegation, Escape close, outside click close, focus return, and focus trap behavior are preserved.

QA result:

- The modal was rechecked at 390px x 900px, 768px x 900px, and 1280px x 900px from `npm run preview`.
- The headline wraps to three lines at 390px, two lines at 768px, and three balanced lines at 1280px without any awkward orphan.
- The CTA and the fallback email link remain visible at 390px x 900px without scrolling the panel.
- No horizontal overflow was detected on any tested width.
- Console errors and warnings were both 0 on the preview server.

## May 17 Modal Polish Update

A focused modal UX and copy pass refined the inquiry modal further.

Copy:

- Headline shortened to "Rough idea or stubborn workflow?"
- Intro changed to "Modernization effort, product concept, or strange
  little system problem? Send over the shape of it. Jera Technologies
  will help turn it into a practical next step."
- Email fallback helper changed to "Send project details to:".
- Project category options, message label ("What needs attention?"),
  message placeholder, fallback heading, and email are unchanged.

Form hierarchy:

- The form is presented as four groups: Project category, Contact
  details, Project details, then Submit or direct email. Two aria-hidden
  uppercase scanning labels mark the Contact details and Project details
  groups. Each input keeps its own associated label.

CTA icon:

- The submit button icon changed from a checkmark to a send /
  paper-plane icon. A checkmark implied the inquiry was already
  confirmed; the send icon depicts the actual action.

Footer action area:

- The hard top border was replaced with a soft faded hairline.
- The vertical divider between the CTA and the direct email helper was
  removed; a column gap separates them on desktop.
- Spacing was loosened so the footer is not cramped.

Headline sizing:

- The headline font size was reduced so the modal headline reads as a
  modal heading rather than a page hero.

Accessibility:

- Dialog semantics, Escape close, outside click close, focus return,
  focus trap, visible focus states, native validity, and per-input
  labels remain intact. Escape close and focus return were verified in
  preview. The native select is unchanged; no custom dropdown was added.

The mailto draft behavior is unchanged.

## May 18 Modal Intro Microcopy And Wrap Update

A final microcopy and text rhythm refinement on the inquiry modal intro.
The modal design, the form structure, the accessibility behavior, and
the mailto handoff are all unchanged.

Copy:

- Intro changed to "Modernization effort, product concept, or strange
  little system problem? Send the rough shape. We'll help turn it into a
  practical next step." The previous intro named "Jera Technologies"
  literally, which broke the company name across lines in rendered QA
  and read as unpolished. The name is now dropped from the intro and
  replaced with "We'll", which keeps the tone warm and down to earth.
- The headline "Rough idea or stubborn workflow?" is unchanged.

Wrapping:

- The modal intro paragraph (.inquiry-modal__description) switched from
  text-wrap: pretty to text-wrap: balance. pretty only optimizes the
  last few lines to prevent an orphan; it left a dangling article ("a")
  at the end of a line at 390px. balance evens every line. The intro is
  three to four lines, well within the browser balancing cap.

QA result:

- Rendered QA at 390, 430, 768, 1280, and 1440 (x900): the intro wraps
  to even lines with no company-name break and no dangling article, the
  headline stays a clean two lines, the CTA and the fallback email are
  visible, there is no horizontal overflow.
- Escape close and focus return verified. Console errors and warnings 0.
- npm run build and npm run copy-check passed.

## May 18 Modal Intro Measure Composition Update

A composition fix. The microcopy and wrap update above improved the
intro but it still rendered as cramped fragments because it was
constrained too narrowly. This update fixes the modal text composition
system. The headline and intro copy are unchanged. The form structure,
the accessibility behavior, and the mailto handoff are unchanged.

Decision: the modal headline and the modal intro use separate, named
text measures.

- The headline (.inquiry-modal__title) stays compact, at the
  --measure-modal-heading token (24ch, unchanged in value, now named).
- The intro (.inquiry-modal__description) uses the new
  --measure-modal-intro token at 64ch, up from a too-narrow 50ch.
- The shared header wrapper (.inquiry-modal__header) max-width was
  widened from 43rem to 46rem so it never clips the wider intro measure.
  The headline keeps its own 24ch cap regardless of the wrapper width.
- The intro keeps text-wrap: balance. At 64ch, balance places the line
  break after the opening question and keeps the second sentence whole.

Rationale: the intro problem was a measure problem, not a copy problem.
A two-sentence intro forced into a 50ch helper-text measure can only
wrap into cramped fragments. The fix is to give the intro its own wider
measure, not to keep trimming the copy. 50ch was a leftover from the
May 15 text composition pass, which set the modal intro to a helper-like
width; that value is now corrected.

QA result:

- Rendered QA at 390, 430, 768, 1280, and 1440 (x900): at 768, 1280, and
  1440 the intro composes as two calm lines with the break after the
  opening question; at 430 and 390 it is four even lines bounded by the
  panel. The headline stays a clean two lines. CTA visible, footer and
  direct email readable, no horizontal overflow, no right edge artifact.
- Escape close and focus return to the trigger verified. Console errors
  and warnings 0.
- npm run build and npm run copy-check passed.

Remaining Vercel preview QA: recheck the modal at the five widths on the
deployed preview, confirm the mailto handoff and the native select
popup, and smoke test contact links, redirects, metadata, sitemap, and
console output.

## May 27 Contact Hierarchy: Form Primary, Email Demoted

Decision: the inquiry form is the single primary contact path. Direct
email is demoted to a quiet, secondary fallback, and the raw address is no
longer rendered as visible text anywhere on the site.

Why the form is primary over direct email:

- The structured form (category, name, email, company, message) produces
  better-organized intake than a bare email, and the category + message
  prompt help filter low-quality or off-topic messages.
- It is the foundation for future spam controls — honeypot field, rate
  limiting, Cloudflare Turnstile, structured dropdowns — none of which a
  plain `mailto:` link supports. Keeping the form primary now avoids
  re-training visitors later.

Why direct email is hidden / secondary:

- A prominently displayed raw address invites scraping and spam, and a
  second equally-weighted "Email directly" CTA competes with the form and
  blurs the intended action.
- Demoting it keeps the form the obvious choice while still giving people
  who strongly prefer email an honest, reachable path.

Implementation:

- A shared `.quiet-email-link` primitive: a small muted text link labelled
  "Prefer email?" that points at the `mailto:` href. The literal address
  is never printed as page content (it lives only in the `mailto:` href
  and the modal's submit script).
- Contact page dark panel: one `button-dark` primary ("Open inquiry form")
  plus the quiet link. The old equally-weighted white "Email directly"
  button was removed.
- Inquiry modal action area: the fallback heading, note, and raw-address
  link were replaced with the single quiet "Prefer email?" link.
- Footer Contact column: leads with "Start an inquiry" (`/contact`, with
  the inquiry-trigger so it opens the modal where JS is available) and a
  quiet "Prefer email?" beneath. The raw address was removed.

Constraints preserved (consistent with this ADR's boundaries):

- The mailto fallback remains; the contact path still works without
  JavaScript (every affordance is a real anchor — modal triggers fall back
  to `/contact` or `mailto:`).
- No backend form service was added. The form still opens a prepared
  mailto draft. No claim of successful submission was introduced.
- copy-check still passes; the address only appears in `mailto:` hrefs, not
  as forbidden visible copy.

This supersedes the earlier "direct email helper on the right" framing in
the modal action area, which displayed the raw address.

## May 28 Contact Alignment Correction (no hierarchy change)

Decision refinement: keep the May 27 hierarchy (form primary, email
demoted), but tighten the composition rule so demoted email actions remain
intentional and aligned.

Implementation refinement:

- Footer Contact column does not use a boxed mini-card treatment. It is a
  simple aligned link stack: primary `Start an inquiry` plus quiet mail-icon
  `Prefer email?`.
- Contact page dark panel keeps one primary `Open inquiry form` action and
  one quiet `Prefer email?` fallback; the primary button is content-fit and
  not forced into an unnecessarily wide block.
- Shared `.quiet-email-link` spacing and icon alignment were refined so the
  fallback reads consistently in footer, contact panel, and modal contexts.

Rules reaffirmed:

- No raw support email in visible page text.
- `mailto:` fallback remains functional and reachable without JavaScript.
- Secondary email action stays subordinate and never competes with the form
  CTA.
- Demoted actions should stay simple, aligned, and intentional. Avoid
  decorative mini-card wrappers that visually detach the fallback from the
  surrounding footer system.

## May 28 Principal Polish Addendum (surgical refinement)

Decision refinement: keep the same hierarchy and behavior, but improve how
it composes across contact surfaces.

What changed in the rule set:

- The primary contact action remains the inquiry path (`Open inquiry form`,
  `Start an inquiry`), and its sizing should be content-fit in panel
  contexts unless narrow mobile constraints require wider controls.
- The demoted fallback remains `Prefer email?` and now consistently carries a
  small mail icon so the action is legible at a glance without visual
  competition.
- Footer contact stays a simple aligned link stack (not a mini-card):
  primary line first, secondary line second, aligned with other footer
  columns.
- The same subordinate fallback pattern is used in contact panel and inquiry
  modal action areas so demotion is consistent instead of ad hoc.

What did not change:

- No backend form dependency was added.
- No-JS fallback behavior remains intact (real anchor `mailto:` links).
- Raw support email is still hidden from normal page text and remains only in
  `mailto:` hrefs and mailto draft logic.
