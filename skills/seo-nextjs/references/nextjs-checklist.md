<!-- Updated: 2026-04-26 -->
# Next.js / Vite SEO Pre-launch Checklist

Derived from recurring audit findings across JS-heavy projects. Every item here
has appeared as a gap in at least one real analysis session.

---

## Rendering Strategy

| Check | Pass condition | Severity |
|-------|---------------|----------|
| SSR or SSG enabled | Content visible in `curl` response without JS | Critical |
| Canonical in raw HTML | `<link rel="canonical">` in curl response | Critical |
| noindex/nofollow in raw HTML | `<meta name="robots">` in curl response, not JS-injected | Critical |
| Structured data in raw HTML | `<script type="application/ld+json">` in curl response | High |

**How to verify:** `curl -s <url> | grep -i "canonical\|robots\|ld+json\|title"`

---

## Metadata (every page)

| Check | Pass condition | Severity |
|-------|---------------|----------|
| Unique `<title>` | 50–60 chars, in initial HTML | Critical |
| Unique `<meta description>` | 120–155 chars, in initial HTML | High |
| Open Graph title | Present and matches title | High |
| Open Graph description | Present | High |
| Open Graph image | 1200×630px, absolute URL | High |
| Twitter card | `summary_large_image` | Medium |
| Canonical | Self-referencing on every page | Critical |

**Next.js App Router:** Use `metadata` export or `generateMetadata()` — never `document.head`.
**Next.js Pages Router:** Use `next/head` in `_app.tsx` for defaults, override per page.
**Vike/Vite SSR:** Use `+Head.tsx` page component.

---

## Schema Markup

| Check | Pass condition | Severity |
|-------|---------------|----------|
| `Organization` on homepage | Present in initial HTML | High |
| Page-type schema | Article, Product, LocalBusiness, etc. on relevant pages | High |
| `BreadcrumbList` | Present on all pages with nav hierarchy | Medium |
| `FAQPage` | Present on informational pages with Q&A sections | Medium |
| Validates at schema.org/validator | Zero errors | High |

---

## Core Web Vitals

| Check | Pass condition | Severity |
|-------|---------------|----------|
| Hero image uses `next/image` with `priority` | No `<img>` on LCP element | Critical |
| `fetchPriority="high"` on LCP image | Present | High |
| `next/font` for body/heading fonts | No Google Fonts `<link>` in `<head>` | High |
| All images have explicit `width` + `height` | No layout shift from unsized images | High |
| LCP target | < 2.5s (field data via PSI or CrUX) | Critical |
| CLS target | < 0.1 | High |
| INP target | < 200ms | High |

---

## robots.txt + Sitemap

| Check | Pass condition | Severity |
|-------|---------------|----------|
| `robots.txt` present at root | `curl <url>/robots.txt` returns 200 | High |
| Sitemap referenced in robots.txt | `Sitemap:` directive present | High |
| Sitemap valid XML | All URLs return 200, no noindex pages | High |
| AI crawler directives present | Deliberate allow or disallow for GPTBot, Google-Extended | Medium |

**App Router files:** `app/robots.ts` → `/robots.txt`, `app/sitemap.ts` → `/sitemap.xml`

---

## Security Headers

| Header | Required value | Severity |
|--------|---------------|----------|
| `Strict-Transport-Security` | `max-age=63072000; includeSubDomains` | High |
| `X-Frame-Options` | `SAMEORIGIN` | High |
| `X-Content-Type-Options` | `nosniff` | High |
| `Referrer-Policy` | `strict-origin-when-cross-origin` | Medium |
| `Permissions-Policy` | Restrict camera/mic/geo | Medium |

**Verify:** https://securityheaders.com

---

## AI Search / GEO

| Check | Pass condition | Severity |
|-------|---------------|----------|
| `llms.txt` at root | Present, describes site purpose | Medium |
| AI crawler intent deliberate | Not accidental allow/block | Medium |
| FAQ schema on informational pages | AI citation benefit (~2.5× rate) | Medium |
| Direct answers in first paragraph | No buried lede | Medium |

---

## GSC Setup

| Check | Pass condition | Severity |
|-------|---------------|----------|
| Domain property added | Not URL-prefix property | High |
| Verified via DNS TXT | Not file verification | High |
| Sitemap submitted | Shows in GSC → Sitemaps | High |
| URL Inspection run on homepage | Status: URL is on Google | High |
