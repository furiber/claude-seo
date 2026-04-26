<!-- Updated: 2026-04-26 -->
# Next.js / Vite SEO Code Patterns

Ready-to-use implementations. Copy, adjust domain/names, ship.

---

## Metadata helper (App Router)

```ts
// lib/metadata.ts
import { Metadata } from 'next';
const BASE = 'https://yourdomain.com';

export function buildMetadata({
  title, description, path,
  ogImage = '/og-default.png',
}: { title: string; description: string; path: string; ogImage?: string }): Metadata {
  const url = `${BASE}${path}`;
  return {
    title: `${title} | Site Name`,
    description,
    alternates: { canonical: url },
    openGraph: { title, description, url, siteName: 'Site Name',
      images: [{ url: ogImage, width: 1200, height: 630 }], type: 'website' },
    twitter: { card: 'summary_large_image', title, description, images: [ogImage] },
  };
}
```

Dynamic page usage:
```ts
export async function generateMetadata({ params }: Props): Promise<Metadata> {
  const post = await getPost(params.slug);
  return buildMetadata({ title: post.title, description: post.excerpt,
    path: `/blog/${params.slug}`, ogImage: post.ogImage });
}
```

---

## robots.ts + sitemap.ts (App Router)

```ts
// app/robots.ts
import { MetadataRoute } from 'next';
export default function robots(): MetadataRoute.Robots {
  return {
    rules: [
      { userAgent: '*', allow: '/' },
      { userAgent: 'GPTBot', disallow: '/' },        // blocks OpenAI training
      { userAgent: 'Google-Extended', disallow: '/' }, // blocks Gemini training, NOT search
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
  const posts = await getAllPosts();
  return [
    { url: 'https://yourdomain.com', lastModified: new Date(), priority: 1.0 },
    { url: 'https://yourdomain.com/about', lastModified: new Date(), priority: 0.8 },
    ...posts.map(p => ({
      url: `https://yourdomain.com/blog/${p.slug}`,
      lastModified: p.updatedAt, priority: 0.6,
    })),
  ];
}
```

---

## JSON-LD component

```tsx
// components/JsonLd.tsx
export function JsonLd({ data }: { data: Record<string, unknown> }) {
  return (
    <script type="application/ld+json"
      dangerouslySetInnerHTML={{ __html: JSON.stringify(data) }} />
  );
}
```

Organization (homepage):
```tsx
<JsonLd data={{ '@context': 'https://schema.org', '@type': 'Organization',
  name: 'Your Company', url: 'https://yourdomain.com',
  logo: 'https://yourdomain.com/logo.png',
  sameAs: ['https://linkedin.com/company/yourco', 'https://twitter.com/yourco'] }} />
```

Article (blog post):
```tsx
<JsonLd data={{ '@context': 'https://schema.org', '@type': 'Article',
  headline: post.title, datePublished: post.publishedAt, dateModified: post.updatedAt,
  author: { '@type': 'Person', name: post.author.name },
  image: post.ogImage, url: `https://yourdomain.com/blog/${post.slug}` }} />
```

BreadcrumbList:
```tsx
<JsonLd data={{ '@context': 'https://schema.org', '@type': 'BreadcrumbList',
  itemListElement: breadcrumbs.map((b, i) => ({
    '@type': 'ListItem', position: i + 1, name: b.label, item: b.url })) }} />
```

---

## next/image for LCP

```tsx
import Image from 'next/image';

// Hero — always use priority + fetchPriority
<Image src="/hero.webp" alt="Descriptive alt text"
  width={1200} height={600} priority fetchPriority="high" />

// Below fold — lazy load (default)
<Image src="/feature.webp" alt="Feature description" width={800} height={400} />
```

---

## next/font (eliminates CLS from font swap)

```ts
// app/layout.tsx
import { Inter } from 'next/font/google';
const inter = Inter({ subsets: ['latin'], display: 'swap', variable: '--font-inter' });

export default function RootLayout({ children }) {
  return <html lang="en" className={inter.variable}><body>{children}</body></html>;
}
```

---

## Security headers (next.config.js)

```js
const securityHeaders = [
  { key: 'X-Frame-Options', value: 'SAMEORIGIN' },
  { key: 'X-Content-Type-Options', value: 'nosniff' },
  { key: 'Referrer-Policy', value: 'strict-origin-when-cross-origin' },
  { key: 'Permissions-Policy', value: 'camera=(), microphone=(), geolocation=()' },
  { key: 'Strict-Transport-Security', value: 'max-age=63072000; includeSubDomains; preload' },
];

module.exports = {
  async headers() {
    return [{ source: '/(.*)', headers: securityHeaders }];
  },
};
```

---

## llms.txt (public/llms.txt)

```
# Site: Your Site Name
# Description: One sentence about what the site covers.
# Contact: you@yourdomain.com

## Allowed
User-agent: *
Allow: /

## Key pages
/about
/blog
/products
```

---

## Vike (Vite SSR) — metadata equivalent

```tsx
// pages/+Head.tsx
export function Head({ pageContext }) {
  const { title, description, canonical } = pageContext.documentProps ?? {};
  return (<>
    <title>{title}</title>
    <meta name="description" content={description} />
    <link rel="canonical" href={canonical} />
  </>);
}
```
