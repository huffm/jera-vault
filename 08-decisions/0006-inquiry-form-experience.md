# 0006 Inquiry Form Experience

## Status

Accepted

## Date

May 12, 2026

## Context

The public site needs a more refined project inquiry experience before Vercel preview, but it should remain static and launch ready. There is no approved backend form service yet, and the site should not imply that messages are submitted to an API when they are not.

The inquiry flow should help Jera Technologies understand what service area, project stage, and timeline the visitor is asking about while staying easy to fill out on mobile and desktop.

## Decision

Use a lightweight accessible inquiry modal implemented with Astro markup and minimal vanilla JavaScript.

The modal opens from project-oriented CTAs such as `Discuss a project`, `Contact Jera Technologies`, and related service/product CTAs when JavaScript is available. Fallback links continue to route to `/contact` or mailto.

The modal fields are:

- Service area.
- Project stage.
- Timeline.
- Name.
- Email.
- Message.

Submission opens a prepared mailto draft to `support@jeratechnologies.com` using the subject `Project Conversation with Jera Technologies`. The body includes the selected field values and visitor message.

## Accessibility Notes

- The modal uses `role="dialog"` and `aria-modal="true"`.
- The modal is labelled by its heading and described by its intro paragraph.
- Escape closes the modal.
- Clicking outside the panel closes the modal.
- The close button has an accessible label.
- Focus moves into the modal on open and returns to the triggering element on close.
- The form keeps a visible fallback email link.

## Boundaries

- Do not add React or Preact.
- Do not add a backend form submission service in this slice.
- Do not claim the form sends successfully.
- Do not remove the mailto fallback.
- Keep the site static and Vercel preview ready.

## Consequences

Positive:

- The inquiry experience feels more intentional than a plain email link.
- Visitors can identify service area, project stage, and timeline before opening the email draft.
- Launch remains low risk because no backend dependency is introduced.
- The contact path remains accessible without JavaScript.

Tradeoffs:

- Visitors still need a local email client or browser email handler for the final send action.
- A real backend form may be needed later if mailto creates friction.

## QA Result

Responsive QA checked the modal at 390px and 1280px.

Results:

- Modal opened from the project CTA.
- Six fields were present.
- Service area selection worked.
- Mailto fallback pointed to `support@jeratechnologies.com`.
- Escape close worked.
- No horizontal overflow was detected.
- No console errors were reported.

The broader responsive QA sweep checked 360, 390, 430, 768, 1024, 1280, and 1440 widths across all public routes and found 0 failures.
