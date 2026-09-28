# Evidence and missing-input contract

Use this reference whenever an SEO deliverable depends on identity, domain, content, route policy, commercial facts, dates, external accounts, or another value that is missing or contradictory.

## Evidence classes

| Class | Meaning | May enter a published artifact? |
| --- | --- | --- |
| `CONFIRMED` | Explicit user confirmation, accepted project decision, or direct observation in the relevant target environment | Yes |
| `DERIVED` | Mechanical transformation of confirmed facts with no new factual claim | Yes |
| `OWNER_INPUT` | Commercial, legal, editorial, strategic, or account truth controlled by the owner | Only after confirmation |
| `UNKNOWN_OR_CONFLICTING` | Missing, ambiguous, placeholder-like, stale-looking, or contradicted | No |

Source code is authoritative for implementation behaviour, not automatically for commercial truth. A string found in a component may be a placeholder. A production response is authoritative for what is currently served, not necessarily for what the business wants. Identify the authority appropriate to the fact.

## Progress-first decision flow

1. Inspect before asking: project docs, configuration, routes, content, assets, tests, generated output, and published output when in scope.
2. List the safe independent work and complete it when implementation is authorised.
3. Classify each gap:
   - `BLOCKING`: using a guessed value would make the requested output false, unsafe, or technically incorrect;
   - `NON_BLOCKING`: the value improves completeness but can be omitted correctly;
   - `ACCESS_DEPENDENT`: evidence or mutation requires a deployed environment, account, credential, or permission.
4. Explain any prerequisite improvement. Do not use a metadata file to disguise weak or absent visible content.
5. Ask only when the answer is necessary for the requested scope or unlocks the next safe action. Group related blockers; do not send a broad intake questionnaire. Otherwise report or omit an optional value without asking.
6. Continue all safe independent work, including unaffected parts of the same deliverable. If no answer is available, omit optional data and report only the dependent item as blocked without publishing placeholders.

## Gap format

Use equivalent labels in the user's language. A single simple gap may be one concise sentence covering the same information; use the expanded form only when it improves a decision.

```text
Entregável:
Consigo fazer agora:
Informação ou acesso em falta:
Porque é necessário:
Ordem ideal:
Pergunta mínima:
```

Good language is specific and progressive:

> Com os dados atuais consigo fazer X. Falta Y para concluir Z sem inventar. Idealmente, primeiro melhoramos A no conteúdo/site, depois implementamos B e por fim validamos C. Preciso apenas de confirmar D.

## Decision matrix

| Deliverable | Safe derivation | Requires confirmation | If missing |
| --- | --- | --- | --- |
| `robots.txt` | Existing explicit public/private route policy | Ambiguous crawl policy; absolute sitemap origin | Do not invent `Disallow`; explain that robots is not access control; omit only the blocked directive |
| Sitemap | Confirmed public canonical routes and factual update data | Canonical origin; source of dynamic routes; intended indexability | Generate only proven coverage or prepare the generator without calling it complete; omit non-factual `lastmod` |
| Canonicals and redirects | Observed duplicates and accepted URL rules | Preferred host/protocol, locale, parameters, trailing-slash policy | Ask before choosing; never canonicalise unrelated pages to the homepage |
| Hreflang | Confirmed equivalent locale URLs | Supported locales, regional targeting, translation completeness | Implement only complete equivalent sets; report missing translations |
| Titles and descriptions | Visible page purpose that is factual and unambiguous | Positioning, audience, offer, or location when unclear | Write only supported copy; recommend visible content first when substance is absent |
| Structured data | Visible facts and an unambiguous entity/page type | Missing identity, business, product, author, date, price, review, or location facts | Omit optional properties; do not create a misleading or ineligible entity |
| Local SEO | Consistency of already published NAP and location content | Official name, physical/service-area model, address, phone, hours, category | Audit gaps; do not fabricate `LocalBusiness`, coordinates, opening hours, or reviews |
| Image alt text | The inspected image's function and visible context | Identity, event, place, or meaning not safely observable | Use `alt=""` only when decorative; otherwise request context; never infer from filename alone |
| Open Graph/favicon | Approved existing brand assets and page facts | Official asset, message, crop, and usage rights | Report the missing asset and propose creation/approval first |
| Content/search intent | Existing factual content and real first-party search data | Audience, market, offer, expertise, differentiation, editorial intent | Ask targeted editorial questions; do not generate claims or text to hit a word count |
| Analytics/Search Console | Confirmed existing integration and property | Account/property, measurement ID, consent and authorisation | Prepare a documented integration point only if useful; never invent an ID or claim submission |
| Business Profile | Public business facts and authorised account access | Ownership, category, location/service area, hours | Provide a preparation checklist; never claim edits or verification without access |
| `llms.txt` | Confirmed public content and canonical links | Intended audience and inclusion scope | Treat as optional; never present it as a ranking requirement |

## Truth that must never be inferred

- Domain ownership or the preferred canonical hostname.
- Legal/company identity, NAP, coordinates, service area, or opening hours.
- Product/service availability, price, currency, guarantees, or regulated claims.
- A person's identity, role, qualifications, experience, or relationship to an image.
- Ratings, reviews, review counts, customers, awards, performance claims, or dates.
- Social profiles, official logos, brand imagery, or usage rights.
- Search demand, rankings, competitors, conversions, or the meaning of Analytics data.
- Search Console, Analytics, Business Profile, merchant, or advertising identifiers.
- Supported languages, regional targets, or translation equivalence.

## Content before markup

When the site does not visibly support the requested claim, use this order:

```text
confirm the fact
-> add or improve useful visible content
-> align title, description, headings, links, and schema
-> validate rendered output
-> validate published output
-> monitor real search evidence
```

Examples:

- A technically unique title for “best accountant in Lisbon” is not defensible when the page contains no location, qualifications, services, or supporting evidence. Ask for factual service and location information; improve the page before intensifying the title.
- `LocalBusiness` must not be created from a typical address. Confirm whether customers are served at a physical location or through a service area, publish the true contact information visibly, and only then reflect it in JSON-LD.
- Reviews copied from a private message or social platform must not become review schema unless their use is authorised, they are genuine, and the applicable page visibly presents them in a policy-compliant way.

## External-state boundary

Never say an item was submitted, indexed, selected, measured, verified, or improved unless the relevant service was accessed and the outcome observed. Keep these states separate:

```text
prepared in source
-> generated locally
-> deployed
-> reachable publicly
-> submitted
-> crawled/indexed or measured
```
