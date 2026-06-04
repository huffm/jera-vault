# Inquiry Endpoint — Deployment & Operations (v1)

## Date

May 31, 2026

## Summary

The inquiry form is the primary contact path. It posts JSON to a Vercel
Function at `POST /api/inquiry`, which verifies a Cloudflare Turnstile token,
validates the payload, and sends the inquiry via Resend to the Jera inbox. The
Astro site stays **fully static** — no SSR adapter, no `output: "server"`. The
function file (`jera-site/api/inquiry.ts`) is detected by Vercel independently
of the static build.

For v1 / soft launch the inquiry form is the **only** public contact path.
There is no public `mailto:` fallback (see "Contact is form-only" below).

## Architecture decision

- **Platform:** Vercel. Static Astro + root-level Vercel Function.
- **Why not SSR:** A root `api/*.ts` function covers the one dynamic need
  (form POST) without converting the whole site to SSR. Converting would add an
  adapter, change the build/runtime model, and slow every page for one endpoint.
- **Why no SDKs:** Turnstile and Resend are called over their REST APIs with
  `fetch`, so v1 adds **zero npm dependencies**.

## Required environment variables (set in Vercel → Settings → Env Vars)

Public (exposed to the browser — safe by design):

| Var | Purpose |
| --- | --- |
| `PUBLIC_SOFT_LAUNCH` | `true` keeps the site noindexed (meta + robots.txt). |
| `PUBLIC_FORM_ENABLED` | Must be exactly `true` for the form to actually submit. |
| `PUBLIC_TURNSTILE_SITE_KEY` | Turnstile widget site key. Blank → widget not rendered. |

Secret (server-only — NEVER expose, never commit):

| Var | Purpose |
| --- | --- |
| `TURNSTILE_SECRET_KEY` | Server-side Turnstile verification. |
| `RESEND_API_KEY` | Resend transactional email auth. |
| `CONTACT_TO_EMAIL` | Destination inbox (the Jera alias). |
| `CONTACT_FROM_EMAIL` | Fixed verified sender. NOT the visitor's email. |
| `CONTACT_ALLOWED_ORIGINS` | Comma-separated origins allowed to POST. |

`PUBLIC_*` values are inlined at **build time** — changing them requires a
redeploy. Secret values are read at **runtime** in the function.

## Configuring Turnstile

1. Cloudflare dashboard → Turnstile → add a widget for the site domain(s).
2. Copy the **site key** → `PUBLIC_TURNSTILE_SITE_KEY` (public).
3. Copy the **secret key** → `TURNSTILE_SECRET_KEY` (secret).
4. The widget script loads only when the site key is present; the token is sent
   as `turnstileToken` and verified server-side against
   `https://challenges.cloudflare.com/turnstile/v0/siteverify`.

## Configuring Resend

1. Resend → add and **verify the sending domain** (DNS: SPF, DKIM, and a DMARC
   policy). Deliverability depends on this.
2. Create an API key → `RESEND_API_KEY` (secret).
3. `CONTACT_FROM_EMAIL` must be an address on the verified domain
   (e.g. `no-reply@jeratechnologies.com`). It is the fixed `From`.
4. The **visitor's** email is used only as `Reply-To`, never as `From` and
   never placed in headers without CR/LF normalization.
5. `CONTACT_TO_EMAIL` is where inquiries land (the alias, e.g.
   `inquiries@jeratechnologies.com`).

## Security controls implemented

- POST-only (Vercel returns 405 for other methods).
- `Content-Type: application/json` required (else 415).
- Body size capped at 8 KB (content-length + actual bytes; else 413).
- Safe `JSON.parse` (else 400).
- Allowlist validation: category against a fixed set; name/email/company/
  message length bounds; message min 20 / max 4000.
- Honeypot field `website` — if filled, the request is silently accepted and
  dropped (no signal to bots).
- Mandatory Turnstile token, verified server-side.
- Origin allowlist check against `CONTACT_ALLOWED_ORIGINS`.
- Generic error responses — no field-level validation leakage.
- Email body uses plain text plus fully HTML-escaped content; no raw user HTML.
- Subject and Reply-To are CR/LF-normalized (no header injection).
- No secrets and no full inquiry bodies are logged.

## Rate limiting recommendation

v1 has **no application-level rate limiter**. An in-memory `Map` in a
serverless function gives false confidence — instances are ephemeral and scaled
horizontally, so counters do not hold. Real protection is edge-level:

- **Vercel WAF** rate-limiting rules on `/api/inquiry`, or
- **Cloudflare** rate limiting if the domain is proxied through Cloudflare.

Turnstile + honeypot + body limits + origin checks are the in-app defenses.

## Contact is form-only (no public email)

For v1 and soft launch the secure inquiry form is the **single** public contact
path. The previous quiet "Prefer email?" `mailto:` fallback was **removed** from
the contact page, inquiry modal, and footer (ADR 0006, June 1 2026).

- **Why removed:** a `mailto:` href cannot be secured — the destination address
  is exposed in page source to anyone who inspects or clicks it, and is trivially
  scraped. Obfuscation is weak and hurts accessibility, so it was never real
  protection. The form, by contrast, enforces Turnstile, the honeypot,
  validation, origin checks, and server-side delivery; a mailto bypasses all of
  them.
- **No address in the client.** `src/config/site.ts` no longer exports any email
  or `mailto:` value (`contactEmail` / `contactMailtoHref` were deleted). A
  `dist/` scan finds no `mailto:` and no `support@…` in visible text or hrefs.
- **The receiving inbox stays server-side only.** Inquiries are delivered to
  `CONTACT_TO_EMAIL` (Vercel secret env, read at runtime in `api/inquiry.ts`). It
  must never be exposed client-side and appears only as a placeholder in
  `.env.example`. Always use a shared **alias**, never a personal inbox. Keep
  SPF/DKIM/DMARC on the domain and mailbox spam filtering as the delivery-side
  defenses.
- **Disabled-form honesty:** when `PUBLIC_FORM_ENABLED` is not `true`, the modal
  shows a calm "Inquiry submission is being finalized for soft launch." and the
  submit button is disabled — no mailto fallback, and the form is never faked as
  sent.

## Success / failure UX (client)

On success the inquiry modal **swaps its own content from the form to an in-modal
success view** — there is no toast, no browser alert, no mail-client popup, and
no transient overlay. Failure stays inline in the form. See ADR 0006
("June 1 In-Modal Success State") for the full decision and the ghost-rectangle
post-mortem.

- **Success:** the same modal transitions form view → success view. Sequence:
  clear the submitting flag → reset the form → clear status/field/server errors →
  hide the form view → show the success view → reset Turnstile (now off-screen, so
  it cannot flash) → move focus into the success view (`role="status"`,
  announced). Success view: a blue/cyan check, title "Inquiry sent.", line "Thanks
  for sharing the details. We'll review it and be in touch soon." There is
  intentionally **no internal action button** (no "Close", no "Send another") —
  the modal's top-right X, Escape, and backdrop click are the ways out, and the
  success container takes focus so it is announced (in this state the X is the
  only focusable element, so no internal button is needed).
- **Client validation (UX only; server authoritative):** the modal validates
  inline before POST — category required (allowlist), name 2–120, email ≤200 and
  a basic shape, company ≤200, message 20–4000, Turnstile present — **mirroring
  `api/inquiry.ts` exactly**. Failures show per-field messages (wired via
  `aria-describedby` + `aria-invalid`, restrained clay styling) and focus the
  first invalid field; no native browser bubbles. The server re-validates
  everything and remains the source of truth — client checks are never trusted by
  the endpoint and expose no server internals.
- **Why in-modal, not a toast:** the earlier toast was a fixed-position pearl
  surface that auto-dismissed after ~5s. Reopening the modal within that window
  left the toast sitting *behind* the modal panel as a faint translucent
  rectangle (the reported "ghost box"); clicking the backdrop dismissed it. An
  in-modal success state cannot leave a layer behind the modal and is harder to
  miss for a project inquiry. The toast system (markup, JS, CSS) was removed.
- **Why Turnstile is reset only after the form view is hidden:** resetting a
  *visible* managed Turnstile widget can briefly flash its challenge overlay.
  Hiding the form view first makes the reset off-screen and invisible.
- **Failure:** the modal stays open on the form view and shows a calm two-line
  block (`role="alert"`): title "Inquiry was not sent." and line "Please try
  again in a moment." No backend detail is exposed, no popup. (The long
  single-paragraph error was replaced.)
- **Duplicate submits** are blocked by an `isSubmitting` guard plus the disabled
  submit button while a request is in flight. The honeypot path runs the same
  success transition so a bot sees an identical outcome.
- **No stale layers:** opening always forces the form view and clears any error;
  closing from the success view restores the form view for the next open.

This is UX only — the endpoint, Turnstile/Resend, validation, origin checks, the
honeypot, and the form-only contact rule are unchanged.

## How to test the endpoint

Local dev note: `astro dev` does not run Vercel Functions. Test the function
with `vercel dev` (Vercel CLI) or against a preview deployment. Expected
behaviors (replace `$BASE` with the deployment origin):

```bash
# Wrong method → 405 (only POST is exported)
curl -i -X GET "$BASE/api/inquiry"

# Wrong content type → 415
curl -i -X POST "$BASE/api/inquiry" -H "Content-Type: text/plain" --data "x"

# Missing Turnstile token → generic 400 "Verification required."
curl -i -X POST "$BASE/api/inquiry" \
  -H "Content-Type: application/json" \
  -H "Origin: https://jeratechnologies.com" \
  -d '{"category":"applied-ai","name":"Jane Doe","email":"jane@example.com","company":"Example Co","message":"This is a sufficiently long test message.","website":"","turnstileToken":""}'

# Disallowed origin → 403 "Origin not allowed."
curl -i -X POST "$BASE/api/inquiry" \
  -H "Content-Type: application/json" -H "Origin: https://evil.example" \
  -d '{}'
```

When secret env vars are **not configured**, a request that passes validation
returns a generic `502 "Unable to send right now. Please try again later."`
and the server logs a non-sensitive misconfiguration line (no secret values).

## Keeping soft launch noindexed

Unchanged from `soft-launch-and-noindex.md`: `PUBLIC_SOFT_LAUNCH=true` keeps the
robots meta + `robots.txt Disallow: /`, and `vercel.json` sends the
`X-Robots-Tag` backstop. The form can be enabled (`PUBLIC_FORM_ENABLED=true`)
during soft launch independently of indexing.

## What changes before public launch

1. Set all secret env vars in Vercel (Turnstile, Resend, contact addresses,
   allowed origins).
2. Set `PUBLIC_FORM_ENABLED=true` and `PUBLIC_TURNSTILE_SITE_KEY` (redeploy).
3. Verify domain auth (SPF/DKIM/DMARC) and send a real test inquiry.
4. Add Vercel WAF / Cloudflare rate limiting on `/api/inquiry`.
5. When ready to be indexed: `PUBLIC_SOFT_LAUNCH=false` and remove the
   `vercel.json` `X-Robots-Tag` headers block (see soft-launch doc).
