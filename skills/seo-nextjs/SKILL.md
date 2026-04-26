---
name: seo-nextjs
description: >
  Next.js and Vite SEO specialist. Audits framework-specific SEO patterns:
  rendering strategy (SSR/SSG/CSR), App Router metadata API, JSON-LD in
  initial HTML, next/image LCP, next/font CLS, security headers, robots.ts,
  sitemap.ts, and AI crawler directives. Use when user says "Next.js SEO",
  "Vite SEO", "React SEO", "framework SEO", "setup SEO for my project", or
  when a Next.js or Vite project is detected during a full audit.
user-invokable: true
argument-hint: "<url or 'setup'>"
license: MIT
metadata:
  author: furiber
  version: "1.0.0"
  category: seo
---

# SEO: Next.js / Vite Framework SEO

**Invocation:** `/seo nextjs <url>` to audit an existing project, or `/seo nextjs setup` for a new project checklist.

Audits Next.js (App Router and Pages Router) and Vite (with SSR/Vike or prerendering) projects
against a framework-specific SEO checklist derived from recurring audit findings.

## Commands

| Command | What it does |
|---------|-------------|
| `/seo nextjs <url>` | Full framework SEO audit against the checklist |
| `/seo nextjs setup` | Generate setup checklist and code templates for a new project |
| `/seo nextjs rendering <url>` | Check rendering strategy only (SSR vs CSR vs SSG) |
| `/seo nextjs schema <url>` | Check JSON-LD presence in initial HTML (not JS-injected) |
| `/seo nextjs vitals <url>` | Check next/image, next/font, CWV patterns |

## Orchestration Logic

### For `/seo nextjs <url>`

1. Fetch the page with `scripts/fetch_page.py` and capture raw HTML (before JS execution)
2. Delegate to `seo-nextjs` agent with the raw HTML
3. Agent checks all checklist categories and scores each
4. Cross-delegate to `seo-technical` for full technical audit if not already run
5. Present findings as a framework SEO scorecard
6. Offer: "Generate a PDF report? Use `/seo google report full`"

### For `/seo nextjs setup`

1. Read `references/nextjs-checklist.md` and `references/nextjs-code-patterns.md`
2. Ask: Next.js App Router, Pages Router, or Vite?
3. Ask: deployment target (Vercel, Netlify, Cloudflare, self-hosted)?
4. Output a tailored checklist with code templates pre-filled for their stack

### Framework detection (used during `/seo audit`)

Signals that trigger spawning of `seo-nextjs` agent:
- `_next/` path in page source
- `__NEXT_DATA__` script tag
- `next/image` noscript tags
- `@vite/` in source, `vite.svg` default favicon
- `<script type="module" src="/src/main.tsx">` pattern (Vite default)

## Scoring

| Category | Weight |
|----------|--------|
| Rendering strategy (SSR/SSG/CSR) | 25% |
| Metadata in initial HTML | 20% |
| Schema in initial HTML | 20% |
| Core Web Vitals patterns (image, font) | 15% |
| robots.txt + sitemap | 10% |
| Security headers | 10% |

## Quality Gates

- **Critical**: Canonical or noindex injected by JS only (not in initial HTML)
- **Critical**: No metadata export — title/description missing from server HTML
- **Critical**: Plain `<img>` on hero/LCP element (no `next/image` with `priority`)
- **High**: No JSON-LD on any page
- **High**: No `robots.ts` or `sitemap.ts` (Next.js App Router)
- **High**: No security headers in `next.config.js` or hosting config
- **Medium**: No `next/font` (CLS risk from system font swap)
- **Medium**: No `llms.txt`
- **Low**: No IndexNow route for fast Bing/Yandex indexing

## Reference Files

Load on-demand:
- `references/nextjs-checklist.md`: Pre-launch checklist with pass/fail criteria
- `references/nextjs-code-patterns.md`: Ready-to-use code for metadata, JSON-LD, headers, sitemap

## Community Footer

Show after `/seo nextjs <url>` completes (full audit). Skip for `setup` and sub-commands.

## Error Handling

| Scenario | Action |
|----------|--------|
| URL is CSR-only (Vite SPA) | Flag as Critical rendering issue. Show migration path to Vike or prerendering. |
| Next.js Pages Router detected | Apply Pages Router patterns (`_app.tsx`, `next/head`) not App Router patterns. Note migration path to App Router. |
| Site behind auth | Audit what's publicly visible. Note that auth-gated pages can't be indexed. |
| No framework signals detected | Run standard `/seo technical` instead and note no Next.js/Vite signals found. |
