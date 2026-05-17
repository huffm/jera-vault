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
