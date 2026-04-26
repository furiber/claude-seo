# Next.js / Vite SEO Setup Guide

> Set this up before writing a single page of content. Every issue in this guide
> has appeared in analysis sessions in this repo. Fix it once at project start
> instead of finding it post-launch.

---

## Why this exists

The recurring pattern across every `/seo audit` and `/seo technical` run on JS-heavy
sites: the same 8 categories fail. Schema missing. Canonicals injected by JS (not in
initial HTML). No sitemap. Images not optimised for LCP. Fonts causing CLS. No security
headers. No robots.txt AI directives. No content architecture.

This guide front-loads all of that.

---

## 1. Rendering Strategy (the most important decision)

Google renders JavaScript, but with a delay. Content that only exists after JS execution
may be indexed days or weeks later, and some elements are never picked up.

**Rule:** Critical SEO elements must be in the **initial server-rendered HTML response**
— not injected by JavaScript.

This includes:
- `<title>` and `<meta name="description">`
- Canonical tags (`<link rel="canonical">`)
- `<meta name="robots">` (noindex/nofollow)
- JSON-LD structured data
- Open Graph tags

### Next.js (App Router) — correct by default

Next.js App Router SSR/SSG handles this automatically when you use the `metadata`
API. Do not use `document.head` manipulation or client-only helmet libraries.

```ts
// app/layout.tsx or any page.tsx
export const metadata: Metadata = {
  title: 'Page Title | Site Name',
  description: 'Under 160 chars. Specific, not generic.',
};
```

### Vite + React — CSR by default, requires SSR setup

Plain Vite apps are client-side rendered. Google will eventually index them but
structured data, canonicals, and meta tags injected via React Helmet are unreliable.

Options in order of preference:
1. **[Vike](https://vike.dev/)** (formerly vite-plugin-ssr) — full SSR/SSG control
2. **[TanStack Start](https://tanstack.com/start)** — SSR-first, file-based routing
3. **Prerendering** via `vite-plugin-prerender` — viable for mostly-static sites
4. Avoid plain CRA/Vite SPA for content pages that need to rank

---

## 2. Metadata (every page, not just homepage)

### Next.js App Router

```ts
// lib/metadata.ts — shared helper
import { Metadata } from 'next';

export function buildMetadata({
  title,
  description,
  path,
  ogImage = '/og-default.png',
}: {
  title: string;
  description: string;
  path: string;
  ogImage?: string;
}): Metadata {
  const url = `https://yourdomain.com${path}`;
  return {
    title: `${title} | Site Name`,
    description,
    alternates: { canonical: url },
    openGraph: {
      title,
      description,
      url,
      siteName: 'Site Name',
      images: [{ url: ogImage, width: 1200, height: 630 }],
      type: 'website',
    },
    twitter: {
      card: 'summary_large_image',
      title,
      description,
      images: [ogImage],
    },
  };
}
```

Use `generateMetadata` for dynamic routes:

```ts
// app/blog/[slug]/page.tsx
export async function generateMetadata({ params }: Props): Promise<Metadata> {
  const post = await getPost(params.slug);
  return buildMetadata({
    title: post.title,
    description: post.excerpt,
    path: `/blog/${params.slug}`,
    ogImage: post.ogImage,
  });
}
```

### Vike / Vite SSR

```ts
// pages/+Head.tsx
export { Head };
function Head({ pageContext }) {
  const { title, description, canonical } = pageContext.documentProps;
  return (
    <>
      <title>{title}</title>
      <meta name="description" content={description} />
      <link rel="canonical" href={canonical} />
    </>
  );
}
```

---

## 3. Schema Markup (JSON-LD)

**Schema is the single most commonly missing element.** Content with schema has ~2.5×
higher chance of appearing in AI-generated answers (Google/Microsoft, March 2025).

Add a JSON-LD component that outputs in the initial HTML:

```tsx
// components/JsonLd.tsx
export function JsonLd({ data }: { data: Record<string, unknown> }) {
  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(data) }}
    />
  );
}
```

### Minimum schemas by page type

| Page type | Schema | Required properties |
|-----------|--------|-------------------|
| Homepage | `Organization` | name, url, logo, sameAs (social profiles) |
| Article/Blog | `Article` | headline, author, datePublished, image |
| Product | `Product` | name, description, offers (price, currency, availability) |
| Local business | `LocalBusiness` | name, address, telephone, openingHours |
| FAQ section | `FAQPage` | mainEntity[]{question, acceptedAnswer} |
| Breadcrumbs | `BreadcrumbList` | item[]{position, name, item} |

Example `Organization` on homepage:

```tsx
// app/page.tsx
<JsonLd data={{
  '@context': 'https://schema.org',
  '@type': 'Organization',
  name: 'Your Company',
  url: 'https://yourdomain.com',
  logo: 'https://yourdomain.com/logo.png',
  sameAs: [
    'https://linkedin.com/company/yourco',
    'https://twitter.com/yourco',
  ],
}} />
```

---

## 4. robots.txt + Sitemap

### Next.js App Router (file-based, generated at build time)

```ts
// app/robots.ts
import { MetadataRoute } from 'next';

export default function robots(): MetadataRoute.Robots {
  return {
    rules: [
      { userAgent: '*', allow: '/' },
      // Block AI training crawlers if desired (does NOT affect search indexing)
      { userAgent: 'GPTBot', disallow: '/' },
      { userAgent: 'Google-Extended', disallow: '/' },
      { userAgent: 'Bytespider', disallow: '/' },
    ],
    sitemap: 'https://yourdomain.com/sitemap.xml',
  };
}
```

```ts
// app/sitemap.ts
import { MetadataRoute } from 'next';

export default async function sitemap(): Promise<MetadataRoute.Sitemap> {
  const posts = await getAllPosts(); // your data source
  const staticPages = ['/', '/about', '/contact'];

  return [
    ...staticPages.map((path) => ({
      url: `https://yourdomain.com${path}`,
      lastModified: new Date(),
      changeFrequency: 'monthly' as const,
      priority: path === '/' ? 1 : 0.8,
    })),
    ...posts.map((post) => ({
      url: `https://yourdomain.com/blog/${post.slug}`,
      lastModified: post.updatedAt,
      changeFrequency: 'weekly' as const,
      priority: 0.6,
    })),
  ];
}
```

### Vite

Use `vite-plugin-sitemap` and a static `public/robots.txt`.

---

## 5. Core Web Vitals: LCP, INP, CLS

### LCP (target < 2.5s) — biggest issue on JS sites

- Hero image must use `next/image` with `priority` prop. Never use `<img>` for above-fold images.
- Preconnect to CDN origins in `<head>`:
  ```html
  <link rel="preconnect" href="https://your-cdn.com" />
  ```
- Avoid render-blocking scripts above the fold

```tsx
// next/image for LCP hero
import Image from 'next/image';

<Image
  src="/hero.webp"
  alt="Hero"
  width={1200}
  height={600}
  priority          // preloads the image, critical for LCP
  fetchPriority="high"
/>
```

### CLS (target < 0.1) — fonts and images

```ts
// app/layout.tsx — next/font eliminates FOUT and layout shift
import { Inter } from 'next/font/google';

const inter = Inter({
  subsets: ['latin'],
  display: 'swap',
  variable: '--font-inter',
});
```

Always set explicit `width` and `height` on all images (or use `fill` with a sized container).

### INP (target < 200ms) — interaction responsiveness

- Keep event handlers fast; move heavy work to `useTransition` or web workers
- Avoid large JavaScript bundles blocking the main thread
- Check with Chrome DevTools Performance panel, not just Lighthouse

---

## 6. Security Headers

Google doesn't rank on headers but they affect trust signals. Add to `next.config.js`:

```js
// next.config.js
const securityHeaders = [
  { key: 'X-Frame-Options', value: 'SAMEORIGIN' },
  { key: 'X-Content-Type-Options', value: 'nosniff' },
  { key: 'Referrer-Policy', value: 'strict-origin-when-cross-origin' },
  { key: 'Permissions-Policy', value: 'camera=(), microphone=(), geolocation=()' },
  {
    key: 'Strict-Transport-Security',
    value: 'max-age=63072000; includeSubDomains; preload',
  },
];

module.exports = {
  async headers() {
    return [{ source: '/(.*)', headers: securityHeaders }];
  },
};
```

For Vite, set headers in your hosting config (`vercel.json`, `netlify.toml`, or Cloudflare rules).

---

## 7. URL Structure

- Use descriptive, hyphenated slugs: `/blog/life-insurance-guide` not `/blog/post-123`
- No trailing slash inconsistency — pick one, enforce it with redirects
- No query parameters for content pages (e.g. `/products?id=123` → `/products/product-name`)
- Redirect chains: max 1 hop. `/old` → `/new`, never `/old` → `/middle` → `/new`
- Keep important pages within 3 clicks of the homepage

Next.js enforces trailing slash behaviour via `trailingSlash` in `next.config.js`.

---

## 8. AI Search (GEO/AEO) — growing channel

Based on the AA analysis: **zero AI citation presence** is a medium-priority gap that
grows as ChatGPT, Perplexity, and AI Overviews capture more zero-click traffic.

### llms.txt (add at project start)

```
# /public/llms.txt
# Site: Your Site Name
# Description: What your site covers, in plain English.
# Contact: yourname@yourdomain.com

## Allowed
User-agent: *
Allow: /

## Key pages for AI context
/about
/blog
/products
```

### Content for AI citability

- Answer questions directly, in the first paragraph
- Use structured headings (H2/H3) that match common search queries
- Include statistics with sources
- Add FAQ schema to Q&A content (2.5× citation rate)

---

## 9. Pre-launch Checklist

Run `/seo technical <url>` and `/seo audit <url>` before launch. These should all pass:

**Crawlability**
- [ ] `robots.txt` at root, references sitemap, no accidental Disallow on `/`
- [ ] `sitemap.xml` valid, all canonical URLs included, submitted to GSC

**Indexability**
- [ ] Canonical tag on every page, in initial HTML (not JS-injected)
- [ ] No noindex on pages that should rank
- [ ] www vs non-www redirects to one canonical version

**Metadata — every page**
- [ ] Unique `<title>` (50–60 chars)
- [ ] Unique `<meta description>` (120–155 chars)
- [ ] Open Graph title, description, image (1200×630)
- [ ] Twitter card tags

**Schema**
- [ ] `Organization` on homepage
- [ ] Page-type schema on all main page types (Article, Product, LocalBusiness, etc.)
- [ ] `BreadcrumbList` on all pages with navigation hierarchy
- [ ] Validate at https://validator.schema.org

**Performance**
- [ ] LCP < 2.5s (use `priority` on hero image, `next/font`)
- [ ] CLS < 0.1 (explicit image dimensions, no layout-shifting ads)
- [ ] INP < 200ms (no heavy main-thread work on user interaction)

**Technical**
- [ ] HTTPS enforced, no mixed content
- [ ] Security headers present (check with securityheaders.com)
- [ ] All images have descriptive `alt` text
- [ ] Mobile viewport meta tag present

**AI / Content**
- [ ] `llms.txt` at root
- [ ] AI crawler directives in `robots.txt` (deliberate allow or block)
- [ ] At least one FAQ section with `FAQPage` schema on informational pages

---

## 10. Google Search Console Setup

Do this the day the domain is bought, not post-launch:

1. Add property in GSC (domain property, not URL prefix)
2. Verify via DNS TXT record
3. Submit sitemap
4. Set preferred version (www vs non-www)
5. Check URL Inspection for any indexing issues within 48h of first crawl

---

## Quick reference: what `/seo audit` checks

The claude-seo audit spawns up to 15 parallel subagents across:
`technical` · `content` · `schema` · `sitemap` · `performance` · `visual` · `geo` ·
`local` · `backlinks`

If you've implemented this guide, `technical`, `schema`, `sitemap`, and `performance`
should pass with minimal findings on day one.
