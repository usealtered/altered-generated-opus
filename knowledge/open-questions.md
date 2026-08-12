# Open questions

Questions are asked in the Cursor chat, in dependency order, never as a file the owner has to read.
This register exists only so a restarted session knows what is outstanding and what was answered.

Status values: `asked`, `answered`, `deferred`. Answered questions move to `decisions.md` and are
struck from the active list here.

---

## Round 1 - foundation (asked 2026-08-12, awaiting answers)

Ordered so that no answer can invalidate an earlier one: what we sell, then where it is built, then
how we work, then the one technical choice with the longest lead time.

### Block A - what we sell

| # | Question | Recommendation | Status |
| --- | --- | --- | --- |
| Q1 | What exists at the moment of sale | Immediate founding access to what is real today, plus a dated delivery guarantee with automatic refund | asked |
| Q2 | Who we sell to | Keep detail-obsessed technical founders, add an explicit disqualification list | asked |
| Q3 | Lead promise | Outcome-led (shipping), memory as the mechanism rather than the headline | asked |
| Q4 | Brand surface | Koa as the product brand, ALTERED as the company, drop "Layer 1" from public copy | asked |
| Q5 | Price and offer shape | $100 fully-credited deposit toward a $499 program | asked |
| Q6 | Risk reversal | Fully refundable until delivery | asked |
| Q7 | Delivery commitment | Milestone-based with one hard dated milestone tied to the refund guarantee | asked |

### Block B - boundary

| # | Question | Recommendation | Status |
| --- | --- | --- | --- |
| Q8 | What this repo owns | Go-to-market only, with a clean seam to the product core, unless Q1 requires a sellable slice here | asked |
| Q9 | Infrastructure isolation from `altered` | Fully isolated: own database, own iMessage line, own subdomain | asked |

### Block C - operating protocol

| # | Question | Recommendation | Status |
| --- | --- | --- | --- |
| Q10 | Guardrail list and runtime-write approval model | Confirm `constraints.md` as written; per-integration approval plus default-off kill switch | asked |
| Q11 | Pull request trail | Pull request per change, self-merged once green | asked |
| Q12 | Question round size | Six to eight per round after this one | asked |
| Q13 | Inherit `altered` code conventions | Inherit copy, aesthetic and formatting; choose code structure fresh | asked |

### Block D - long-lead technical

| # | Question | Recommendation | Status |
| --- | --- | --- | --- |
| Q14 | Adopt Effect v4 as the backbone | Yes for services, errors, logging and config; wrap AI SDK, Drizzle and auth at the edges | asked |

### Block E - blocking resources

| # | Question | Recommendation | Status |
| --- | --- | --- | --- |
| Q15 | When to provision missing credentials | Just in time, in small batches; first batch is a database and an LLM key | asked |

---

## Planned later rounds

Not yet asked. Listed so the dependency order stays visible.

- **Round 2 - funnel and channels.** Channel priority and sequencing, whether direct messages are in
  the path, the landing page's job and whether price appears on it, payment provider and checkout
  mechanics, sales agent autonomy and escalation threshold, follow-up and nurture policy.
- **Round 3 - systems and surfaces.** Content engine depth and approval model, analytics and
  attribution, ads promotion criteria, dashboard scope and authentication, iMessage notification
  agent scope, scheduling model.
- **Round 4 - technical design.** Repository shape, data model, hosting, testing and CI, observability
  stack, environment and configuration strategy.
- **Round 5 - copy and visual design.** Headline and offer copy, landing page structure, visual
  system, iMessage voice and tone.

---

## Known limitation

The original commissioning chat for the previous repo
(`bc-019fec8e-b595-799e-a563-893350c98cc5`) is not readable from this run's scope. Intent was
reconstructed from the two repositories instead, which is why every claim taken from them is being
re-confirmed rather than assumed.
