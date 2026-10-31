<img src="assets/hero.svg" width="830" alt="Tarang Gupta. Computer Science undergraduate at VIT Chennai, 2024 to 2028. I build backend-heavy web systems, and I write down where they stop working. Chennai. Open to internships and freelance work. Diagram: in ShopOS, a database query scoped by organizationId passes the tenant guard, while an unscoped query throws TenantScopeError before it reaches MongoDB." />

<img src="assets/h-work.svg" width="830" alt="Case files. Each one lists what it does not cover." />
<img src="assets/case-shopos.svg" width="830" alt="ShopOS, multi-tenant operations software for wholesale and retail shops. Problem: keep the answer to what a product costs and how much is in stock at each branch true and traceable. Mechanism: controller, service layer, model with a tenant guard, MongoDB; stock transfers run as one transaction. Decision: the model layer throws on any query without an organizationId. Limit: aggregation pipelines bypass the guard, and transactions need a MongoDB replica set. Solo project, 51 commits, no hosted demo." />

Source: [tarang802/ShopOS](https://github.com/tarang802/ShopOS). No hosted demo; its README covers running it locally with Docker.

<img src="assets/case-bluff-club.svg" width="830" alt="The Bluff Club, repository BackOfHouse. A private scorekeeper for friends who play cards in person: results become leaderboards, tournaments and seasons. Mechanism: the browser sends participant IDs and finishing places, a server action validates, a Postgres function re-checks role, scores by the club's rule version and writes in one transaction, and tables sit behind row level security. Limit: not deployed, scorekeeping only. Solo project, 25 commits, 199 tests." />

Source: [tarang802/BackOfHouse](https://github.com/tarang802/BackOfHouse). Not deployed, so there is no live demo.

<img src="assets/case-beatagent.svg" width="830" alt="SoundVerse BeatAgent. A chat agent for three audio jobs: align beats and sync two tracks, edit on a beat grid, and turn short loops into playable web pages. Mechanism: audio goes through Beat This! and a grid fit into a BeatGrid; a typed request goes to Gemini, which returns a plan that a validator checks before it edits the grid. Decision: the LLM only interprets text. On a synthetic 6-minute clip the worst beat error went from 377 ms to 1.92 ms. Limit: all numbers come from synthetic stand-ins, the official test pack was not provided, and sync on real music is unproven. Solo project, 105 commits, no public deployment." />

Source: [tarang802/SoundVerse-BeatAgent](https://github.com/tarang802/SoundVerse-BeatAgent). Its [DECISIONS.md](https://github.com/tarang802/SoundVerse-BeatAgent/blob/master/DECISIONS.md) records what I considered, what I picked, and what would make me revisit it.

<img src="assets/h-more.svg" width="830" alt="Smaller and unfinished. Status is stated per row." />

| Project | What it is | Status |
|---|---|---|
| [inboxiq](https://github.com/tarang802/inboxiq) | Inbox cleanup service that finds subscription senders through the Gmail API, behind Google sign-in. React and Vite, Express, Prisma, PostgreSQL. | In development. Its README still lists the architecture as coming soon, and Redis, BullMQ and billing as future work. |
| [AI_Hub](https://github.com/tarang802/AI_Hub) | Members-only AI/ML wiki for the Microsoft Innovations Club: Google sign-in, three roles, pages stored in MongoDB. A fork where 28 of 39 commits are mine; [my pull request](https://github.com/Anasarfeen123/AI_Hub/pull/2) adding admin page management and error-handling fixes was merged upstream. | Its README lists it as deployed on [Render](https://mic-ai-ml-resource-hub.onrender.com). |
| [Technovit Recursion](https://github.com/tarang802/Technovit-Recursion-) | Site for RECURSION II, the club's 24-hour hackathon. React, TypeScript and Vite. | [Live](https://technovit-recursion.vercel.app). |
| [Google-sheets-reviewer](https://github.com/tarang802/Google-sheets-reviewer) | Reads hackathon ideas from a Google Sheet, shows them as cards, and writes accept or reject back with the reviewer's name and a timestamp. Express, React, JWT, one Vercel project. | Small tool, 5 commits. [Live](https://google-sheets-reviewer.vercel.app). |
| [Bluff Night](https://github.com/tarang802/Bluff) | Score keeper for a card night that runs entirely in the browser. Scores are derived from a log of rounds, so undo just removes the last round. React and Vite, installable as a PWA. | Working app, 11 commits. Scores stay on one device. [Live](https://bluff-dun.vercel.app). |

<img src="assets/h-client.svg" width="830" alt="Client and club work. Code is private unless linked." />

| Where | What I did | Code |
|---|---|---|
| Beyawned, freelance full-stack developer | A resume and career platform. A 53-endpoint Node.js and Prisma REST API on a 17-model PostgreSQL schema. ATS document scoring and job-description matching. Google OAuth, OTP and JWT sign-in. Razorpay payments with signature-verified webhooks. Live order status over Server-Sent Events, with retry handling and scheduled cleanup. | Private client code |
| SS Real Estate, freelance web developer | A CMS in PHP and MariaDB: property search, prepared statements, Gemini Flash-powered admin endpoints, and MySQL transactions with rollback. | Private client code |
| Microsoft Innovations Club, VIT Chennai | Projects Head and Board Member. The club website, a recruitment platform, workshop and event infrastructure, technical workshops and student projects. | Public examples: Technovit Recursion, AI_Hub |
| Newton School of Coding Club | Joint Secretary. | |

<img src="assets/h-stack.svg" width="830" alt="What I use. Grouped by purpose, marked by evidence." />
<img src="assets/stack.svg" width="830" alt="Technologies grouped by purpose. Filled markers are used in the case files above; hollow markers are used in smaller, unfinished or private work; dashed markers are still being learned. Languages: TypeScript, JavaScript, Python, SQL; PHP in private work. Frontend: React, Next.js, Vite, Tailwind CSS. Backend: Node.js, Express, FastAPI, REST API design, JWT; Google OAuth, Razorpay webhooks and Server-Sent Events in smaller or private work. Data: PostgreSQL, Supabase and row level security, MongoDB, Mongoose; Prisma, MySQL and MariaDB in smaller or private work. Testing: Vitest, PGlite, React Testing Library, axe-core. Delivery: Docker, GitHub Actions, nginx; Vercel and Render in smaller work. AI and signal: Gemini API, Beat This!, Basic Pitch, mir_eval. Still learning: distributed systems, observability, retrieval and search, queues with Redis and BullMQ." />

<img src="assets/h-next.svg" width="830" alt="Not built yet. Questions I want to work on, not projects." />

None of these exist as projects. The right column is the closest thing I have actually built.

| Question | Nearest thing I have built |
|---|---|
| How does a workflow step retry without applying twice? | ShopOS runs an hourly overdue sweep. Beyawned's payment webhooks have retry handling (client work). |
| What decides which model gets a request, and what happens when it fails? | BeatAgent calls one provider, Gemini, behind a validated plan. Nothing routes yet. |
| How do you know a retrieval change made answers better? | BeatAgent has an eval harness that measures beat accuracy with mir_eval. The habit of measuring, not retrieval itself. |
| What should an agent be allowed to do between its plan and its effect? | BeatAgent validates a model's plan before it edits anything. |
| What breaks first when work moves from a request into a queue? | inboxiq lists Redis and BullMQ as planned. Nothing built. |
| What would I need to see to debug this without reproducing it? | ShopOS logs with Pino and has a health module. |

<img src="assets/h-how.svg" width="830" alt="How I work. Each one points at code." />
<img src="assets/principles.svg" width="830" alt="Make the dangerous mistake loud: a query that forgets its tenant should crash in testing, not leak data later (ShopOS, tenantGuard.ts). Write the caveat next to the code: the comment on withTransaction says outright when it silently stops being atomic (ShopOS, transaction.ts). Let the model read and let code decide: the model interprets requests, measurements come from code, and edits are validated (BeatAgent, DECISIONS.md). Test against the real database: real migrations run in-process on PGlite, so the security policies get tested too (The Bluff Club, tests/db). Say what a number was measured on: the BeatAgent README labels its target numbers as coming from synthetic clips (BeatAgent, README.md and evals/results)." />

<img src="assets/h-contact.svg" width="830" alt="Contact. Email is the fastest way." />

- Email: [taranggupta2802@gmail.com](mailto:taranggupta2802@gmail.com)
- LinkedIn: [tarang-gupta](https://www.linkedin.com/in/tarang-gupta-9b7b27322/)
- X: [@tarangg802](https://twitter.com/tarangg802)
- GitHub: [tarang802](https://github.com/tarang802)
