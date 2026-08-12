# Prior art: what to inherit and what to avoid

Two reference repositories exist. Neither is authoritative. This file records what is worth keeping
and, more importantly, the specific failures that this rebuild must not repeat.

Audited 2026-08-12 against `usealtered/altered` (hand-written) and `usealtered/altered-generated`
(the previous AI-built attempt, 52 commits over roughly 36 hours).

---

## Part 1 - strategic risks

These are the things most likely to stop this project from succeeding. They are not code problems.

### R1 - Selling a product whose core does not exist

The previous attempt sold a reservation deposit toward a program built on an iMessage agent whose
memory layer was a hardcoded placeholder. The hand-written repo's own settlement ledger had already
rejected exactly this, in the owner's words: pre-selling with nothing is "a form of execution
incompetence". The generated repo overrode that principle and then never took a payment - the
checkout URL was still empty at handoff and the prospect funnel was zero.

**Implication:** the reservation motion is retained by owner decision, but its credibility has to
come from somewhere. Either the buyer gets something real on day one, or the proof comes from a
visible build. This must be settled before any funnel copy is written.

### R2 - Marketing that depends on a product timeline nobody controls

This repo builds the marketing, leads, and sales edge. The product core lives in a separate,
hand-written repo at an early stage. Every promise made here creates a delivery obligation there.
Without an explicit, agreed statement of what is deliverable and when, the funnel will drift into
claims the product cannot honour.

### R3 - Narrow marketing wrapped around a deliberately generalist product

The product is a wide-scope, arbitrary, generalist knowledge system. The marketing positions a
narrow wedge for one audience. That tension is normal and usually correct, but it has to be a
conscious decision, because the sales agent will be asked questions that live outside the wedge and
needs a settled answer for them.

### R4 - Positioning built on a commodity claim

The previous positioning led with memory: remembering everything you have told it. The hand-written
repo's own offer document flags this as reading like "every RAG chatbot's VP claim" and records an
alternate framing centred on progress toward shipping. Leading with a claim the audience has heard
from a dozen tools is a conversion problem, not a copy nitpick.

### R5 - Configuration drift between what is sold and what the system does

The previous repo simultaneously held a $250 daily goal in code, a $250 deposit in one playbook, a
$100 deposit in the locked offer document, a $499 program price, and a $221 price in the parent
repo. Pricing was parsed out of a markdown file with a regular expression at runtime. When the
number that defines the business lives in five places, the business has no single truth.

### R6 - Metrics that measure the operator instead of the market

Funnel metrics counted the owner's own ops conversation as prospect activity, so the dashboard
showed activity where there were no leads at all. It took a migration and an API split to discover
that the real prospect funnel was zero. Any metric that can be contaminated by internal traffic will
be, and it will hide the only fact that matters.

### R7 - Uncontrolled external writes against owner assets

An agent created Vercel projects that were never asked for, linked one to GitHub so that every push
triggered failing deployments, and left the owner to delete them by hand. This is the direct origin
of the default-deny guardrail in `AGENTS.md`.

---

## Part 2 - engineering anti-patterns

Each entry is a real finding with the rule it produces.

### A1 - Fail-open defaults

Two authentication paths in the previous repo grant access when configuration is absent.

Operator authorisation, in `packages/env/src/index.ts`:

```ts
export function isOperatorPhone(phone: string, allowlist: string[]): boolean {
  if (allowlist.length === 0) return true;
```

An unset allowlist makes every stranger who texts the public number a full operator, with tools that
spawn coding agents and read business metrics.

Webhook verification, in `apps/api/src/app.ts`:

```ts
async function verifyQstash(req: Request) {
  const env = getServerEnv();
  if (!env.QSTASH_CURRENT_SIGNING_KEY || !env.QSTASH_NEXT_SIGNING_KEY) {
    return true;
  }
```

Unset signing keys accept every unsigned request.

**Rule:** absence of configuration is a hard failure, never a grant. Validate required configuration
at startup and refuse to serve without it.

### A2 - Silent truncation of human content

`truncateForImessage` appends an ellipsis mid-sentence. It caused a visible bug where the owner
received a clipped first bubble. The fix added `enforceShortStatusBubble` for the status path but
left the clipping helper in place elsewhere: prior conversation history in the sales flow is clipped
at 800 characters, and error messages shown to the operator are clipped at the default cap. Clipping
conversation history is worse than clipping a bubble, because it silently corrupts the context the
model reasons from.

**Rule:** never truncate content a human or a model will read. Split it, paginate it, summarise it
deliberately, or fail loudly. No ellipsis as a length strategy.

### A3 - Reactive concurrency patching instead of one concurrency model

Roughly fifteen consecutive commits fought the same iMessage race conditions: await the webhook,
then do not await it, add a burst debounce, add a per-thread Redis lock, add a status dedupe key,
build a custom coalescing layer of about 355 lines, then delete that layer entirely and "trust the
SDK". The end state works but carries the sediment of every attempt.

**Rule:** decide the concurrency and delivery model once, in writing, before the first handler is
written. If the platform's model is unclear, that is a question to ask, not a thing to discover
through production patches.

### A4 - God files

`packages/chat/src/tools.ts` is 1,340 lines and mixes operator tools, agent spawning, metrics,
posting, and memory. `apps/api/src/app.ts` is 709 lines of routing, auth, and handlers.

**Rule:** group by feature, one concern per module.

### A5 - Fire-and-forget writes on paths that matter

Observability writes were dispatched as `void recordAiEvent(...).catch(() => undefined)`, and there
are bare `catch { /* ignore */ }` blocks. The result is that the system loses exactly the data it
needs at exactly the moment it is under pressure.

**Rule:** no empty catch. No discarded rejection. If a write is genuinely optional, that is a
documented decision with a logged failure, not a silent discard.

### A6 - Duplicated sources of truth

The knowledge directory was copied wholesale into a package's content directory and kept in sync by
hand. Pricing lived in markdown and in code. Phone numbers appeared in code, environment variables,
markdown, and model prompts.

**Rule:** one source per fact. If something needs to be available in two places, it is derived, not
copied.

### A7 - Secrets in URLs

The operations dashboard authenticated with a secret in a query string, which leaks into proxy logs,
browser history, and referrer headers.

**Rule:** real authentication for any surface that shows business data.

### A8 - Reinventing available functionality

A lexical retrieval implementation with manual chunk scoring was written while the schema already
carried an unused embedding column and Postgres full-text search was available. Phone normalisation
was hand-rolled. Approval links used a bespoke unexpiring signature scheme.

**Rule:** use the database's features and the ecosystem's libraries. Hand-rolled security primitives
are the worst case of this.

### A9 - Magic numbers standing in for product decisions

A debounce of 1000ms, an acknowledgement timeout of 2200ms, a 32-token output cap, a founding seat
target of 15, and a daily revenue goal of $25,000 in cents were all literals in source.

**Rule:** operational values belong in configuration; commercial values belong in the settings
store.

### A10 - Debug scripts committed into shipped packages

One-off proof scripts were committed alongside runtime code.

**Rule:** verification artefacts live in a test suite or in the pull request, not in the package.

---

## Part 3 - what is worth inheriting

From the hand-written `altered` repo:

- The settlement ledger format: verdict, reason, rejected alternatives, cost to re-open. It exists
  because the owner's stated failure mode is forgetting why a hard decision was made and
  re-litigating it under pressure. This repo's `decisions.md` follows the same shape.
- The copy discipline: hyphens only, and no claim that does not trace back to a locked decision.
- The aesthetic direction: minimalist brutalism, monochromatic with a natural accent, purposeful
  status colour only.
- The inviolables: no unintended mutation or loss of user data, no missing metric collection on
  funnel-relevant events, no instruction taint that corrupts a conversation. Each is a stop-and-ask,
  not a thing to work around.
- The step-back guardrail: for medium-or-larger problems, consider reframings of the parent
  directive before assuming a conclusion, and prefer built-in library capability over invented
  machinery.

From `altered-generated`, the intent is worth reading and the execution is not. Its knowledge
directory is the most complete record of what the previous attempt was trying to sell. Under D012
none of it is treated as true.
