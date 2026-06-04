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

## May 31 Secure Inquiry Endpoint v1 (form submits to `/api/inquiry`)

Decision: the inquiry modal now **submits to a secure backend endpoint**
instead of opening a `mailto:` draft. This supersedes the mailto-on-submit
behavior described above. Direct email is unchanged as the quiet secondary
fallback ("Prefer email?").

What changed (`src/components/inquiry/InquiryModal.astro`):

- The submit handler `fetch`-POSTs JSON to `/api/inquiry` (category, name,
  email, company, message, `turnstileToken`, `website` honeypot).
- A visually hidden, `aria-hidden`, `tabindex="-1"` honeypot field (`website`).
- A Cloudflare Turnstile widget that renders **only** when
  `PUBLIC_TURNSTILE_SITE_KEY` is set and the form is enabled.
- An `aria-live="polite"` status region for generic success/failure copy. No
  server-side validation detail is shown to the visitor.
- `PUBLIC_FORM_ENABLED` gate: when not exactly `"true"` the submit button is
  disabled and a calm "being finalized for launch" note shows — the form never
  fakes a successful send.

Category contract: option values are now slugs (`applied-ai`,
`enterprise-modernization`, `workflow-automation`, `architecture-integration`,
`decision-support-systems`, `product-strategy`, `not-sure-yet`) that the
endpoint validates against. Display labels are unchanged. The endpoint maps the
slug back to the label for the email body. Keep the two lists in sync.

Accessibility unchanged: dialog semantics, Escape close, outside-click close,
focus entry/return, focus trap, visible focus, native validity, per-input
labels. The honeypot is removed from the a11y tree and tab order.

Endpoint, env vars, Turnstile/Resend setup, security controls, rate-limiting
stance, and the launch checklist live in
`02-website/inquiry-endpoint-deployment.md`. The "Boundaries: do not add a
backend form submission service in this slice" constraint above was scoped to
the earlier static slice; v1 of the secure endpoint is the approved successor.

## June 1 Form-Only Contact (mailto fallback removed for v1)

Decision: for v1 and soft launch the **only** public contact path is the
secure inquiry form. The "Prefer email?" `mailto:` fallback is **removed** from
all public UI. This supersedes every earlier section that demoted-but-kept the
mailto fallback (May 27, May 28 x2, and the "Direct email is unchanged as the
quiet secondary fallback" line in the May 31 section). It also reverses the
earlier boundary "Do not remove the mailto fallback" and the accessibility note
"The form keeps a visible fallback email link."

Why direct email was removed:

- A `mailto:` href cannot be secured — the destination address is exposed in
  the page source to anyone who inspects or clicks it, and it is trivially
  scraped. Email obfuscation is weak and hurts accessibility, so it is not a
  real mitigation.
- The form is the stronger path: it carries Turnstile, a honeypot, validation,
  origin checks, and server-side delivery. The mailto fallback bypasses all of
  those spam controls.
- The receiving inbox is configured **server-side only** via `CONTACT_TO_EMAIL`
  (Vercel env). No public personal email or support alias appears in page text
  or hrefs. `src/config/site.ts` no longer exports any email or `mailto:` value.

Form-disabled honesty (soft launch): when `PUBLIC_FORM_ENABLED` is not exactly
`"true"`, the submit button is disabled and the modal shows a calm note —
"Inquiry submission is being finalized for soft launch." No mailto fallback is
offered; the page is not a dead end because the form and its message remain the
clear, single contact affordance.

Implementation:

- `src/config/site.ts`: removed `contactEmail`, `contactMailtoSubject`, and the
  `contactMailtoHref` export.
- `InquiryModal.astro`: removed the "Prefer email?" `.quiet-email-link` from the
  action area; the primary "Send inquiry" button now spans the action row.
  Status/error/disabled copy no longer references an email link.
- `Footer.astro`: Contact column is now just "Start an inquiry" (`/contact`,
  inquiry-trigger). The quiet email link was removed.
- `contact.astro`: dark panel keeps the single "Open inquiry form" button; its
  no-JS `href` now points to `/contact` instead of a `mailto:`. The quiet email
  link was removed.
- `global.css`: the now-orphaned `.quiet-email-link*` and
  `.inquiry-form__fallback` rules were deleted, and the modal action area was
  collapsed from a two-column (button + fallback) grid to a single full-width
  primary button.

Verification: `npm run build` and `npm run copy-check` pass across 9 HTML files;
a `dist/` scan finds no `mailto:`, no `support@…`, and no raw support address in
visible text or hrefs (only the visitor's own `you@example.com` input
placeholder remains).

## June 1 Success UX: Modal Close + Toast (transient popup eliminated)

Decision: a successful submission now **closes the modal gracefully and shows a
toast** outside the modal, instead of leaving an inline success status inside an
open modal. Failures stay inline. This is a UX-only change — the endpoint, the
security controls (Turnstile, honeypot, validation, origin checks, Resend), and
the form-only contact rule are unchanged.

Likely source of the reported "faint popup / brief flash" on success: the old
success path called `window.turnstile.reset()` while the modal — and the
Turnstile widget — were still open and visible. Resetting a visible managed
Turnstile widget can briefly render its interaction/verification overlay, which
reads as a transient popup. A secondary contributor is the browser's
autofill / "save info" bubble that any in-place submit of a form with
name/email fields can surface. There is **no** `alert()`, `confirm()`,
`window.open`, `mailto:`, `target="_blank"`, or native form navigation in the
flow — `event.preventDefault()` is the first line of the submit handler, and the
form is `novalidate` (so the only validation bubble is the deliberate
`reportValidity()` on the invalid path, never on success).

Fix: on success the modal closes first (which removes the widget from view), so
the subsequent `turnstile.reset()` — kept so a re-open gets a fresh token —
cannot flash an overlay. Confirmation moves to a toast that is a real product
surface, not a browser alert.

Success flow (`InquiryModal.astro`):

1. `event.preventDefault()`; a `isSubmitting` guard blocks duplicate submits
   while a request is in flight (submit button is also disabled during the
   request).
2. On `response.ok && data.ok`: reset the form, reset Turnstile, clear the
   inline status, close the modal (focus returns to the trigger), show the toast.
3. The honeypot path routes through the **same** success handler, so a bot sees
   the identical outcome and no signal leaks.

Toast design (premium surface, treated like a product component — not an alert):

- Pearl material (white→cool radial wash), a blue/cyan edge-light hairline, a
  soft layered shadow, and a small blue→cyan gradient check icon. No loud green
  box, no cheap animation.
- Copy: a short bold title "Inquiry sent" with the reassurance as the quieter
  supporting line "We’ll be in touch soon." Title/note use `text-wrap: balance`
  so any wrap stays even with no single-word orphan or mid-word break.
- Fixed bottom-right on desktop; full-width within gutters at ≤30rem (verified
  at 390px: within viewport, no horizontal overflow).
- Accessible: `role="status"` + `aria-live="polite"`, a keyboard-reachable
  dismiss button with visible focus, auto-dismiss after ~5.2s, and motion that
  the global `prefers-reduced-motion` rule neutralizes while keeping it visible.

Failure flow: modal stays open; inline status shows the generic
"Something went wrong sending your inquiry. Please try again in a moment." No
backend detail is exposed and no popup is shown. The earlier catch-block copy
that still said "or use the email link below" (a leftover from the removed
mailto) was corrected to the generic message.

Verification: `npm run build` + `npm run copy-check` pass (9 HTML files); a
`dist/` scan finds no `mailto:`, `support@…`, `alert(`, or `window.open`. The
toast was rendered at 390px in a local preview to confirm the premium look and
no overflow. The full live success path (real Turnstile + Resend on Vercel)
must be smoke-tested on a preview deployment — it cannot run under
`astro preview`/`dev`.

## June 1 In-Modal Success State (toast removed; ghost rectangle fixed)

Decision: this **supersedes the toast** above. A successful submission now keeps
the modal open and **transitions the same modal from its form view to an in-modal
success view**. The toast system is removed entirely. Failure stays inline in the
form as a polished two-line block. UX-only — endpoint, Turnstile, honeypot,
validation, origin checks, and Resend are unchanged.

Cause of the reported "faint rectangular ghost surface": it was the **toast**.
The toast was `position: fixed`, `z-index: 120`, with a pearl background, border,
and shadow, and it auto-dismissed after ~5.2s. Submitting once, then re-opening
the inquiry modal within that window, left the toast still present *behind* the
modal panel — appearing as a faint translucent rectangle across the lower-right
of the panel (through the Turnstile area). Clicking the backdrop closed the modal
and the toast then timed out, so "clicking away made it disappear." Confirmed via
the screenshot geometry and the toast's fixed positioning/z-index. (Not an
`alert`/`confirm`/`window.open`/`mailto`/native-submit issue — none exist in the
flow; `event.preventDefault()` is still the first line and the form is
`novalidate`.)

Why a same-modal success state (not a toast): a toast is a transient corner
surface that (a) can leave a layer behind the modal — the ghost — and (b) is easy
to miss for something as deliberate as a project inquiry. An in-modal success
state cannot leave a stale layer behind the modal and is impossible to miss.

Why no "Send another inquiry": it was considered as an optional secondary action
and briefly implemented, then removed at the user's direction — after sending,
the modal should simply confirm and offer **Close**, not invite another send.

Success flow (`InquiryModal.astro`), a small state machine — idle / submitting /
success / error:

1. `event.preventDefault()` (first line); an `isSubmitting` guard + disabled
   submit button block duplicate submissions.
2. On `response.ok && data.ok` (and the honeypot path): clear the submitting
   flag, reset the form, clear status + error, **hide the form view, show the
   success view**, then `turnstile.reset()` (now off-screen → cannot flash), and
   move focus into the success view.
3. Opening always forces the form view and clears any error; closing from the
   success view restores the form view — so no confirmation layer can linger
   behind a future open.

Success view design (premium product surface, not an alert, not a toast):

- Pearl-consistent with the panel; a small blue→cyan gradient check, title
  "Inquiry sent.", supporting line "Thanks for sharing the details. We'll review
  it and be in touch soon.", and a single **Close** button. No green box, no
  floating corner toast, no entrance animation (no cheap motion).
- Accessible: container is `role="status"` + `aria-live="polite"`, focus moves
  into it on success (announced), `tabindex="-1"` keeps it out of the tab cycle,
  Close is keyboard-reachable with visible focus, focus returns to the trigger on
  close. The focus trap still filters hidden views.

Failure view: the form view stays; a calm two-line block (`role="alert"`) shows
title "Inquiry was not sent." and line "Please try again in a moment." — a soft
rose surface, restrained border, generic and leak-free. This replaces the long
red single-paragraph status.

No browser popups, alerts, mailto fallbacks, native navigation, stale toasts, or
invisible ghost layers are allowed in this flow. The secure inquiry form remains
the only public contact path.

Verification: `npm run build` + `npm run copy-check` pass (9 HTML files); a
`dist/` scan finds no `mailto:`, `support@…`, `alert(`, `window.open`, or
`inquiry-toast`. Rendered in a local preview at 390px: the modal opens on the
form view (success/error hidden, no toast element in the DOM, no horizontal
overflow); the success view renders with only Close and focus lands on it; the
two-line failure block renders as two clean lines. The full live success path
(real Turnstile + Resend on Vercel) still must be smoke-tested on a preview
deployment — it cannot run under `astro preview`/`dev` (the form is also gated by
`PUBLIC_FORM_ENABLED` locally).

## June 4 Form Quality Pass: validation, error surface, success close

Three refinements; no change to the endpoint, Turnstile/Resend, honeypot, origin
checks, or the form-only contact rule.

**Success view loses its internal Close.** The success view previously held a
"Close" button. Removed — the modal already provides three exits (top-right X,
Escape, backdrop click) and the success container takes focus (`role="status"`,
`tabindex="-1"`) so it is announced. In the success state the only focusable
element is the X (verified), so there is no accessibility need for an internal
button; it was redundant. The success state now reads as a calm, complete
confirmation with no extra action bar.

**Error styling — restrained clay surface, not a harsh paragraph.** The inline
send-failure block is now a flex layout: a small clay alert icon plus a body with
title "Inquiry was not sent." (deep clay `#8f3a26`, weight 700) and a quieter line
"Please try again in a moment." (`--color-muted-strong`). Surface is a soft clay
wash (`rgba(176,75,55,0.07→0.035)`) with a restrained `rgba(176,75,55,0.26)`
border and an inset highlight — tone-signalling, palette-consistent, generic, and
leak-free. `role="alert"`.

**Client-side validation — graceful, accessible, inline.** Native
`checkValidity()`/`reportValidity()` (ugly browser bubbles) were replaced with a
custom inline system:

- Each field has a `<p class="inquiry-field__error">` wired via
  `aria-describedby`; on failure the field gets `aria-invalid="true"` (which
  drives a restrained clay border + soft clay focus ring) and the message shows.
- On submit, every field is validated; the inline messages render and focus moves
  to the **first** invalid field (announced via its describedby). No POST occurs.
- Errors live-clear: once a flagged field is corrected (`input`/`change`), its
  message clears. New errors are never introduced mid-typing — only relaxed.
- Bounds and the email shape **mirror `api/inquiry.ts` exactly** — category in the
  allowlist; name 2–120; email ≤200 and `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`; company
  ≤200; message 20–4000 — so the client never rejects what the server accepts nor
  waves through what it rejects. **Client validation is UX only; the server
  remains the source of truth and is unchanged.** Messages are human and calm and
  expose no server internals.
- Missing Turnstile is now a graceful inline message under the widget
  (`role="alert"`: "Please complete the verification, then send again.") rather
  than a generic-feeling status line. The honeypot is untouched and still hidden.

State machine (`InquiryModal.astro`) — idle / clientInvalid / submitting /
success / serverError / formDisabled / turnstilePending. Each transition fully
clears stale UI: opening forces the form view and clears field/turnstile/server
errors; success resets the form, clears all errors, hides the form view, then
resets Turnstile off-screen; serverError keeps the form view and shows the clay
block; an `isSubmitting` guard + disabled submit prevent duplicates. No toast,
popup, alert, native navigation, mailto fallback, or ghost layer exists.

Verification (local `astro preview`, 390px, throwaway build with
`PUBLIC_FORM_ENABLED=true` and Cloudflare's public always-pass Turnstile test key
`1x…AA` — `.env.local` untouched; the shipped build is rebuilt clean):

- Empty submit → 4 inline errors (category/name/email/message; company optional),
  focus on the first invalid, no native bubble, no overflow, 0 console errors.
- Bad email → "Please enter a valid email address."; short message → "…at least
  20 characters."; both live-clear on correction.
- Valid data + test token → real POST (404 under preview) → clay error block,
  modal stays on the form view.
- Success view: 0 internal buttons, focus on the container, only the X focusable;
  Escape, backdrop, and X all close; reopening returns a clean, reset form.
- `dist` scan: no `mailto:`, `support@…`, `alert(`, `window.open`, or
  `inquiry-toast`; clean build does not contain the test key.

Live success (real Turnstile + Resend on Vercel) still must be smoke-tested on a
preview deployment.

## June 4 Success Composition (tighten copy, center, fix awkward wrap)

Problem: the success supporting line wrapped awkwardly — "…We'll review it and"
/ "be in touch soon." — and the block looked stranded. Cause: `.inquiry-success`
was left-aligned (`justify-items: start`) and narrow (`max-width: 42ch`) inside a
wide panel, and the longer Option B line orphaned its tail.

Decision: compose the success view as a deliberate, centered confirmation
surface, and use the shorter copy so it renders cleanly without forcing a bad
break.

- Copy is now **Option A**: title "Inquiry sent.", line "Thanks for sharing the
  details. We'll be in touch soon." (Option B's "review it and" was the source of
  the orphan and was dropped — extra words were not worth a bad wrap.)
- `.inquiry-success` is centered (`justify-items: center`, `text-align: center`,
  `margin-inline: auto`, `max-width: 34rem`) with calmer clamped vertical padding,
  so the icon, title, and copy read as one grouped, finished surface rather than
  leftover form content.
- `.inquiry-success__note` uses `max-inline-size: 26ch` + `text-wrap: balance` so
  the two sentences land as two even lines ("Thanks for sharing the details." /
  "We'll be in touch soon.") instead of relying on default wrapping. The title
  also gets `text-wrap: balance`.

Unchanged: same-modal success pattern, no internal close button, X / Escape /
backdrop close, `role="status"` + focus announcement, the polished clay error
block, and the accessible inline validation.

Verification (local `astro preview`, throwaway enabled build): rendered line
measurement confirms the note is exactly two even lines at **both 1280px and
390px**, the block is centered in the panel, no horizontal overflow; Escape,
backdrop, and X still close; reopening returns a clean form; empty submit still
yields 4 inline field errors with focus on the first; the error block markup is
intact. `npm run build` + `npm run copy-check` pass; `dist` scan finds no
`mailto:`, `support@…`, `alert(`, `window.open`, or `inquiry-toast`; the clean
build ships Option A copy and not the test key.

## June 4 Initial-Open Ghost Rectangle (backdrop-filter + transform)

Symptom: on first open of the modal — before any interaction — a faint
rectangular pale box appeared behind the lower/right form area and vanished on
any click. This was NOT the old toast (long removed) and not a post-submit
artifact; it showed on initial render.

Cause: the modal panel (`.inquiry-modal__panel`) carried the shared
`.pearl-panel` class, which applies `backdrop-filter: blur(18px)`. The panel
also runs the `inquiry-rise` entrance **transform** animation and sits inside
the overlay's own `backdrop-filter: blur(20px)`. A backdrop-filter on a
transforming element nested inside another backdrop-filter is a known Chromium
compositing bug: it leaves a stale snapshot of the panel's backdrop as a faint
rectangle until the next repaint (a click) clears it. Diagnosis was by computed
style + toggling classes in a live preview; screenshots do NOT capture it
(taking a screenshot forces the repaint that clears it), which is itself the
tell that it is a GPU compositing ghost, not a painted element. Turnstile, the
hidden success/error views, and the honeypot were all transparent with no
filters and were ruled out.

Fix: remove the `pearl-panel` class from the modal panel. The
`.inquiry-modal__panel` rule already defines its own full background, border,
and box-shadow, so `.pearl-panel` contributed **only** the unwanted
`backdrop-filter` — dropping the class removes the blur with zero visual change.
The overlay keeps its own blur (and runs only an opacity fade, not a transform),
so the page behind the modal is still blurred and the panel still reads as a
pearl surface.

Minifier trap (important): the first attempted fix —
`.inquiry-modal__panel { backdrop-filter: none }` — did **not** work. `none` is
the property's initial value, so the CSS minifier (lightningcss) stripped the
standard `backdrop-filter: none` as redundant while keeping only
`-webkit-backdrop-filter: none`; the standard property then still cascaded
`blur(18px)` from `.pearl-panel`. Lesson: you cannot reliably override an
inherited filter/transform to its initial value via a same-or-lower-specificity
rule, because the minifier drops initial-value declarations. Remove the source
class (or the source declaration), do not set the property to `none`.

Rules going forward:
- Hidden modal states must not remain painted, and the panel must not stack a
  `backdrop-filter` on a transforming element nested inside another
  `backdrop-filter` — that combination creates compositing ghosts. One blur
  layer (the overlay) is enough.
- The Turnstile wrapper must stay visually contained and transparent inside the
  modal (it already is: transparent background, no filter); it was not the
  source here but the rule stands so it never becomes one.

Verification (local `astro preview`, enabled throwaway build): computed
`backdrop-filter` on the panel is now `none` (overlay still `blur(20px)`); the
panel keeps its gradient background (no visual regression); Turnstile renders;
empty submit still yields 4 inline field errors with focus on the first; the
success view is two balanced lines; the clay error block is intact; X, Escape,
and backdrop all close; reopening is clean; no overflow at 390px. Clean rebuild:
`build` + `copy-check` pass; `dist` has no `mailto:`/`support@…`/`alert(`/
`window.open`/`inquiry-toast` and the panel no longer carries `pearl-panel`.
