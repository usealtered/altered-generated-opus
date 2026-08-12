# Current state

Updated 2026-08-12. Read this first, then `decisions.md`, `open-questions.md`, `feature-graph.md`,
`prior-art.md`.

## Where the project stands

Documentation and contracts only. No stack scaffolded, no code written, no infrastructure. The
commercial strategy and the operating protocol are now settled; the money, channel, and surface
decisions are not.

Completed:

- Audited both reference repositories. Findings in `prior-art.md`.
- Wrote the operating contract in `AGENTS.md`, including the hard wall, the security pass, the
  third-party doctrine, and the feature graph procedure.
- Recorded round 0 founding directives and all fifteen round 1 answers in `decisions.md`
  (D001 to D039).
- Specified the feature graph in `feature-graph.md`.
- Published the environment contract as `.env.example`.
- Asked round 2 in the Cursor chat, mirrored in `open-questions.md`.

## The shape of the business, settled

Pre-sell ALTERED Koa Layer 1. A $100 deposit reserves a build slot and locks the price; $399 is due
at launch, $499 total. Target launch 2026-11-05, when the six-month program begins and the first
slice ships. Refunds are guaranteed but run through a process, and the window opens after launch.
Buyers get Discord access immediately. The core product is hand-written by the owner; this repo
generates everything around it. Revenue target is at least $3,000 this month.

## What is blocking

- **Round 2 answers.** Payment provider, publishing route, and dashboard auth each add variables to
  `.env.example`, so the credential handover is not complete until they are answered.
- **Credentials.** Nothing live can be built or verified. Only `VERCEL_TOKEN` is usable, and only
  for reads. The `SHARED_STORAGE_DATABASE_URL` in the environment belongs to the parent project, has
  been rolled, and should be removed from this project's secrets.

## What can proceed without answers

Repository scaffolding and the feature graph implementation, once the owner has had a chance to
object to the structural choices below. Both are independent of every open question.

## Structural choices taken under D031

Q13 gave the agent full authority over structure and composition. These are stated plainly so the
owner can veto any of them:

- **pnpm workspaces with Turborepo.** One deployable application, feature packages beside it.
- **A single Next.js 16 application** serving the landing page, the admin dashboard, and the API
  routes including webhooks. One deployment, one set of environment variables, far less operational
  surface than splitting an API out. Revisit only if a genuine long-running workload appears.
- **Effect v4 as the backbone**, per D032, with AI SDK v7, Drizzle, and the auth library wrapped at
  the edges.
- **Neon Postgres with Drizzle**, Upstash Redis for chat state and locks, Upstash QStash for
  scheduling.

## Useful facts verified this session

Registry versions as of 2026-08-12: `effect` rc 4.0.0-rc.108 (stable line is 3.22.1), `ai` 7.0.63,
`next` 16.3.0, `drizzle-orm` rc 1.0.0-rc.4 (stable line 0.45.2), `hono` 4.13.1, `better-auth`
1.6.27, `arktype` 2.2.3, `zod` 4.4.3.

Image toolchain: Node 22.14.0, pnpm 10.33.3, git 2.43.0.

The complete GTM master chat from the parent repo is committed at
`.context/strategy-generated/sources/gtm-master-chat.jsonl` in `usealtered/altered`. It is 316K of
JSONL and is the richest available record of how the offer was reasoned out. Under D012 nothing in
it is treated as true without re-confirmation, but it is the best source for the owner's voice and
for the reasoning behind retired options.

The Apple Notes repository is not reachable. `gh` sees only four repos under `usealtered` and
eighteen under `inducingchaos`, none of which is a notes export. It is presumably private.
