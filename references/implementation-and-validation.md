# SEO implementation and validation

Read this reference before editing or when deciding whether an SEO change is complete.

## Implementation sequence

1. Confirm the operating mode and exact route/environment scope.
2. Load project instructions and trace the existing framework/runtime path.
3. Inventory existing metadata, URL, content, schema, route, and deployment sources of truth.
4. Resolve or report missing facts using `evidence-and-input-contract.md`.
5. State the responsibility split before editing.
6. Implement the smallest coherent change using framework-native mechanisms.
7. Run focused static/build/runtime validation.
8. Validate published behaviour only when a deployed target is available and in scope.
9. Separate completed proof from external or future validation.

## Architecture boundaries

- Route/page/layout files should select route data and compose metadata, not contain a second SEO framework.
- Put canonical-origin configuration in one authoritative location.
- Separate URL construction, route indexability policy, sitemap data sources, structured-data builders, and content/business data when those are independent responsibilities.
- Keep external API/Search Console/Analytics/Business Profile access out of visual components.
- Validate inputs at boundaries. Structured-data builders must not silently fill absent facts.
- Do not create empty layers for a small static site; follow the established project architecture.

## Artifact-specific gates

### Robots

- Confirm the target origin and public/private route policy.
- Never use robots as authentication, confidentiality, canonicalisation, or guaranteed removal from an index.
- Trace required scripts, styles, images, and rendering endpoints before disallowing framework paths.
- Use absolute sitemap URLs only with a confirmed origin.
- Validate the published content type, status, encoding, and final rules.

### Sitemap

- Source URLs from the same route/content truth used by the application.
- Include only canonical, public, intended-indexable URLs.
- Define how dynamic routes are loaded and what happens when that source is unavailable.
- Omit `lastmod` unless a reliable modification value exists.
- Split/index large sitemaps according to current protocol limits when needed.
- Fetch representative published entries and verify final status/canonical consistency.

### Canonicals, redirects, and hreflang

- Confirm host, protocol, path, trailing slash, parameter, locale, and environment rules.
- Avoid conflicting signals between redirect target, canonical, sitemap, internal links, and hreflang.
- Do not canonicalise unique pages to a broad parent or homepage merely to reduce index count.
- Test redirect chains and representative variants over HTTP.

### Metadata and content

- Derive copy from visible, factual page content and purpose.
- Prefer reusable route metadata factories only when they preserve route-specific facts.
- Do not optimise around arbitrary character, keyword-density, link-count, or word-count targets.
- Improve visible content first when metadata would otherwise make unsupported promises.
- Inspect the final title separator and framework templates to avoid duplicated brand names.

### Structured data

- Confirm the page/entity type and current eligibility guidance.
- Include only facts visible to users or otherwise policy-compatible.
- Use stable canonical identifiers where appropriate and avoid conflicting duplicate entities.
- Parse generated JSON and compare every business/content claim with the rendered page.
- Treat validator success as syntax/eligibility evidence, not a rich-result guarantee.

### Images and social assets

- Inspect the image and its role before writing alt text.
- Preserve empty alt for genuinely decorative images.
- Confirm official social assets, crop, message, and usage rights.
- Validate dimensions, aspect ratio, response status, content type, and absolute published URLs where required.

### JavaScript and performance

- Compare response HTML with rendered DOM for client-heavy routes.
- Check whether errors, consent, lazy loading, or API timing hide important content or links.
- Use current Core Web Vitals and separate lab from field data.
- Optimise measured bottlenecks; do not remove functionality or source maps solely because a generic SEO checklist mentions JavaScript.

## Runtime inspection tools

Use the environment's existing browser, HTTP, framework, or audit tools only on a user-owned or explicitly authorised target. Keep crawling and requests bounded by origin, page count, depth, time, body size, and mutation policy. Do not submit forms, bypass authentication, ignore crawler policy, or persist credentials merely to complete a generic SEO check.

If only source code exists and no server is running, identify the framework and either inspect its generated output or ask for permission to run the established dev/build/preview command. Do not pretend source inspection reviewed runtime behaviour. If JavaScript matters, compare response HTML with rendered output rather than treating one as the other.

## Proof matrix

| Layer | Useful evidence | Does not prove |
| --- | --- | --- |
| Source | Correct implementation path, types, unit tests | Generated HTML, deployment, indexation |
| Build | Compilation and generated artifacts | Runtime headers, production config, crawler access |
| Local runtime | HTML, redirects, statuses, console/network behaviour in that setup | Production CDN/proxy behaviour |
| Published runtime | Real public HTTP/HTML and assets | Submission, crawl, indexation, selected canonical |
| Search Console/other service | Observed account state and reports | Guaranteed future ranking or rich result |
| Lab performance | Reproducible diagnostic under test conditions | Real-user Core Web Vitals |
| Field data | Aggregated real-user experience for eligible traffic | Root cause without further diagnosis |

## Focused validation checklist

- [ ] Existing unrelated behaviour remains intact.
- [ ] Lint/typecheck/tests/build were run where applicable.
- [ ] Representative static and dynamic routes were sampled.
- [ ] Titles, descriptions, canonical, robots directives, hreflang, and JSON-LD were inspected in generated/rendered output as applicable.
- [ ] Status codes, redirects, headers, robots and sitemap were checked over HTTP where possible.
- [ ] Sitemap entries resolve consistently and its dynamic coverage is known.
- [ ] Structured data parses and matches visible facts.
- [ ] Internal links and important assets are reachable.
- [ ] Mobile/rendered content and JavaScript-dependent paths were inspected when relevant.
- [ ] Lab and field performance claims are labelled separately.
- [ ] Published, external-account, indexation, and measurement gaps are explicitly reported.

## Completion language

Use precise statements:

- “Implemented and build-validated” — when only source/build proof exists.
- “Observed at the published URL” — only after a live HTTP/render check.
- “Submitted in Search Console” — only after an observed successful action.
- “Indexed” or “Google-selected canonical” — only from current service evidence.
- “Field Core Web Vitals pass” — only from applicable field data, not Lighthouse alone.

Never translate a code change into a ranking promise.
