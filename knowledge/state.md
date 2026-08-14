# Current state

Updated 2026-08-14. Read this first, then `decisions.md`, `open-questions.md`, `feature-graph.md`,
`prior-art.md`.

## Where the project stands

The repository is deployable. A single Next.js application builds and runs, with configuration,
observability, a readiness endpoint, and an inert inbound iMessage webhook. The feature graph is
implemented and enforced: every file in the repo is accounted for by a node, and the check gates
both `pnpm check` and CI.

Nothing touches a live service yet, because the credentials exist only in the Vercel project.

## The shape of the business, settled

Pre-sell ALTERED Koa Layer 1. A $100 deposit reserves a build slot and locks the price; $399 due at
launch, $499 total. Target launch 2026-11-05, when the six-month program begins and the mechanism
core ships: memory, self-scheduled reach-outs, voice notes, notes import. Refunds are guaranteed
through a process, and the window opens after launch. Discord access is immediate.

The landing page informs and moves people into iMessage, where the sales agent closes. Payments via
Autumn. Publishing via Zernio. Outreach and content run in parallel. The dashboard authenticates
with an emailed code.

The core product stays hand-written by the owner. This repo generates everything around it, and says
so openly, because the generated system is itself the proof.

## What is blocking

- **Environment values.** They are in Vercel but not in this environment. Nothing that touches a
  live service can be built or verified until they are reachable here, either as Cloud Agent secrets
  or by an approved pull.
- **Round 3 answers.** Publishing identity, content approval model, domain, dashboard scope, the
  iMessage operator's first version, and analytics.

## What can proceed without answers

The data model and schema, the sales and lead domain logic, and tests. All are independent of the
open questions and of live credentials, provided they fail loudly when configuration is absent.

## Deploying

Vercel project settings: root directory `apps/web`, framework Next.js. The build runs from the
workspace root through Turborepo, so the install command must run at the root.

The inbound iMessage webhook is `https://<domain>/api/webhooks/sendblue`. Readiness is at
`/api/health`, which outside production names every missing environment variable and in production
reports only a count.

## Reference material now mined

The notes archive and the `liminal` repo have been read. Findings landed in two places: the concepts
worth adopting are in `feature-graph.md` under "Adopted from Liminal", and ALTERED's data primitives
are drafted in `product-primitives.md` as unconfirmed reference for the copy and sales rounds. The
`liminal` repo itself is an empty scaffold and needs no further attention.

## Open strategic thread

The owner is considering a broader angle: helping detail-obsessed founders achieve intentional app
generation, with the feature graph providing stateful consistency. It is a genuine opportunity and
also a genuine risk to the launch date. The agent's recommendation, pending his answer, is to run it
as the content narrative while the offer stays exactly as locked. See Q23 in `open-questions.md`.

The notes strengthen both sides of that. He has circled this angle for months and once considered it
his first high-ticket offer, describing the buyer as a solo founder whose app is too complex and who
is too perfectionist to finish, which is almost exactly the locked demographic. He has also deferred
building it every time, most recently in July, on the grounds that development time is the binding
constraint and memory matters more. Both facts point the same way: run it as narrative now, keep the
delivery promise where it is.

## Useful facts verified this session

Registry as of 2026-08-14: `effect` rc 4.0.0-rc.109, `ai` 7.0.63, `next` 16.3.0, `drizzle-orm` rc
1.0.0-rc.4, `typescript` 7.0.2 available but 5.9.3 pinned, `@biomejs/biome` 2.5.8, `turbo` 2.10.10.

Effect v4 API notes, verified against the installed source rather than recalled: services live in
`Context` and are created with `Context.Service<Self, Shape>()("Key")`. `Config.literals` takes the
array first and the name second. `Config.redacted(name)` accepts an empty string, so secrets are
built as `Config.nonEmptyString(name).pipe(Config.map(Redacted.make))` to stay fail-closed.
`Logger.layer([...])` installs loggers; `Logger.consoleJson` and `Logger.consolePretty()` are the two
in use.

Node 22 provides `path.matchesGlob` and `--experimental-strip-types`, which is how the graph check
runs without a build step or a glob dependency.
