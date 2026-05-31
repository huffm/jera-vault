# Soft Launch & Noindex

## Date

May 31, 2026

## Purpose

During soft launch the Jera Technologies site is publicly reachable but must
stay **out of search indexes**. A single switch, `PUBLIC_SOFT_LAUNCH`, drives
that behaviour in the application layer, with a belt-and-braces Vercel header
as a static backstop.

## The switch: `PUBLIC_SOFT_LAUNCH`

- Astro exposes any `PUBLIC_`-prefixed env var to build/client code via
  `import.meta.env.PUBLIC_SOFT_LAUNCH`.
- Value is a **string**. Only the exact string `"true"` enables soft launch;
  anything else (including unset) is treated as public.
- Read in exactly two places (grep `PUBLIC_SOFT_LAUNCH` in `jera-site/src`).

## What it controls

1. **Robots meta tag** — `jera-site/src/components/seo/SEO.astro`
   - Soft launch on → every page emits
     `<meta name="robots" content="noindex,nofollow,noarchive" />`.
   - Soft launch off → falls back to the per-page `noindex` prop
     (`noindex, nofollow`) only where a page asks for it.
2. **robots.txt** — `jera-site/src/pages/robots.txt.ts` (Astro static endpoint,
   built to `dist/robots.txt`)
   - Soft launch on → `User-agent: *` / `Disallow: /`.
   - Soft launch off → `Allow: /` plus the `Sitemap:` line pointing at
     `sitemap-index.xml`.

## The Vercel backstop (NOT flag-driven)

- `jera-site/vercel.json` has a `headers` block sending
  `X-Robots-Tag: noindex, nofollow, noarchive` on `/(.*)`.
- Vercel header config is **static** — it cannot read `PUBLIC_SOFT_LAUNCH`. It
  is unconditional and applies on every deploy until removed.
- It is flagged with a `$comment` in the file as soft-launch-only.

## Where env vars are set

- **Local:** `jera-site/.env.local` (git-ignored via `.env*`; never committed).
  Currently contains `PUBLIC_SOFT_LAUNCH=true`.
- **Template:** `jera-site/.env.example` (committed; placeholders only, no real
  secrets). The `.gitignore` has a `!.env.example` exception so it survives the
  `.env*` ignore rule.
- **Vercel:** set `PUBLIC_SOFT_LAUNCH` under Project → Settings → Environment
  Variables for each environment (Production / Preview). It must be present at
  **build time** because Astro inlines `PUBLIC_*` values during the build.

## Before public launch — checklist

1. Set `PUBLIC_SOFT_LAUNCH=false` (or remove it) in Vercel **and** local
   `.env.local`, then rebuild — this clears the robots meta and flips
   `robots.txt` to `Allow: /` + sitemap.
2. **Remove the `headers` block from `vercel.json`** (the static
   `X-Robots-Tag` noindex). This is the easiest step to forget; it silently
   keeps the site de-indexed even after the flag is off.
3. Rebuild and confirm `dist/`:
   - No `<meta name="robots" content="noindex...">` on public pages.
   - `dist/robots.txt` shows `Allow: /` and the `Sitemap:` line.
4. Verify a deployed response has no `X-Robots-Tag` header.
5. Submit/refresh the sitemap in search console once indexing is intended.

## Verification commands

```
cd jera-site
npm run build        # builds dist/, including robots.txt
npm run copy-check   # restricted-copy scan over dist/*.html
```

Then inspect `dist/` for the robots meta and `dist/robots.txt` contents.
