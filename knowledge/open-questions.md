# Open questions

Questions are asked in the Cursor chat, in dependency order, in rounds of six to eight. Never in a
file. This register exists only so a restarted session knows what is outstanding.

Answered questions move to `decisions.md` and are removed from the active list here.

---

## Round 1 - foundation

**Answered 2026-08-12.** All fifteen questions resolved. See `decisions.md`, entries D015 to D039.

---

## Round 2 - offer stack, money, and channels (asked 2026-08-12, awaiting answers)

Ordered so that no answer can invalidate an earlier one: what we promise, then how we take money,
then where traffic comes from, then who closes it, then how the owner sees it.

| # | Question | Recommendation | Status |
| --- | --- | --- | --- |
| Q16 | Exactly what is promised for the launch date | The mechanism core only: memory, self-scheduled reach-outs, voice notes, notes import. Nothing that risks the date. | asked |
| Q17 | Payment provider | Stripe directly, for payout speed | asked |
| Q18 | Where the deposit is taken | Price stated openly on the page, iMessage as the primary close, a direct checkout link as the secondary path | asked |
| Q19 | First traffic source and sequencing | Assisted outreach now for cash, content engine built in parallel as the durable channel, paid only on proven posts | asked |
| Q20 | Social publishing route | Reuse the existing posting API if the account is still good, otherwise draft-only until it is worth wiring | asked |
| Q21 | Sales agent autonomy | Autonomous, with hard escalation on product claims, dates, and refunds | asked |
| Q22 | Dashboard authentication | Passkey as primary, an iMessage one-time code as the new-device fallback | asked |

Answers to Q17, Q20, and Q22 complete the pending section of `.env.example`.

---

## Planned later rounds

- **Round 3 - systems and surfaces.** Content engine depth and approval model, analytics and
  attribution, ads promotion criteria, dashboard scope, iMessage operator agent design and its link
  to the coding agents, scheduling model, Discord setup.
- **Round 4 - data and delivery.** Data model for leads and content, environment strategy, testing
  and CI, deployment topology, observability stack.
- **Round 5 - copy and visual design.** Headline and offer copy, the Layer 1 explainer, landing page
  structure, visual system, Koa's voice and tone.

---

## Waiting on the owner

- **Credentials.** The template is published in chat and committed as `.env.example`. Nothing that
  touches a live service can be built or verified until values exist.
- **Cursor API key and a broader GitHub token.** Needed to read prior cloud chats and to find the
  Apple Notes repository.
- **The Apple Notes repository name.** Not visible to the current token and not present under
  `usealtered` or `inducingchaos`. It holds the Liminal notes that inform the feature graph, and the
  foundational thinking on ALTERED's primitives. Likely private.
- **Whether the previous system is still live.** See the warning in `constraints.md`.
- **Final confirmation of the 2026-11-05 launch date**, once sales are consistent.
