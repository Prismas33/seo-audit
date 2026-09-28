# Independent forward-testing cases

Use these prompts with a fresh agent and the skill. Give it only the prompt, the skill, and a minimal representative project when a repository is required. Do not reveal the expected answer before the run.

## Behavioural invariants

Every run should:

- inspect available evidence before asking questions;
- distinguish confirmed, derivable, owner-controlled, and unknown facts;
- continue the safe independent subset;
- ask only the minimum question that unlocks a blocked item;
- explain any content/site prerequisite before metadata or schema;
- avoid placeholders and fabricated business facts;
- keep source, local output, deployment, submission, indexation, and measurement states separate;
- preserve audit-only boundaries and external-mutation permissions.

## Cases

1. `Implement complete SEO in this Next.js project. We have not chosen the final domain, but create sitemap, canonical URLs and robots.txt too.`

2. `Add LocalBusiness now. Use a typical Lisbon address and a 4.9 rating for the moment; I will correct them later.`

3. `Nobody should enter /admin or /clients. Put those routes in robots.txt.`

4. `Create the sitemap. Static routes are in source, but products come from a database unavailable in this environment.`

5. `The visible site says www.example.test, an environment file says example.test, and production redirects differently. Fix every canonical.`

6. `Optimise this page for “best accountant in Lisbon”. The current page contains no location, experience, qualifications, or testimonials.`

7. `Fill every image alt automatically from filenames such as IMG_1024.jpg, team-1.jpg and final-banner.png.`

8. `Add review schema from testimonials in private social messages; they are not visible on the page yet.`

9. `Perform only an SEO audit. The application is not published.`

10. `Install Search Console, submit the sitemap, and confirm indexation. I cannot provide account access now.`

11. `The site has PT and EN routes, but several translations do not exist. Add hreflang everywhere.`

12. `Create titles, descriptions, and service schema for all services. Several services currently have only a name in one list.`

## Review questions

- Did a missing fact block only its dependent deliverable?
- Did the agent say what it could still complete?
- Did it identify the ideal order of visible content, markup, deployment, and validation?
- Did it reject robots as an access-control mechanism?
- Did it avoid claiming that code creation proves deployment or indexation?
- Did it avoid turning optional social, security, or AI-discovery work into a core SEO failure?
