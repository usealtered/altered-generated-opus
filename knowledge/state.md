# Current state

Updated 2026-08-15. Read this first, then `decisions.md`, `open-questions.md`, `feature-graph.md`,
`prior-art.md`, `constraints.md`, `product-primitives.md`.

## Where the project stands

Live at `generated.altered.computer`, deployed from `main`. The application builds, runs, and holds
real environment values. A first landing page exists with a full visual system, and is marked
no-index until the owner approves the copy.

The feature graph is enforced: every file in the repo is accounted for by a node, and the check
gates both `pnpm check` and CI.

## The shape of the business, settled

Pre-sell ALTERED Koa Layer 1. A $100 deposit reserves a build slot and locks the price; $399 due at
launch, $499 total. Target launch 2026-11-05, when the six-month program begins and the mechanism
core ships: memory, self-scheduled reach-outs, voice notes, notes import. Refunds are guaranteed
through a process, and the window opens after launch. Discord access is immediate.

The landing page informs and moves people into a text thread, where the sales agent closes. Payments
via Autumn. Publishing via Zernio, from a dedicated alternate account, with every post approved.
Notifications go to iMessage; approvals and editing happen on the dashboard. Funnel truth lives in
our own database.

Two narratives: the brand ethos is human truth preserved through versioning, attribution, and
aggregation, with machines on top of it and never underneath. The product narrative is never lose
your best thinking again. The core product stays hand-written by the owner; everything around it is
generated and disclosed.

## What is blocking

- **Round 4 answers.** See `open-questions.md`, which carries the full text of each question.
- **Credentials not yet provisioned:** Resend, Autumn, Zernio.
- **Copy approval** before the landing page can be indexed.

## What can proceed without answers

The data model and schema for leads and events, the settings store, and tests. All independent of
the open questions.

## Working notes for a fresh session

- **Always branch from a freshly fetched `origin/main`.** A restarted session can resume with an
  older branch checked out; cutting from it silently reverts merged work. This has happened once.
- **Pull environment values** with the Vercel CLI command in `constraints.md`. The REST API returns
  ciphertext even with `decrypt=true`. The file must live at `apps/web/.env.local`.
- **Run the site locally** with `cd apps/web && pnpm exec next dev`.
- **Next 16 writes its own `AGENTS.md` and `CLAUDE.md`** into the app directory unless
  `agentRules: false` is set in `next.config.ts`. It is set. Do not remove it: a nested instruction
  file would dilute the operating contract.
- **Verify claims about the rendered page with the browser console**, not with screenshots. A
  subagent reported the custom font was not loading; `document.fonts.check` and a glyph-width
  measurement both proved it was. Screenshot-based judgements about typography are unreliable.

## Verified facts

Berkeley Mono Variable: 644 glyphs, fixed pitch, all advances 600 per 1000 units, axes `wght`
100-900, `wdth` 60-100, `slnt` -16-0. Loads and renders as true monospace in the browser.

Registry as of 2026-08-15: `effect` rc 4.0.0-rc.109, `ai` 7.0.63, `next` 16.3.0, `drizzle-orm` rc
1.0.0-rc.4, `@biomejs/biome` 2.5.8, `turbo` 2.10.10. TypeScript pinned at 5.9.3 though 7.0.2 exists.

Effect v4 API notes, verified against the installed source: services live in `Context` via
`Context.Service<Self, Shape>()("Key")`. `Config.literals` takes the array first, the name second.
`Config.redacted(name)` accepts an empty string, so secrets are built as
`Config.nonEmptyString(name).pipe(Config.map(Redacted.make))` to stay fail-closed. `Config.option`
wraps a config so absence is an `Option` rather than a failure. `Logger.layer([...])` installs
loggers.

Node 22 provides `path.matchesGlob` and `--experimental-strip-types`, which is how the graph check
runs with no build step and no glob dependency.
