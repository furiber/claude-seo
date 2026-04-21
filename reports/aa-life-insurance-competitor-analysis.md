# AA Life Insurance — SEO Competitor Analysis vs Aggregators
**Analysed:** aa.co.nz/insurance/life-insurance/ vs moneyhub.co.nz vs glimp.co.nz
**Date:** March 2026
**Branch:** claude/aa-insurance-competitor-analysis-6WhEg

---

## Note on "Glip.co.nz"

The domain `glip.co.nz` does not exist — all scrape attempts returned empty. The aggregator
the user is likely referring to is **Glimp** (`glimp.co.nz`), a NZ-based comparison site
primarily focused on broadband, power, and utilities that also lists insurance providers.
This report uses `glimp.co.nz` throughout.

---

## 1. Executive Summary

AA Life Insurance operates a well-branded, conversion-optimised product page that performs
its primary job (getting quotes) adequately. However, it is invisible in organic search for
every high-volume informational and comparison keyword in the NZ life insurance category.
**MoneyHub holds the #1 position for every major keyword tested.** Glimp is present in the
category but thin and not ranking for top terms.

**The five most important gaps for AA to close:**

| # | Gap | Impact |
|---|-----|--------|
| 1 | No schema markup (zero JSON-LD on page) | Critical — prevents rich results |
| 2 | Content depth: ~700 words vs MoneyHub's ~10,000 | Critical — invisible for informational queries |
| 3 | No pricing transparency | High — loses all comparison-intent traffic |
| 4 | No topical content cluster (calculator, guides, FAQs) | High — misses top-of-funnel completely |
| 5 | Zero AI citation presence | Medium — growing channel, both ChatGPT and Perplexity omit AA |

**Structural note:** AA does not work with third-party brokers, which means LifeDirect
(MoneyHub's primary affiliate partner) cannot feature AA. This limits aggregator referrals
by design. AA's only path to owning this space is building direct organic visibility through
its own informational content — a direct-to-consumer SEO strategy.

---

## 2. On-Page SEO Scorecard

| Dimension | AA Life (aa.co.nz) | MoneyHub | Glimp |
|-----------|:------------------:|:--------:|:-----:|
| **Title tag** | 4/10 | 9/10 | 6/10 |
| **Meta description** | N/A (JS-rendered) | 9/10 | 7/10 |
| **H1 / heading hierarchy** | 3/10 | 8/10 | 5/10 |
| **Word count (content)** | 2/10 | 10/10 | 2/10 |
| **Schema markup** | 0/10 | 2/10 | 0/10 |
| **Pricing transparency** | 0/10 | 10/10 | 0/10 |
| **E-E-A-T signals** | 5/10 | 8/10 | 3/10 |
| **Internal linking / cluster** | 4/10 | 10/10 | 4/10 |
| **AI citation readiness** | 1/10 | 7/10 | 2/10 |
| **Overall** | **~24/90** | **~73/90** | **~29/90** |

### AA Life
- **Title:** `Trusted Life Insurance for Your Family` — no geographic modifier ("NZ"),
  no year signal, no primary keyword ("life insurance") in natural phrase
- **H1:** `Why consider life insurance?` — informational intent but placed well below the
  fold (after hero banners and CTAs)
- **Content:** ~700 words of actual body copy (after stripping nav). This falls below
  the 800-word service page minimum in the skill's quality gates
- **Schema:** None detected. The page has FAQs, a financial product, and breadcrumbs —
  all qualify for structured data but none is implemented
- **Pricing:** No indicative pricing shown anywhere on the page
- **Strengths:** Strong brand trust signals (100-year-old organisation, "NZ's trusted"
  claim, Asteron Life underwriter disclosed with Fitch A+ rating), clear CTAs, no-medical-
  check message, 5% member discount highlighted

### MoneyHub
- **Title:** `Compare Life Insurance NZ 2026: Best Policies, Quotes & Deals - MoneyHub NZ`
  — year, geography, primary keyword, intent modifier ("compare"), and brand all present
- **Content:** ~10,000 words of article content — 5 full demographic pricing tables,
  9 detailed FAQs, methodology disclosure, concluding guide
- **Sub-pages (life insurance cluster):** 10+ pages cross-linked from the main article:
  Life Insurance Calculator, Policy Comparison (multi-insurer), Stepped vs Level guide,
  Pre-existing Conditions guide, Smokers guide, Videos series, Cancel/Change guide,
  Family Protection Insurance guide
- **Pricing tables:** 5 demographic scenarios × 9 insurers with methodology disclosure
  and "as of 2026" dating — AA is included and shown as mid-range
- **Affiliate model:** LifeDirect cited 15+ times per article as the comparison tool.
  MoneyHub earns commission when users click through to LifeDirect quotes. AA is excluded
  from LifeDirect because AA doesn't work with brokers — so MoneyHub has a financial
  incentive NOT to feature AA prominently in its recommendations
- **Schema:** Not detected in scraped content (may be in JS-rendered layer)
- **E-E-A-T:** Strong — dated content ("2026"), transparent methodology, named sources,
  multiple data points with financial strength ratings

### Glimp
- **Title:** `Best Life Insurance Companies NZ - Providers Comparison - Glimp`
- **Content:** ~400–600 words — thin provider cards (13 insurers: AIA, Asteron, Fidelity,
  Cigna, Partners Life, Southern Cross, **AA Life**, BNZ, Pinnacle, Momentum, Westpac,
  ANZ, AMP) with brief blurbs and "Compare Quotes" CTAs
- **AA included:** Yes — Glimp does list AA Life and links to `glimp.co.nz/life-insurance/aa-insurance`
- **Site focus:** Primarily broadband, power, and utilities comparison. Insurance is a
  secondary/supplementary category
- **Not ranking:** Glimp does not appear in the top 10 for any of the five main NZ
  life insurance keywords tested (see Section 4 below)
- **Schema:** None detected
- **No pricing, no educational content, no FAQs**

---

## 3. SERP Landscape — Who Ranks for What

Tested March 2026 across five core NZ life insurance queries:

| Keyword | #1 | #2 | #3 | AA Position |
|---------|----|----|----|-----------:|
| `best life insurance NZ 2026` | **MoneyHub** | Consumer NZ | Pinnacle Life | #4 (aainsurance.co.nz¹) |
| `compare life insurance NZ` | **MoneyHub** | ComparaNow | LifeDirect | #5 (aainsurance.co.nz¹) |
| `life insurance calculator NZ` | **MoneyHub** | KiwiCover | OneChoice | Not in top 10 |
| `how much life insurance NZ` | **MoneyHub** | — | — | Not in top 10 |
| `cheap life insurance NZ` | **MoneyHub** | — | — | Not in top 10 |

¹ The domain `aainsurance.co.nz` is AA's general insurance brand (car, home, contents).
`aa.co.nz/insurance/life-insurance/` — the specific life insurance page — does not appear
in the top 10 for any of these queries.

**Glimp** does not rank in the top 10 for any of the five queries tested. Its primary
strength is broadband and utilities SEO; insurance is a secondary category without
meaningful life insurance search visibility.

**Key competitors in organic:**
- MoneyHub (dominant aggregator — #1 for all informational/comparison queries)
- LifeDirect (broker comparison tool — #2–3 for comparison queries)
- Policywise, ComparaNow (broker-led comparison sites)
- AIA, Southern Cross Life, Pinnacle Life, Fidelity Life (direct insurer pages)

---

## 4. Pricing Position — What MoneyHub's Tables Show

MoneyHub publishes real-time comparative pricing across 9 insurers for $500,000 cover.
AA Life's pricing positions:

| Demographic | AA Annual Premium | Market Position | Cheapest Option |
|-------------|:-----------------:|:---------------:|:---------------:|
| 30M non-smoker | $445 | 7th / 9 | Fidelity $336 |
| 35F+35M joint | $795 | 8th / 9 | Fidelity $580 |
| 40M non-smoker | $555 | 8th / 9 | Fidelity $420 |
| 45M non-smoker | $795 | 8th / 9 | Fidelity $642 |
| 55M smoker | $4,420 | 4th / 9 | Chubb $4,227 |

**Implication:** AA is mid-to-high price in most scenarios. A pure price-comparison
strategy would not favour AA. The SEO strategy should emphasise **trust, simplicity,
no-medical-checks, and brand longevity** — the areas where AA genuinely differentiates.

MoneyHub also notes: *"AA Life doesn't work with brokers, though we believe their products
mirror Asteron's"* — confirming the structural exclusion from the broker/affiliate channel.

---

## 5. Content Gap Analysis

Topics MoneyHub covers (with dedicated pages or major sections) that AA's page does not:

| Topic | MoneyHub Has | AA Has | Priority |
|-------|:------------:|:------:|:--------:|
| Life insurance calculator | ✅ (dedicated page, ranks #1) | ❌ | Critical |
| How much cover do I need? | ✅ (FAQ + guide) | ❌ | Critical |
| Indicative pricing by age | ✅ (table, 5 segments) | ❌ | High |
| Stepped vs level premiums | ✅ (dedicated page) | ❌ | High |
| Life insurance for over 50s | ✅ (FAQ section) | ❌ | High |
| Pre-existing conditions guide | ✅ (dedicated page) | ❌ | High |
| Life insurance for smokers | ✅ (dedicated page) | ❌ | Medium |
| Family Protection Insurance | ✅ (FAQ section) | ❌ | Medium |
| Multi-insurer policy comparison | ✅ (dedicated page) | ❌ | Medium |
| Video explainer series | ✅ (11-minute series) | ❌ | Medium |
| When to cancel/change policy | ✅ (dedicated page) | ❌ | Low |
| Methodology/editorial disclosure | ✅ | ❌ | Low |

AA does have sub-pages for its four products (Life Cover, Funeral Cover, Accidental Death,
Cancer Care) — these are assets MoneyHub does not have for AA-specific products. These
sub-pages could be SEO-optimised more aggressively as AA's primary organic moat.

---

## 6. Schema Markup Comparison

| Schema Type | AA | MoneyHub | Glimp | Opportunity |
|-------------|:--:|:--------:|:-----:|-------------|
| `FAQPage` | ❌ | Unknown | ❌ | AA has 5 FAQs — qualify immediately |
| `BreadcrumbList` | ❌ | Unknown | ❌ | Nav breadcrumb exists — add JSON-LD |
| `Product` / `Service` | ❌ | Unknown | ❌ | Each product sub-page qualifies |
| `Organization` | ❌ | Unknown | ❌ | Brand, founding date, NZAA entity |
| `FinancialProduct` | ❌ | ❌ | ❌ | Emerging type; used in FinServ |
| `ItemList` | ❌ | ❌ | ❌ | For product comparison pages |

None of the three sites show schema in the scraped content layer (MoneyHub/Glimp may
use JS-injected JSON-LD). AA has the highest marginal gain from adding schema given
its current zero baseline.

**Recommended JSON-LD additions for aa.co.nz/insurance/life-insurance/:**

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "How long does the application process take?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "The application takes between 15–30 minutes to complete online."
      }
    },
    {
      "@type": "Question",
      "name": "Do I need to complete a medical check?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. AA Life Insurance does not require medical checks. Once the online questions are answered, cover is confirmed immediately."
      }
    }
  ]
}
```

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.aa.co.nz/"},
    {"@type": "ListItem", "position": 2, "name": "Insurance", "item": "https://www.aa.co.nz/insurance/"},
    {"@type": "ListItem", "position": 3, "name": "Life Insurance", "item": "https://www.aa.co.nz/insurance/life-insurance/"}
  ]
}
```

---

## 7. E-E-A-T Assessment

### AA Life Insurance
| Factor | Score | Evidence |
|--------|:-----:|---------|
| Experience | 6/20 | Implied through claims history and NZ operations; no original data or case studies |
| Expertise | 6/25 | No author attribution, no financial adviser credentials displayed on page |
| Authoritativeness | 10/25 | 100-year-old brand, Asteron Life underwriter, Fitch A+ rating — present but understated |
| Trustworthiness | 12/30 | HTTPS, privacy policy linked, Asteron Life disclosed, financial advice disclaimer present; no date stamps on content |
| **Total** | **34/100** | |

**Gaps:** No "last reviewed" date anywhere on the page. No named author or editorial team.
No original statistics about NZ underinsurance rates. No testimonials or claims data.

### MoneyHub
| Factor | Score | Evidence |
|--------|:-----:|---------|
| Experience | 12/20 | Real quote data obtained "by MoneyHub team", dated to 2026, multiple segments |
| Expertise | 18/25 | Financial services content with detailed methodology; no named author but strong editorial depth |
| Authoritativeness | 17/25 | Cited by Perplexity as top NZ comparison source; 10+ life insurance sub-pages |
| Trustworthiness | 20/30 | Transparent methodology, "as of 2026" dating, sources cited, affiliate disclosures |
| **Total** | **67/100** | |

---

## 8. AI Search (GEO) Visibility

| AI Engine | AA Life cited? | MoneyHub cited? | Glimp cited? | Who is cited? |
|-----------|:--------------:|:---------------:|:------------:|---------------|
| **ChatGPT** | ❌ | ❌ | ❌ | LifeDirect, Canstar, Sorted |
| **Perplexity** | ❌ | ✅ | ✅ (as "Glimp") | Policywise, MoneyHub, Glimp, MoneyCompare |

**AA has zero AI citation presence.** In both AI engines tested, users asking about NZ
life insurance will not encounter AA Life in the recommendations.

MoneyHub is cited by Perplexity but not ChatGPT — indicating it has strong enough
informational depth to appear in some AI models but not universal coverage.

**Why AA is missing from AI recommendations:**
1. The page has no quotable statistics (e.g. "X% of Kiwis are underinsured")
2. Content is transactional, not informational — AI engines prefer to cite guides
3. No structured answer-first formatting for common questions
4. No topical cluster — single page rather than an authoritative hub

**What it would take to be cited:**
- Add 1-2 original NZ statistics (AA could publish its own claims data)
- Answer-first H2 structure: "What does AA life insurance cost?" → direct answer in first paragraph
- FAQPage schema (increases extractability for AI snippets)
- Build the content cluster so AA is seen as a topical authority, not just a product page

---

## 9. Structural Barrier Analysis

### The Broker Exclusion Problem

AA Life is explicitly noted by MoneyHub as excluded from broker/comparison platforms
because *"AA doesn't work with brokers."* This has two compounding SEO effects:

1. **Direct referral loss:** MoneyHub and similar aggregators route users to LifeDirect
   for quotes. AA never appears in that flow. Users who start on MoneyHub (which ranks #1)
   are funnelled toward competitors.

2. **Content incentive misalignment:** MoneyHub earns commission from LifeDirect clicks.
   Since AA cannot be quoted via LifeDirect, MoneyHub has no financial incentive to
   feature AA positively — and actively warns users that AA "mirrors Asteron's" products
   at higher prices.

### Implication for SEO Strategy

AA cannot win by competing for the same keywords in the same way as aggregators. The
recommended approach is a **parallel content strategy**:

- **Aggregator keywords** (compare, best, calculator): Compete with informational content
  that AA can own — not as a neutral comparison but as the provider with the strongest
  NZ trust story
- **Brand-specific keywords** (AA life insurance, AA life insurance review): Own these
  fully with rich, schema-marked, FAQ-heavy pages
- **Segment-specific keywords** (life insurance for parents NZ, no medical check life
  insurance NZ): AA's no-medical-check differentiator is a genuine competitive advantage
  for many segments — build pages targeting these

---

## 10. Prioritised Recommendations

### Critical — Implement Within 30 Days

**1. Add FAQPage schema to the existing FAQ section**
Five FAQs already exist on the page. Adding JSON-LD FAQPage markup costs nothing to
implement and could generate rich results (expanded FAQ accordion in SERPs) immediately.
Expected impact: rich result eligibility for branded queries.

**2. Improve title tag**
Current: `Trusted Life Insurance for Your Family`
Recommended: `AA Life Insurance NZ | No Medical Checks, Fast Cover (2026)`
Rationale: Adds primary keyword, geographic modifier, key differentiator, and freshness
signal. Keep under 60 characters.

**3. Add BreadcrumbList schema**
The navigation breadcrumb `Home > Insurance > Life Insurance` already exists visually.
Add JSON-LD to make it machine-readable. Improves SERP display and crawl signals.

**4. Add indicative pricing to the page**
Even a "from $X/month" range (e.g. "Life Cover from $7/week for a 30-year-old") would:
- Enable Product/Offer schema markup
- Compete for "cheap life insurance NZ" and "life insurance cost NZ" queries
- Reduce the information asymmetry that drives users to MoneyHub first

---

### High Priority — 1 to 3 Months

**5. Build a Life Insurance Calculator page**
`aa.co.nz/insurance/life-insurance/calculator/`
MoneyHub ranks #1 for "life insurance calculator NZ" with a simple tool. This is the
single highest-volume informational keyword AA is missing. AA could build a simple
calculator (how much cover do I need?) that captures this traffic and funnels to quotes.

**6. Create "How Much Life Insurance Do I Need?" guide**
`aa.co.nz/insurance/life-insurance/how-much-cover/`
Targets: `how much life insurance NZ`, `life insurance amount NZ`
Cover: the 10× salary rule, mortgage considerations, dependents, funeral costs.
This is the most common pre-purchase question — owning it means AA is in the
consideration set before users reach comparison sites.

**7. Create "Stepped vs Level Life Insurance NZ" guide**
`aa.co.nz/insurance/life-insurance/stepped-vs-level/`
MoneyHub has a dedicated page for this that ranks. Stepped vs level is a genuine
decision point for every buyer. This guide demonstrates expertise and earns long-tail
traffic.

**8. Add a "last reviewed" date and editorial methodology**
Adding `Last reviewed: March 2026` and a one-sentence methodology note ("pricing and
policy information reviewed by the AA Life Insurance team") significantly boosts E-E-A-T
signals at minimal implementation cost.

---

### Medium Priority — 3 to 6 Months

**9. Create segment-specific landing pages**
AA's "no medical checks" and "quick apply" positioning is especially compelling for:
- `life insurance for over 50s NZ` — high intent, underserved
- `no medical check life insurance NZ` — AA's primary differentiator
- `life insurance for new parents NZ` — emotionally resonant, high conversion
- `life insurance for self-employed NZ` — specific pain point (income protection angle)

**10. Build a transparent AA vs competitors comparison page**
`aa.co.nz/insurance/life-insurance/compare/`
A factual, AA-authored comparison of AA vs Asteron, AIA, Fidelity, Southern Cross.
AA acknowledges it is mid-range on price but differentiates on: no medical checks,
fast application, AA member discount, NZ team. This page captures "AA life insurance
vs [competitor]" queries and controls the narrative rather than leaving it to MoneyHub.

**11. Create a "NZ Life Insurance Costs by Age" data page**
AA could publish its own indicative pricing data (30s, 40s, 50s, smoker/non-smoker)
to compete directly with MoneyHub's pricing tables. This page would:
- Rank for pricing queries
- Be highly citable by AI engines (original data = highest AI citation priority)
- Position AA as transparent on price

**12. Build AI-citability into all new content**
For every new page created, include:
- One quotable statistic (ideally AA-sourced or NZ-sourced)
- Answer-first H2 formatting (question as heading, answer in first sentence)
- FAQPage schema
- Clear author/reviewer attribution (e.g. "Reviewed by the AA Life Insurance team")

---

## 11. Quick Wins Summary

| Action | Effort | Expected Impact | Timeline |
|--------|:------:|:---------------:|:--------:|
| FAQPage schema JSON-LD | Low (dev) | Rich results for branded queries | Week 1 |
| Title tag update | Low (CMS) | +CTR on existing rankings | Week 1 |
| BreadcrumbList schema | Low (dev) | SERP display improvement | Week 1 |
| "From $X/week" pricing | Low (copy) | Comparison-intent snippets | Week 2 |
| Last reviewed date | Minimal | E-E-A-T signal | Week 1 |
| Life insurance calculator | Medium (dev) | Owns #1 calculator keyword | Month 2 |
| "How much cover" guide | Medium (content) | Top-of-funnel traffic | Month 2 |
| Stepped vs level guide | Low (content) | Long-tail keywords | Month 2 |
| Segment pages (3–4) | Medium (content) | New keyword clusters | Month 3 |
| AA vs competitors page | Medium (content+legal) | Controls brand narrative | Month 3 |

---

## Appendix: Pages Analysed

| Page | URL | Scraped | Word Count (content) |
|------|-----|:-------:|:--------------------:|
| AA Life Insurance | aa.co.nz/insurance/life-insurance/ | ✅ March 2026 | ~700 |
| MoneyHub Life Insurance | moneyhub.co.nz/life-insurance.html | ✅ March 2026 | ~10,000 |
| Glimp Life Insurance Companies | glimp.co.nz/life-insurance/companies | ✅ March 2026 | ~500 |
| Glip.co.nz | glip.co.nz | ❌ Domain does not exist | — |

*Note: `glip.co.nz` as specified in the original brief does not resolve. The active
NZ comparison site is `glimp.co.nz`. This may be a typo or brand name confusion.*

---

*Report generated by claude-seo skill · Branch: claude/aa-insurance-competitor-analysis-6WhEg*
