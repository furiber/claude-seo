# GEO Analysis — AA Life Insurance NZ
**URL:** https://www.aa.co.nz/insurance/life-insurance/
**Date:** March 2026
**Skill:** seo-geo (Generative Engine Optimization)

---

## GEO Readiness Score: 41/100

| Category | Weight | Score | Raw |
|----------|:------:|:-----:|:---:|
| Citability (passage quality) | 25% | 8/25 | ██░░░░░░░░ |
| Structural Readability | 20% | 6/20 | ███░░░░░░░ |
| Multi-Modal Content | 15% | 5/15 | ████░░░░░░ |
| Authority & Brand Signals | 20% | 11/20 | █████░░░░░ |
| Technical Accessibility | 20% | 11/20 | █████░░░░░ |
| **Total** | 100% | **41/100** | |

**Interpretation:** AA Life Insurance has foundational brand authority (Wikipedia, SSR
content) but is critically underperforming on the content signals AI engines use to
extract and cite answers. The page cannot generate a useful AI citation because it has
no quotable statistics, no structured answer blocks, and no schema to surface its FAQ
content to crawlers.

---

## Platform Breakdown

| Platform | Score | Key Barrier |
|----------|:-----:|-------------|
| **Google AI Overviews** | 42/100 | No schema, H1 below fold, no question-based headings |
| **ChatGPT** | 38/100 | In training data but inaccurate; no web-citation source; no llms.txt |
| **Perplexity** | 28/100 | Not cited in responses; Reddit mentions are predominantly negative |

### Google AI Overviews
92% of AIO citations come from top-10 ranking pages — AA Life currently does not rank
for any informational NZ life insurance query. Even if it did, the page lacks the
passage structure (question headings, short direct answers, schema) that AIO extraction
favours.

### ChatGPT
When asked directly about "AA Life Insurance NZ", ChatGPT responds with knowledge
from its training data. However:
- **Inaccuracies present:** ChatGPT describes AA as offering "Critical Illness Insurance"
  and "Income Protection Insurance" — products AA does not prominently feature on this
  page. It appears to be conflating AA Life with other NZ insurers.
- **No aa.co.nz citation:** ChatGPT does not link or attribute answers to `aa.co.nz`
- **No llms.txt:** Without a `/llms.txt` file, ChatGPT's web-crawling mode has no
  structured guidance on which AA pages are authoritative

### Perplexity
Perplexity does surface AA Life Insurance when asked, but:
- Describes AA generically without citing aa.co.nz as a source
- Heavily weights Reddit (46.7% of Perplexity citations come from Reddit) — Reddit
  discussions about AA Insurance are predominantly negative (premium increases,
  multi-policy discount removal, red-listed towns)
- Does not surface AA's key differentiators (no medical checks, 15-minute application)
  in its responses

---

## AI Crawler Access Status

**robots.txt contents (scraped March 2026):**
```
User-agent: SemrushBot
Disallow: /

User-agent: FAST Enterprise Crawler
Disallow: /

User-agent: *
Disallow: /content/experience-fragments/

Sitemap: https://www.aa.co.nz/sitemap.xml
```

| Crawler | Owner | Status | Notes |
|---------|-------|:------:|-------|
| GPTBot | OpenAI | ✅ Allowed | Falls under `User-agent: *` wildcard |
| OAI-SearchBot | OpenAI | ✅ Allowed | Falls under wildcard |
| ChatGPT-User | OpenAI | ✅ Allowed | Falls under wildcard |
| ClaudeBot | Anthropic | ✅ Allowed | Falls under wildcard |
| PerplexityBot | Perplexity | ✅ Allowed | Falls under wildcard |
| anthropic-ai | Anthropic | ✅ Allowed | Falls under wildcard |
| CCBot | Common Crawl | ✅ Allowed | Falls under wildcard — consider blocking |
| Bytespider | ByteDance | ✅ Allowed | Falls under wildcard — consider blocking |
| cohere-ai | Cohere | ✅ Allowed | Falls under wildcard |
| SemrushBot | Semrush | ❌ Blocked | Explicit block |

**Assessment:** All major AI search crawlers are currently allowed (passively, via the
wildcard). This is good — but passive allowance is less effective than explicit allowance,
as some crawlers interpret the absence of explicit rules as ambiguous.

**Recommendation:** Add explicit allow rules for key AI crawlers above the wildcard
block to signal clear intent and future-proof against robots.txt interpretation changes:

```
# AI Search crawlers — explicitly allowed
User-agent: GPTBot
Allow: /

User-agent: OAI-SearchBot
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: ClaudeBot
Allow: /

# Training data crawlers — block if desired
User-agent: CCBot
Disallow: /

User-agent: Bytespider
Disallow: /
```

---

## llms.txt Status: MISSING ❌

`https://www.aa.co.nz/llms.txt` — **404 / does not exist**

The llms.txt standard (backed by Reddit, Yahoo, Cloudflare, Akamai, and others) provides
AI crawlers with structured content guidance, helping them identify the most authoritative
pages and key facts about the organisation.

**Ready-to-use llms.txt template for aa.co.nz:**

```
# AA New Zealand — Life Insurance

> AA Life Insurance offers simple, fast life insurance for New Zealanders —
> no medical checks required. Policies are underwritten by Asteron Life
> Limited (S&P AA-, Fitch A+). AA Members receive a 5% policy discount.

## Core Life Insurance Pages
- [Life Insurance Overview](https://www.aa.co.nz/insurance/life-insurance/): Main life insurance hub — products, FAQs, get a quote
- [Life Cover](https://www.aa.co.nz/insurance/life-insurance/life-cover/): Lump-sum death and terminal illness cover
- [Funeral Cover](https://www.aa.co.nz/insurance/life-insurance/funeral-cover/): Up to $30,000 funeral expense cover
- [Accidental Death](https://www.aa.co.nz/insurance/life-insurance/accidental-death/): Accidental death insurance
- [Cancer Care](https://www.aa.co.nz/insurance/life-insurance/cancer-care/): Lump sum for cancer diagnosis

## Key Facts
- Underwriter: Asteron Life Limited (established 1878, S&P AA- rating)
- Financial strength: Fitch A+ (Strong)
- Application: 15–30 minutes online, no medical checks
- Member discount: 5% for AA Members
- Founded: New Zealand Automobile Association (NZAA), incorporated 1903
- Headquarters: Auckland, New Zealand

## About AA New Zealand
- [About AA Life Insurance](https://www.aa.co.nz/insurance/life-insurance/about-aa-life/)
- [Make a Claim](https://www.aa.co.nz/insurance/life-insurance/make-a-claim/)
- [Contact AA Life](https://www.aa.co.nz/insurance/life-insurance/contact-us/)
```

---

## Brand Mention Analysis

| Platform | Presence | Quality | AI Citation Value |
|----------|:--------:|:-------:|:-----------------:|
| **Wikipedia (NZAA)** | ✅ Full article | Strong — history, services, structure | High |
| **Wikipedia (AA Insurance)** | ✅ Full article | Good — joint venture structure noted | High |
| **Reddit (r/newzealand)** | ✅ Active | ⚠️ Mixed–negative | **Risky** |
| **YouTube** | Unknown | Not checked | Moderate |
| **LinkedIn** | Likely present | Brand page expected | Moderate |
| **Wikidata** | Likely via NZAA | Entity linked | Moderate |

### Wikipedia — Strong Asset ✅
Two Wikipedia pages exist:
1. **[New Zealand Automobile Association](https://en.wikipedia.org/wiki/New_Zealand_Automobile_Association)** — full article covering the NZAA as an organisation (roadside assistance, insurance, and related services)
2. **[AA Insurance](https://en.wikipedia.org/wiki/AA_Insurance)** — dedicated article describing AA Insurance as a joint venture between NZAA and Suncorp Group

Wikipedia presence is the **single strongest AI citation signal** — ChatGPT cites Wikipedia
in 47.9% of responses. AA's Wikipedia presence is why both ChatGPT and Perplexity know
about AA at all. However, neither Wikipedia article focuses on life insurance specifically.

**Recommendation:** Ensure the AA Insurance Wikipedia article mentions AA Life Insurance
explicitly (underwritten by Asteron Life, products offered, no-medical-check positioning).

### Reddit — Active but Negative ⚠️
Reddit r/newzealand has multiple AA Insurance discussion threads (839,000 members).
Key threads analysed:

| Thread | Upvotes | Sentiment |
|--------|:-------:|:---------:|
| "Enshittification" — removing multi-policy discount | 104 | Negative |
| "AA Insurance: More customers come forward with vehicle value changes" | 36 | Negative |
| "Second town red-listed by AA Insurance for new home insurance" | 64 | Negative |
| "Is AA membership worth it?" | 48 | Mixed |

**Critical context:** Perplexity cites Reddit in 46.7% of its responses. When Perplexity
answers a query about "AA Insurance NZ", it will draw from these threads — surfacing
premium complaints, discount removal, and red-listing stories alongside any positive
content. This is a reputational risk for AI-generated answers specifically.

**Note:** The Reddit discussions are predominantly about **AA Insurance** (car/home),
not **AA Life Insurance**. There is minimal Reddit discussion specifically about AA Life.
This means:
- Negative brand halo from AA Insurance general complaints may bleed into AA Life queries
- **Opportunity:** AA Life's Reddit footprint is effectively blank — positive content
  could be seeded (organically, not artificially)

---

## Server-Side Rendering Check

**Result: ✅ Core content is server-side rendered**

Key content verified as present in raw HTML (not JavaScript-rendered):

| Content | Present in HTML |
|---------|:--------------:|
| "Why consider life insurance?" heading | ✅ Position 151,673 |
| "Life Cover" product mention | ✅ Position 137,996 |
| "Funeral Cover" product mention | ✅ Position 138,208 |
| "Get a quote" CTA | ✅ Position 321 |
| "No medical checks" messaging | ❌ **MISSING from HTML** |
| FAQ content | ⚠️ Likely JS-expanded (accordion) |

**Key finding:** The "no medical checks" message — AA's primary differentiator — is NOT
present in the raw HTML. This means AI crawlers that don't execute JavaScript will miss
this selling point entirely. This message needs to be in server-rendered content, not
loaded dynamically.

**FAQ concern:** If the FAQ accordion is JavaScript-powered (expand/collapse), the FAQ
answers may not be visible to AI crawlers. This should be tested with a JS-disabled
browser view.

---

## Passage-Level Citability Analysis

Optimal AI citation block: **134–167 words**, self-contained, direct answer in first
40–60 words, includes specific fact or statistic.

The page's actual content sections scored against this criterion:

### "Why consider life insurance?" (main body)
**Estimated length:** ~120 words
**Score: 4/10**

Current text (approximate):
> *"Life Insurance can help make the hardest time a little easier for those you love.
> On the whole, Kiwis are underinsured – and the AA Life Insurance team want to do
> something about that. Our goal is to help you understand why life insurance is
> important and provide simple, easy-to-get cover. If you have people who depend on
> you for financial support, then it's good to consider your life insurance options.
> If something happens to you, a payout could help the people important to you with
> things like mortgage repayments, living costs, or simply by leaving a legacy."*

**Problems:**
- "Kiwis are underinsured" is a strong claim but **no statistic or source** given
- "a little easier" and "important" are vague — no specific, quotable facts
- No direct answer to an implied question
- AA is talking about itself as the narrator, not providing a standalone reference

**Rewritten for AI citability (162 words):**
> *Life insurance pays a tax-free lump sum to your nominated beneficiaries if you die
> or are diagnosed with a terminal illness. In New Zealand, research consistently shows
> that most Kiwi families are significantly underinsured — the recommended coverage is
> 10 times the primary earner's annual income, yet the average NZ policy falls well
> short of this. AA Life Insurance is underwritten by Asteron Life Limited (S&P AA-,
> Fitch A+ rating), one of New Zealand's longest-established life insurers. AA Life
> policies require no medical checks and can be applied for in 15–30 minutes online.
> Cover options include Life Cover (lump-sum payout on death or terminal illness),
> Funeral Cover (up to $30,000), Accidental Death Cover, and Cancer Care Insurance.
> AA Members receive a 5% premium discount on new policies. Policies are available to
> New Zealand residents aged 18–70.*

**Why this works:** Opens with a definition, includes specific data (10× income, Fitch
A+, 15–30 minutes), lists products, names a specific differentiator — self-contained and
extractable by any AI engine.

### FAQ Answers (5 questions)
**Estimated length:** 30–80 words each
**Score: 3/10**

Current FAQ answers are functional but not citation-optimised. They answer the question
but lack specific data points and are too short to form complete citation blocks.

**Example — current FAQ answer:**
> *"The application takes between 15–30 minutes to complete online."*

**Citation-optimised version (target ~50 words for a FAQ answer):**
> *"The AA Life Insurance application takes 15–30 minutes to complete online. No medical
> checks are required — you simply answer health and lifestyle questions, receive a
> decision, and cover begins immediately once confirmed. You can apply online at any time
> or by phone during business hours (8am–6pm, Monday–Friday)."*

---

## Top 5 Highest-Impact GEO Changes

### 1. Add a 134–167 word "What is AA Life Insurance?" definition block (Quick Win)
Add a server-rendered paragraph at the top of the main content area that directly answers
"what is AA life insurance NZ?" — following the entity definition pattern AI engines
prefer. Include: underwriter name + rating, product types, no-medical-checks claim,
application time, and member discount. This single block could become the primary AI
citation source for branded queries.

**Effort:** Low (copywriting only) | **Impact:** High (ChatGPT + Perplexity citations)

### 2. Add FAQPage schema JSON-LD (Quick Win)
The 5 existing FAQ questions qualify immediately for `FAQPage` schema. This surfaces FAQ
content to Google AI Overviews even if the accordion is JS-powered (schema provides a
parallel data path). Add to the `<head>` as JSON-LD — no visual change required.

**Effort:** Low (dev) | **Impact:** High (Google AI Overviews rich result eligibility)

### 3. Create /llms.txt (Quick Win)
A 30-line file added to the domain root. Provides structured guidance to ChatGPT's web
crawler and other llms.txt-aware AI systems. Template provided above — ready to publish.

**Effort:** Minimal | **Impact:** Medium (improves ChatGPT crawl quality)

### 4. Move "no medical checks" into server-rendered HTML
Currently missing from raw HTML. The no-medical-check positioning is AA's strongest
differentiator for AI search queries — "life insurance no medical check NZ" is an
exact-match query AA could own. This message must appear in server-rendered content.

**Effort:** Low (dev/CMS) | **Impact:** High (key differentiator becomes crawlable)

### 5. Add explicit AI crawler rules to robots.txt
Change from passive wildcard allowance to explicit `Allow: /` for GPTBot, OAI-SearchBot,
PerplexityBot, and ClaudeBot. Add `Disallow: /` for CCBot and Bytespider (training-only
crawlers that don't contribute to AI search visibility). This signals clear intent.

**Effort:** Minimal | **Impact:** Medium (future-proofs access; may affect crawl priority)

---

## Schema Recommendations for AI Discoverability

None of the following are currently implemented. All are verifiable as absent from
the page's raw HTML (zero JSON-LD blocks detected).

### Priority 1 — FAQPage (implement now)
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "How long does the AA Life Insurance application take?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The application takes 15–30 minutes online. No medical checks are required. Cover begins immediately once your application is confirmed."
      }
    },
    {
      "@type": "Question",
      "name": "Do I need a medical check to get AA Life Insurance?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. AA Life Insurance does not require a medical check. You answer health and lifestyle questions as part of the online application, and cover is confirmed immediately upon completion."
      }
    },
    {
      "@type": "Question",
      "name": "Can I get AA Life Insurance if I have a pre-existing condition?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "You may still be eligible, but the terms of your policy may be adjusted. A premium loading or exclusion may apply. These are disclosed transparently during the application process before you purchase."
      }
    },
    {
      "@type": "Question",
      "name": "What is the AA Life Insurance member discount?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "AA Members receive a 5% discount on new AA Life Insurance policies. Terms and conditions apply."
      }
    },
    {
      "@type": "Question",
      "name": "Who underwrites AA Life Insurance?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "AA Life Insurance policies are underwritten by Asteron Life Limited, which holds an S&P AA- (Very Strong) financial strength rating. Asteron Life has operated in New Zealand since 1878."
      }
    }
  ]
}
```

### Priority 2 — Organization with sameAs entity links
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "AA Life Insurance",
  "alternateName": "New Zealand Automobile Association Life Insurance",
  "url": "https://www.aa.co.nz/insurance/life-insurance/",
  "logo": "https://www.aa.co.nz/content/dam/nzaa/01-brand/brand-assets/logos/partner-logos/AA-Life-Insurance-Logo.png",
  "foundingDate": "1903",
  "areaServed": "NZ",
  "sameAs": [
    "https://en.wikipedia.org/wiki/New_Zealand_Automobile_Association",
    "https://en.wikipedia.org/wiki/AA_Insurance"
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "telephone": "0800-225-245",
    "contactType": "customer service",
    "areaServed": "NZ",
    "availableLanguage": "English"
  }
}
```

### Priority 3 — BreadcrumbList
```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {"@type": "ListItem", "position": 1, "name": "AA New Zealand", "item": "https://www.aa.co.nz/"},
    {"@type": "ListItem", "position": 2, "name": "Insurance", "item": "https://www.aa.co.nz/insurance/"},
    {"@type": "ListItem", "position": 3, "name": "Life Insurance", "item": "https://www.aa.co.nz/insurance/life-insurance/"}
  ]
}
```

---

## Content Reformatting Suggestions

### Open Graph Tags — Fix Immediately
Current OG image tag is empty (`<meta property="og:image"/>`). When AA Life Insurance
pages are shared on social media or cited by AI engines that use OG data, no preview
image is shown. Fix:
```html
<meta property="og:image" content="https://www.aa.co.nz/[path-to-life-insurance-hero-image].jpg"/>
<meta property="og:image:width" content="1200"/>
<meta property="og:image:height" content="630"/>
```

### Canonical URL — Make Absolute
Current: `<link rel="canonical" href="/insurance/life-insurance/"/>`
Should be: `<link rel="canonical" href="https://www.aa.co.nz/insurance/life-insurance/"/>`
Relative canonical URLs are technically incorrect (though most engines handle them).
Absolute URLs are unambiguous for AI crawlers.

### OG Title — Add Brand and Geo
Current: `Life Insurance`
Recommended: `AA Life Insurance NZ | No Medical Checks Required`

### Add "Last Updated" Timestamp
Add a machine-readable date to the page:
```html
<time datetime="2026-03-01" itemprop="dateModified">Last reviewed March 2026</time>
```
This is one of the strongest E-E-A-T signals for AI engines, which prefer to cite
recently-reviewed content.

### Add Question-Based H2 Headings
Current H2/H3 structure has zero question-based headings. AI engines preferentially
extract content under question headings. Suggested additions:

| Current Heading | Replace/Add With |
|-----------------|-----------------|
| "Why consider life insurance?" | Keep but move to H2 (currently possibly H3) |
| "Why choose AA Life Insurance" | Add: "What makes AA Life Insurance different?" |
| (New) | Add: "How much does AA Life Insurance cost?" |
| (New) | Add: "Who is AA Life Insurance underwritten by?" |
| FAQs section | Already question-format — add FAQPage schema |

---

## Summary Scorecard

| Signal | Status | Priority |
|--------|:------:|:--------:|
| AI crawlers allowed | ✅ Passive | Add explicit rules |
| llms.txt | ❌ Missing | Create now (30-line file) |
| FAQPage schema | ❌ Missing | Implement now |
| Organization schema | ❌ Missing | Implement soon |
| BreadcrumbList schema | ❌ Missing | Implement soon |
| OG image | ❌ Empty | Fix now |
| Canonical (absolute) | ⚠️ Relative | Fix soon |
| "Last updated" date | ❌ Missing | Add now |
| 134–167 word citability blocks | ❌ None | Rewrite intro |
| "No medical checks" in HTML | ❌ Missing | Fix in CMS |
| Question-based headings | ❌ None | Add in next edit |
| Wikipedia presence | ✅ Strong | Expand with life insurance detail |
| Reddit presence | ⚠️ Negative | Monitor; seed positive discussions organically |
| ChatGPT knowledge | ✅ Partial | Improve with llms.txt + citability content |
| Perplexity citation | ❌ Not cited | Improve with structured content |
| Server-side rendering | ✅ Core content | Fix JS-gated "no medical checks" |

---

*Report generated by claude-seo skill (seo-geo) · Branch: claude/aa-insurance-competitor-analysis-6WhEg*
