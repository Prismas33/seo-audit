---
name: seo-audit
description: Audit, plan, implement, and validate evidence-based SEO improvements for websites and web applications when organic search is materially in scope. Use for technical or on-page SEO, SEO-focused content, crawlability, indexability, SEO metadata, robots, sitemaps, canonicals, structured data, local SEO, search-relevant JavaScript rendering, internal links, or organic-search diagnostics; do not use for paid-search campaigns or general marketing work.
metadata:
  author: Prismas33
  version: "1.0.0"
---

# SEO Audit & Improvement

Improve search discoverability from evidence. Make the site technically understandable, indexable where intended, useful to people, and truthful about the organisation or content it represents.

## Select the operating mode

Infer the mode from the request and preserve its boundary:

- **AUDIT**: inspect and report; do not edit code, deploy, submit, or change external services.
- **IMPLEMENT**: make the requested local changes, then validate them proportionally.
- **ADVISORY**: explain priorities, prerequisites, and an implementation sequence without changing the project.

An audit or review request is not permission to implement. A request to implement SEO is permission for scoped local changes, not for production deployment, Search Console submission, Analytics changes, Business Profile edits, domain purchases, or other external mutations unless those are explicitly requested.

## Start from evidence

For project- or site-specific work, inspect the relevant available evidence before recommending or editing. General advisory questions may proceed from the supplied context when no project inspection is needed; state the resulting limits.

1. Read project instructions, documentation, accepted decisions, relevant configuration, route definitions, metadata code, content sources, public assets, build scripts, tests, and deployment configuration.
2. Identify the framework, rendering model, public route surface, dynamic route sources, locales, environments, and existing SEO abstractions. Keep pages and route entrypoints thin; place reusable metadata, schema, URL, and route-policy logic in clearly named modules.
3. When in scope and technically possible, inspect generated or server-rendered HTML, HTTP status and redirect behaviour, response headers, `robots.txt`, sitemaps, and representative routes. Keep any crawl or HTTP inspection bounded and authorised; it does not prove indexation.
4. Distinguish the evidence layers explicitly:
   - present in source;
   - produced by a build or local runtime;
   - observed at a published URL;
   - submitted to an external service;
   - observed as indexed, selected, or measured by that service.
5. Continue with safe, independent work before asking questions. Do not open with a generic SEO questionnaire.

For a comprehensive review, read [references/audit-rubric.md](references/audit-rubric.md).

## Truth-lock every value

Classify information before using it:

- `CONFIRMED`: stated in an authoritative project source, observed in the relevant environment, or explicitly confirmed by the user.
- `DERIVED`: a mechanical transformation of confirmed facts that adds no new factual claim.
- `OWNER_INPUT`: a commercial, legal, editorial, strategic, or account fact that only the owner can confirm.
- `UNKNOWN_OR_CONFLICTING`: absent, ambiguous, stale-looking, placeholder-like, or contradicted by another source.

Only `CONFIRMED` and safe `DERIVED` values may enter published metadata, content, structured data, sitemaps, redirects, or integrations.

Never treat examples, fixtures, mocks, seed data, `.env.example`, filenames, comments, AI-generated copy, screenshots, guide snippets, or plausible defaults as business truth. Never invent or silently complete:

- a canonical domain, protocol, subdomain, locale, country, or target market;
- a brand or legal name, address, coordinates, phone number, email, opening hours, or service area;
- products, services, prices, currencies, stock, guarantees, qualifications, awards, or experience;
- authors, publication or modification dates, ratings, reviews, customer counts, or statistics;
- social profiles, official images, image rights, Analytics/Search Console IDs, or Business Profile data;
- search demand, rankings, competitors, audience intent, conversions, or measured performance.

Do not publish `TBD`, `example.com`, sample company data, provisional ratings, fake reviews, invented alt text, or similar placeholders. If a value is not confirmed, omit the optional field or block only the dependent deliverable.

## Handle missing information constructively

Missing information is part of the SEO work, not a reason to guess or stop everything.

For each gap:

1. Determine what can be implemented correctly now.
2. Decide whether the missing value is:
   - **blocking**: the requested artifact would be false, unsafe, or technically wrong without it;
   - **non-blocking**: omitting it still leaves a correct result, but limits an improvement;
   - **external-access dependent**: validation or mutation requires an account, deployed URL, or permission not currently available.
3. Explain the upstream improvement when the requested artifact would only mask a deeper gap. Metadata and schema must follow real visible content; they do not replace it.
4. Give the ideal sequence in plain language.
5. Ask only when the answer is necessary to fulfil the requested scope or unlock the next safe action. Group closely related blockers, normally in one to three short questions. Otherwise report or omit an optional value without asking.
6. Continue all safe independent work, including unaffected parts of the same deliverable. If the user cannot answer, omit optional values, leave only the affected item explicitly blocked, and state how to resume it later.

Use equivalent labels in the user's language when a gap matters. For one simple gap, a concise sentence covering these fields is enough; do not force a six-line template mechanically.

```text
Entregável:
Consigo fazer agora:
Informação ou acesso em falta:
Porque é necessário:
Ordem ideal:
Pergunta mínima:
```

The expected reasoning is often:

```text
confirm facts -> improve visible site/content -> add metadata or schema
-> validate generated and published output -> monitor real search data
```

Example: if a production hostname is not confirmed, route policy can still be audited and a framework-native sitemap implementation can sometimes be prepared, but absolute canonical and sitemap URLs must not be fabricated. Explain that the preferred origin should be confirmed first, then implement consistent canonicals, sitemap URLs, redirects, and finally validate the published responses.

Read [references/evidence-and-input-contract.md](references/evidence-and-input-contract.md) whenever data is missing or conflicting, and before creating canonicals, redirects, robots, sitemaps, hreflang, local SEO, business/content schema, or external-service integrations.

## Prioritise real SEO risk

Classify findings by user and search impact, not checklist count:

1. **BLOCKER** — intended public content cannot be crawled, rendered, indexed, or resolved correctly; severe canonical, status, redirect, or environment error.
2. **HIGH** — widespread wrong or duplicate metadata, broken route discovery, incorrect structured data, missing critical content, or major internal-link/rendering failure.
3. **MEDIUM** — meaningful route-level weakness with a clear corrective action.
4. **LOW** — limited defect or hygiene issue.
5. **OPPORTUNITY** — optional enhancement whose value depends on product and search context.

Keep adjacent concerns labelled accurately:

- Open Graph, social cards, and favicons affect sharing or presentation; they are not automatically ranking issues.
- JavaScript bundle size and console errors matter to SEO when they affect rendering, links, content, or user performance; they are not ranking shortcuts.
- Production source maps are primarily an operations/security decision, not a generic SEO fix.
- `llms.txt` is an optional AI-discovery convention, not a substitute for crawlable content, robots, sitemaps, or proven search requirements.
- A custom 404 must return an actual `404` status; appearance alone does not prevent a soft 404.

Do not use arbitrary keyword density, mandatory word counts, fixed numbers of internal links, universal title/description character limits, or a mechanical one-`h1` rule as pass/fail criteria. Evaluate clarity, uniqueness, hierarchy, intent, and rendered behaviour in context.

## Implement with framework and route context

When implementation is requested:

- Prefer the framework's supported metadata, route, sitemap, robots, redirect, and rendering mechanisms.
- Reuse existing URL/config/content sources and abstractions when they are authoritative. Resolve conflicts instead of creating a second source of truth.
- Keep domain/configuration facts separate from route generation and presentation.
- Generate sitemaps only from confirmed canonical, public, indexable URLs. Do not fabricate `lastmod`; omit it when no factual modification source exists.
- Use `robots.txt` for crawl guidance, not authentication, confidentiality, canonicalisation, or guaranteed de-indexing. Never add broad disallows for framework assets or APIs without tracing what public rendering needs.
- Add canonicals and hreflang only after the preferred origin, URL variants, languages, and regional relationships are understood.
- Make structured data match visible page content and the correct entity. Omit unsupported optional properties; never add fake reviews, ratings, prices, people, locations, or dates.
- Treat empty `alt=""` as potentially correct for decorative images. Inspect the image and its function before writing alternative text; filenames alone are not evidence.
- Preserve existing product behaviour, accessibility, analytics, consent, permissions, and deployment contracts.
- Avoid broad refactors. Record out-of-scope findings separately.

Read [references/implementation-and-validation.md](references/implementation-and-validation.md) before editing or claiming validation.

## Validate without overclaiming

Use the narrowest applicable evidence:

- focused lint, typecheck, tests, and build;
- generated metadata/routes/files;
- representative HTML before and after JavaScript where relevant;
- HTTP status, redirects, headers, canonical targets, robots and sitemap responses;
- JSON-LD syntax plus semantic comparison with visible content;
- internal-link and asset checks;
- local lab performance and, separately, real-user field data when available;
- published checks only when a deployed URL is actually accessible;
- Search Console, Analytics, Business Profile, or rich-result state only when access and direct evidence exist.

A successful build does not prove deployment, crawling, indexation, Google's selected canonical, rich-result eligibility, ranking improvement, or Core Web Vitals field performance. State each unverified layer.

When current search-engine behaviour matters, verify it against live primary documentation. Read [references/official-sources.md](references/official-sources.md) for source routing; do not preserve an old checklist rule merely because it is common SEO advice.

## Report the outcome

For each finding include:

```text
Severity and category:
Affected route or file:
Evidence:
Why it matters:
Recommended or implemented change:
Validation:
Remaining dependency or uncertainty:
```

End implementation work with these sections when applicable:

- **Implemented and validated**
- **Implemented but needs published validation**
- **Blocked by information or access**
- **Optional improvements**
- **Ideal next sequence**
- **Not verified**

Do not create a fake aggregate SEO score. Report coverage and evidence instead. Never promise rankings or dates for search results.

## Bundled resources

- [references/audit-rubric.md](references/audit-rubric.md): comprehensive audit scope, severity, and finding format.
- [references/evidence-and-input-contract.md](references/evidence-and-input-contract.md): missing-data decision matrix and no-invention examples.
- [references/implementation-and-validation.md](references/implementation-and-validation.md): safe implementation and proof boundaries.
- [references/official-sources.md](references/official-sources.md): primary-source routing for current guidance.
