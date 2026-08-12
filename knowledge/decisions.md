# Decision ledger

Binding decisions, newest section last. Each entry records the verdict, the reason, and what it
would cost to re-open, so that no future session re-litigates a settled question from scratch.

A decision is only in this file once the owner has stated it. Agent recommendations that have not
been accepted live in `open-questions.md`.

---

## Round 0 - founding directives (2026-08-12)

Stated by the owner when commissioning this repo. These are operating-level, not product-level.

### D001 - Development happens in Cursor, not iMessage

**Verdict:** All development, code, and architecture conversation happens in Cursor cloud agent
chats. There is no development iMessage integration.

**Why:** The previous attempt routed build work through iMessage, which produced a fragile bridge
and pushed dev conversation into a channel unsuited to it.

**Re-open cost:** High. The iMessage surface design inherits from this.

### D002 - iMessage is a human-facing agent only

**Verdict:** iMessage exists so the system can reach the owner and so the owner can reach it. Scope:
notifications, small user-land decisions and questions, and longer voice notes that feed the
knowledge base. Knowledge captured this way may inform development, but development conversation
does not happen there.

**Re-open cost:** Medium.

### D003 - External writes are default deny

**Verdict:** No writes to external APIs, services, or accounts without explicit owner approval per
operation. Reads are fine. See `constraints.md`.

**Why:** The previous attempt auto-created Vercel projects that the owner had to clean up manually.
Owner assets are protected by staying away from them, not by careful use.

**Re-open cost:** Never re-opened wholesale. Individual operations get approved one at a time.

### D004 - GitHub writes are scoped to this repo

**Verdict:** Git and GitHub writes only within `usealtered/altered-generated-opus`.

**Re-open cost:** High.

### D005 - No ambiguity, no assumptions

**Verdict:** Agents do not decide on stack, code structure and design, scope, timeframe, feature
depth, roadmap, offer and funnel structure, user-facing copy, or visual design. Those are asked in
rounds in the Cursor chat, with multiple choice and a recommendation, ordered so that no answer
invalidates an earlier one. Minor local implementation choices are the agent's.

**Re-open cost:** High. This is the core working agreement.

### D006 - Mobile-first everywhere

**Verdict:** Every human surface is designed for a phone first: the Cursor chat updates, iMessage
output, and above all the secure web dashboard for drafts, scheduled posts, lead flow, and metrics.
PWA affordances are worth adding where they earn their place, so the dashboard can live on the
owner's home screen.

**Re-open cost:** High.

### D007 - Cleanliness, minimalism, composability

**Verdict:** Code quality, runtime safety, and output quality are the top priority, above speed.
Take the simplest solution that works until a real edge forces more. No invented hacks, no one-off
custom implementations that duplicate a well-known library. Quality, refactor, reliability, and
observability passes at the end of every turn, plus a whole-branch pass before merge.

**Why:** Without a strong source of truth in code, the product, the dev process, the marketing, and
reliability all degrade together.

**Re-open cost:** Never.

### D008 - The owner does not touch git, PRs, or code

**Verdict:** Agents own the entire git lifecycle including merging their own pull requests.

**Re-open cost:** Low, but it changes the reporting protocol.

### D009 - Dynamic over hard-coded

**Verdict:** Values that a human might reasonably want to change belong in a database, a settings
store, or a CMS - not in source. Hard-code only what is structural.

**Re-open cost:** Low.

### D010 - Presale / reservation approach is retained

**Verdict:** The reservation or presale motion stays as the commercial approach, but its shape,
price, and mechanics are to be re-optimised rather than copied from the previous attempt.

**Re-open cost:** Medium. Owner has asked for optimisation, not preservation.

### D011 - Prepare for extractable packages, do not build them yet

**Verdict:** Module boundaries should be drawn so that vetted packages could later be published and
installed privately into the hand-written `altered` repo. No packages are extracted or published
now.

**Re-open cost:** Low.

### D012 - Nothing from the prior repos is treated as truth

**Verdict:** `altered` and `altered-generated` are "before" references. Every offer component,
phrase, product claim, and operational assumption is re-confirmed top-down in this repo.

**Re-open cost:** Never.

### D013 - Stop and ask on blocking constraints

**Verdict:** On a mostly-blocking constraint such as missing access to a resource or repository,
stop and ask. Continue only on genuinely independent work.

**Re-open cost:** Never.

### D014 - Effect.ts is permitted, popular libraries are preferred at the edges

**Verdict:** Effect may be used for dependency injection, error tracking, and logging where the
agent is confident in it. Where a more popular library is the better-understood choice, wrap it
rather than replacing it - the stated example is using the AI SDK over `effect/ai`.

**Status:** Permitted, not yet adopted. Adoption is an open question, see `open-questions.md`.

**Re-open cost:** High once code exists.
