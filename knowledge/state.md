# Current state

Updated 2026-08-12. Read this first, then `decisions.md`, `open-questions.md`, `prior-art.md`.

## Where the project stands

The repository contains documentation only. No stack has been chosen, no code has been written, and
no infrastructure exists. This is deliberate: under D005 nothing gets built while the decisions that
would shape it are still open.

Completed so far:

- Audited both reference repositories and recorded the findings in `prior-art.md`.
- Wrote the agent operating contract in `AGENTS.md`.
- Recorded the owner's founding directives in `decisions.md` as round 0.
- Recorded the guardrail and resource position in `constraints.md`.
- Asked round 1 of the decision questions in the Cursor chat, mirrored in `open-questions.md`.

## What is blocking

- **Round 1 answers.** Nothing downstream can be built until the product, offer, boundary, and stack
  questions are answered. Do not start scaffolding on assumptions.
- **Credentials.** This project has no database, no LLM key, no messaging provider, no cache, no
  queue, no payment provider, and no domain. See the resource inventory in `constraints.md`. The
  only two secrets present belong to the parent project and are not for use here.

## Next action

If round 1 is unanswered: do not build. Re-ask or wait.

If round 1 is answered: record the answers in `decisions.md`, then move to round 2 as listed in
`open-questions.md`.

## Useful facts verified this session

Package landscape as of 2026-08-12, checked against the registry rather than recalled:

- `effect` - stable 3.22.1, `beta` 4.0.0-beta.107, `rc` 4.0.0-rc.108. Version 4 has reached release
  candidate.
- `ai` (AI SDK) - stable 7.0.63.
- `next` - stable 16.3.0.
- `drizzle-orm` - stable 0.45.2, `rc` 1.0.0-rc.4. Several Effect-integration dist-tags exist.
- `hono` 4.13.1, `better-auth` 1.6.27, `arktype` 2.2.3, `zod` 4.4.3.

Toolchain on the cloud agent image: Node 22.14.0, pnpm 10.33.3, git 2.43.0. The parent repo targets
Node 24 and pnpm 11.8.0, so a version manager or an environment build will be needed if this repo
matches it.

To study Effect v4, clone the source rather than relying on documentation:
`git clone --depth 1 https://github.com/Effect-TS/effect-smol` and read
`https://raw.githubusercontent.com/Effect-TS/effect-smol/refs/heads/main/MIGRATION.md`. Clone outside
the repository tree.
