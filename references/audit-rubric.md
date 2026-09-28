# SEO audit rubric

Use this reference for broad audits, prioritisation, or when sampling multiple route types. Apply only checks relevant to the product; absence from a generic checklist is not automatically a defect.

## Establish scope and coverage

Record:

- requested mode and mutation boundary;
- project/framework/rendering model;
- environments and canonical-origin evidence;
- route types: home, listing, detail, article, category, search/filter, locale, account/private, error, and dynamic routes;
- evidence available: source, build, local runtime, published HTTP/HTML, Search Console, Analytics, CrUX, Business Profile;
- sample size, crawl depth, exclusions, authentication boundary, and untested areas.

Do not claim “site-wide” coverage when only a few routes or the source tree were inspected.

## Severity

| Severity | Meaning |
| --- | --- |
| `BLOCKER` | Intended public content cannot be crawled, rendered, indexed, or resolved correctly; severe environment, status, redirect, or canonical failure |
| `HIGH` | Widespread or material search/user impact with a clear causal path |
| `MEDIUM` | Meaningful route-level weakness that should be corrected |
| `LOW` | Limited defect or maintainability/hygiene issue |
| `OPPORTUNITY` | Optional enhancement whose value depends on the product and search context |

Severity is not certainty. Mark uncertain findings `NEEDS_CONFIRMATION` and state the missing evidence.

## 1. Crawlability, indexability, and URL behaviour

- Representative public URLs return meaningful status codes.
- Missing content returns `404` or `410`, not a visually styled `200` soft 404.
- Redirects are intentional, finite, and converge on the preferred URL without avoidable chains.
- Authentication protects private data; robots is not used as access control.
- `robots.txt`, meta robots, and `X-Robots-Tag` do not accidentally block intended public pages or rendering resources.
- Canonical signals are consistent across redirects, HTML/header canonical, sitemap, internal links, protocol, host, path, parameters, and locale strategy.
- Paginated, filtered, searched, faceted, duplicate, print, and tracking variants have an explicit policy where relevant.
- Hreflang sets use equivalent confirmed pages, valid locale codes, self references, and reciprocal references when applicable.
- Sitemaps contain only confirmed canonical, public, indexable URLs. Coverage of dynamic routes is known. `lastmod` is factual; unsupported priority mythology is excluded.

Do not fail a page solely because it lacks a self-referencing canonical. Determine whether duplicate variants exist and whether the framework or platform has a deliberate policy.

## 2. Rendering and JavaScript SEO

- Important text, headings, links, metadata, and structured data exist in server/generated HTML where the architecture supports it.
- Client rendering, hydration, lazy loading, consent, errors, blocked resources, or API failures do not remove essential content from rendered output.
- Links use crawlable URLs rather than click handlers alone.
- Error and empty states return appropriate status/indexing signals.
- Browser console or network errors are treated as SEO findings only when they affect content, links, metadata, rendering, status, or user performance.
- Source HTML, rendered DOM, and published output are compared when JavaScript is consequential.

## 3. Page identity and visible content

- Each indexable route has a clear purpose supported by useful visible content.
- Titles are descriptive, concise in context, and distinguish important routes without boilerplate or placeholder text.
- Meta descriptions are factual and useful where supplied; missing descriptions are prioritised by route value rather than treated as a universal blocker.
- The main visible title is unambiguous and headings express a logical document structure. Multiple `h1` elements are reviewed in context, not failed mechanically.
- Content matches the stated offer and user intent without invented claims, keyword stuffing, mandatory word counts, or filler.
- Authorship, dates, qualifications, policies, contact details, and trust information are accurate where relevant.
- Duplicate/thin programmatic pages are evaluated by unique value, not text length alone.

## 4. Discovery, internal links, and navigation

- Important pages are reachable through crawlable internal links.
- Navigation, breadcrumbs, related content, category/listing paths, and contextual links reflect the real information architecture.
- Anchor text communicates the destination without forced keyword repetition.
- Broken, redirected, orphaned, circular, or environment-specific links are evidenced.
- Pagination and infinite-scroll experiences expose crawlable discovery paths where needed.

Do not require an arbitrary number of internal links per page.

## 5. Images and media

- Informative images have factual alternative text based on their content and function.
- Decorative images use empty alt text when appropriate; missing and intentionally empty alt are distinguished.
- Images have stable dimensions or aspect ratio where practical and responsive variants match display needs.
- Important media is accessible to crawlers and users; lazy loading does not hide content.
- Asset format, compression, preload/priority, caching, and third-party origins are evaluated from measured need.
- Image filenames are not used to invent people, locations, events, or product facts.

## 6. Structured data

- The selected type represents the main visible entity/content accurately.
- Required and recommended properties are checked against current primary documentation.
- JSON-LD parses, uses canonical absolute URLs where required, and matches visible content.
- Ratings, reviews, price, availability, author, dates, organisation, local business, FAQ, product, article, breadcrumb, and other properties are genuine and policy-compatible.
- Duplicate/conflicting graph nodes and identifiers are resolved.
- Rich Results Test eligibility is separate from a guarantee that a rich result will appear.

Syntactically valid JSON-LD is not a semantic pass.

## 7. Performance and user experience

- Use current Core Web Vitals and distinguish lab measurements from real-user field data.
- Investigate LCP, INP, and CLS causes using route/device evidence rather than chasing a score.
- JavaScript, CSS, fonts, images, third-party scripts, caching, compression, and rendering strategy are prioritised by measured impact.
- Mobile usability, accessibility, intrusive overlays, layout stability, and interaction responsiveness are considered part of the user experience.
- A local Lighthouse run does not prove CrUX or Search Console field performance.

## 8. Local and entity SEO

- Confirm whether the organisation has a customer-facing location, service area, online-only model, or multiple locations.
- Verify visible name, address, phone, hours, service area, categories, and location pages against owner-confirmed facts.
- Evaluate Business Profile state only with real access/evidence.
- LocalBusiness/Organization/Person/WebSite choices follow the real entity and visible page content.
- Never fabricate coordinates, ratings, reviews, locations, services, or opening hours.

## 9. Social, browser, and optional discovery

- Open Graph/social cards accurately represent the page and use approved assets.
- Favicons and manifests are valid for browser presentation.
- `llms.txt` is evaluated only as an optional AI-discovery convention with an explicit content scope.
- These items remain labelled separately from core crawl/index/search issues.

## 10. Measurement and external services

- Analytics code, consent, events, and measurement IDs are confirmed before change.
- Search Console ownership, sitemap submission, coverage, selected canonical, manual actions, and performance data are reported only from observed account evidence.
- Search demand, queries, impressions, clicks, CTR, conversions, rankings, and competitors are not invented from code.
- Monitoring recommendations identify the account/access required and the exact post-deploy check.

## Finding format

```markdown
### [SEVERITY] Short finding title

- Category:
- Status: CONFIRMED | NEEDS_CONFIRMATION
- Affected routes/files:
- Evidence:
- Why it matters:
- Recommended action:
- Missing input/access:
- Validation required:
```

Avoid a synthetic SEO score. Summarise counts only after deduplicating a shared root cause; one faulty layout affecting 100 pages is normally one systemic finding with 100 affected routes, not 100 independent defects.
