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

**Status:** Adopted. See D033.

**Re-open cost:** High once code exists.

---

## Round 1 - strategy, offer, and operating protocol (2026-08-12)

### D015 - Pre-selling is the strategy, and it is a skill

**Verdict:** We pre-sell. Revenue comes before a shipped product, deliberately.

**Why (the owner's reasoning, preserved because it overturns an earlier position):** speed is the
single biggest leverage point in software - time to money, time to revenue, time to capital. Capital
buys the time to build the real thing and ends the day job. Pre-selling converts lower than selling
a tangible product on a like-for-like basis, but the comparison is not like-for-like once you price
in what early cash unlocks. Pre-selling is a skill, and the skill is available: the constraint is
execution quality, which is what this repo is for.

The earlier position in the parent repo, that pre-selling with nothing is execution incompetence, is
retired. Its real target was incompetent execution, not the pre-sale motion.

**The honest framing we use publicly:** we pre-sell *because* we care about the details. The core is
hand-written rather than generated because a data platform that people trust with their thinking
cannot afford a wrong column name, a missed primitive, or a subtly generic design. We would rather
sell the promise and get it right than ship a generated approximation early.

**Re-open cost:** Very high. Every downstream marketing decision inherits this.

### D016 - The core product is hand-written, and this repo never touches it

**Verdict:** The entire `altered` repo is written by the owner, by hand, 100%. No agent writes core
product code. This repo generates everything else, disclosed as generated.

**Why (preserved in the owner's terms):** ALTERED is infrastructure - a thin layer beneath other
people's products. Its primitives, data models, naming, and backlink semantics have to be uniquely
his, or the platform regresses toward a generic composite of existing tools. Beyond that: knowing
the data model completely prevents losing the vision; hand-writing preserves human authorship in the
product; and it is the part of the work he wants to do. Performance, durability, and logging may use
AI assistance, but every line is reviewed by him.

**Consequence:** no partial product is offered. Nothing ships to buyers until V1 is whole.

**Re-open cost:** Never. Stated as final.

### D017 - Q1: what the deposit buys

**Verdict:** A deposit reserves a build slot, or customisation slot, in the early access program and
locks the advertised price. There is a published launch date. If we miss it, the deposit is
refunded, though not automatically - we may first offer an extension if something dramatic happens.

On the launch date the buyer receives the first slice only: the Koa chat that helps them align, to a
specification we define. No core code access at deposit time.

Delivered immediately on deposit: access to a Discord community where the product is discussed
pre-launch, plus any bonuses we create.

### D018 - Q2: who we sell to

**Verdict:** Detail-obsessed technical founders, with an explicit disqualification list.

**Disqualify:** no budget; blocked by procrastination we cannot solve; a skill gap we cannot close;
no direction at all. **Qualify:** they have a sense of what they want and real problems to solve.

### D019 - Q3: the promise leads with outcome

**Verdict:** Outcome-led. Memory and self-scheduling are the mechanism, never the headline.

**The outcome chain:** get crystal clear on what your product actually is, consolidate a thousand
scattered thoughts into the few that matter, build product and marketing around those, ship, hold
marketing steady, and let revenue follow. We never promise revenue.

**The pain we name:** starting down a path without being able to finish or clarify it, switching
ships, and never focusing long enough to make the value proposition clear.

### D020 - Q4: the name

**Verdict:** **ALTERED Koa Layer 1**. ALTERED is the company, Koa is the product, Layer 1 is the
program. Digit, not the word. Followed by a short tagline describing what the program is and what
Koa delivers.

**Why Layer 1 survives:** the audience is technical and values aesthetics, control, and refinement.
Cold traffic hitting it with no context will not parse it, so the landing page defines it
immediately, along the lines of: Layer 1 is the first wave of user testing ALTERED will undergo, and
its members shape the platform's direction permanently. Exact copy is a later round.

Domain: `altered.computer`.

### D021 - Q5: price

**Verdict:** $100 deposit, $499 total, $399 due at launch. **No additional discount.** Total stays
under $500 so it remains closable inside a chat thread without a call.

**Why no discount:** the deposit's job is commitment, not price reduction. "Credited toward" already
delivers the feeling of value; cutting the total to $399 softens the anchor, invites price
negotiation, and gives away roughly $100 of margin per sale that is better spent on paid
amplification. The stronger lever is what the deposit unlocks - the build slot in D017 - not a
smaller number.

### D022 - Q5a: proof is staged, not fabricated

**Verdict:** Proof assets are recreations of outcomes that genuinely happened in the owner's own Koa
usage, restaged for clarity and stripped of personal detail. Constructed iMessage screenshots are
acceptable and normal for social. The events are real; the screenshots are reconstructions.

**Constraint:** we never stage an outcome that did not happen.

### D023 - Q6: conditional refund guarantee

**Verdict:** A full refund is guaranteed, but it runs through a process rather than a one-click
request. The buyer states why they are unsatisfied and gives feedback. The refund is then honoured
unconditionally.

**Timing:** the refund window opens after the launch date and after they have used the product. The
deposit funds development until then.

**Why:** an instantly refundable deposit is a real cash risk once we reinvest a share of deposits
into paid acquisition. A single bad public moment could force refunds out of money already spent.
The process keeps the marketing claim strong while protecting solvency.

**Delegated:** exact wording is the agent's, subject to copy review.

### D024 - Q7: dated cohort start

**Verdict:** A dated launch, targeting **2026-11-05**, roughly twelve weeks out. The six-month
program begins on that date. Nothing is released before it.

We publish exactly what buyers receive on that date. Vague early access kills anticipation;
specific promises with a date sustain it.

**Owner confirms the final date** once sales are consistent and profitable. If we need to stretch
past it, we refund or offer a discount.

**Standing constraint:** every promise attached to that date must be something the owner can
hand-write within the window. No agent may add to the launch promise list.

### D025 - Q8: what this repo owns

**Verdict:** Everything go-to-market, and everything we want generated and built fast. Docs and the
landing page live here for now.

**Excluded, permanently:** the core infrastructure and architecture layer - ALTERED's core data
types, the shipping applications, and the official API surface.

### D026 - Q9: hard wall between generated and hand-written

**Verdict:** Total separation. Separate database, separate iMessage line, separate everything.

**The only two sanctioned seams:** packages generated here that the owner chooses to install into
the core repo, and read-only reads of core product data once it is live. Neither exists yet.

### D027 - Q10: guardrails confirmed as written

**Verdict:** `constraints.md` is confirmed. Default deny, per-operation approval, session writes and
runtime writes approved separately, kill switches default off.

### D028 - Q10a: never ask for review in a file

**Verdict:** Questions and review requests go in the chat. The owner reads on a phone and cannot
practically open repo files. A long, genuinely file-shaped artefact such as the agent instructions
may be committed, but the decisions inside it are still surfaced as chat questions.

### D029 - Q11: branches, then merge to main by hand

**Verdict:** Branch per logical change for visibility, then merge to `main` directly using git. Do
not use the pull request tooling - it requires owner approval, which defeats the purpose. Pull
requests are optional and mostly unnecessary since the owner does not review code.

### D030 - Q12: rounds of six to eight questions

**Verdict:** Smaller rounds, each shaped by the previous round's answers.

### D031 - Q13: fresh everything

**Verdict:** No conventions inherited from the parent repo. Code style, formatting, structure, and
composition are entirely the agent's own choice, subject only to the quality bar: clean, composable,
safe, durable, readable.

**Why:** the two codebases never touch except through compiled package installs, so shared
formatting buys nothing. Agents should write in the style they execute best in.

### D032 - Q14: Effect v4 adopted

**Verdict:** Effect v4 is the backbone: services, dependency injection, the error channel, logging,
tracing, and configuration. Popular libraries are wrapped rather than replaced at the edges - AI SDK
v7, Drizzle, and the auth layer.

**Version policy:** pin exact versions, upgrade deliberately later. A moving release candidate is
acceptable under a lock.

**Learning:** clone `Effect-TS/effect-smol` and search the source alongside the docs. Do not spend a
turn studying before starting; the owner considers it proven in production.

### D033 - Q15: credential handover

**Verdict:** The agent publishes the exact environment variable template in chat. The owner fills it
and provides the values. He will also provide a Cursor API key and a GitHub token with broader
scope.

### D034 - Residual resources from the previous project may be wiped

**Verdict:** For any credential handed over, the agent has standing approval to perform a first wipe
where the contents are clearly residual from the old `altered-generated` project. Do not port or
migrate old data. The owner will flag anything worth keeping before handover.

**Boundary:** this approval covers the first wipe of handed-over resources only. It is not general
permission to create, delete, or modify anything else.

### D035 - Chat SDK concurrency: burst mode, no custom machinery

**Verdict:** Set the Chat SDK to burst mode, which is closest to the behaviour we want, and build
nothing custom on top of it.

**Standing design intent for when it is not enough:** proper abort controllers, checkpointed state
so an aborted turn rolls back cleanly and resumes, and reliance on the SDK's own locks and queues so
a locked thread holds later messages until the in-flight turn completes. Any move beyond
configuration is a chat conversation first.

**Operational workaround in the meantime:** space messages out rather than building a fix. This is
not revenue-critical.

### D036 - The iMessage agent is the top-level operator

**Verdict:** Koa on iMessage is the owner's assistant and co-operator. It orchestrates, stores
human-level knowledge, and knows what is happening across the business.

**In scope:** notifications, small decisions and questions, voice notes into the knowledge base,
reporting on repo and development state by relaying to and from coding agents, and eventually
user-land admin commands over lead generation and sales.

**Out of scope:** being a development tool. It relays and reports; it is not designed to drive or
fuel development, even though that is a possible side effect.

**Implementation implication:** it needs a channel to the coding agents, likely Cursor webhooks or
the Cloud Agents API, so it can report which tasks are running and when they finish. Design is a
later round.

### D037 - The feature graph is required

**Verdict:** The repo maintains a feature-level mirror of itself. See `knowledge/feature-graph.md`
for the model and `AGENTS.md` for the every-turn procedure. Kept deliberately minimal.

### D038 - Security is an explicit, itemised pass every turn

**Verdict:** Security is checked point by point at the end of every turn that touched code, per the
checklist in `AGENTS.md`. Environment variables, endpoints, cross-party data access, and admin tool
gating each get their own explicit check.

**Why:** like a human, an agent misses what it does not look at directly. The two fail-open defaults
in the previous repo were exactly this failure.

### D039 - Revenue target

**Verdict:** At least $3,000 in the current month. Cleanliness and stability are the stated route to
it, not a trade against it.

