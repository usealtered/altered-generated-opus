# Open questions

Questions are asked in the Cursor chat, in dependency order, in rounds of six to eight. Never in a
file.

This register carries the **full text** of every outstanding question, not a summary, so that a
fresh session can correlate answers given later against exactly what was asked. Answered questions
move to `decisions.md` and are removed from here.

---

## Rounds 1 to 3

**Answered.** Round 1 on 2026-08-12 (D015 to D039), round 2 on 2026-08-14 (D040 to D051), round 3 on
2026-08-15 (D052 to D061).

---

## Round 4 - finishing the offer, then volume (asked 2026-08-15)

### Q30 - the posting account

Under D053 marketing volume goes to a dedicated alternate account. Two things are undecided: the
handle, and which platforms it runs on first.

- a) A person-extended handle, in the spirit of `@morehormozi`: the owner's voice, obviously his,
  clearly the overflow channel.
- b) A brand-extended handle in the `alteredcomputer` family.
- c) Both, with the person-extended one leading.

Platforms: X only to start, or X and Instagram together.

**Recommendation:** a, on X only to start. The narrative is first person, so the account should read
as a person. One platform done properly beats two done thinly, and the demographic is on X.

### Q31 - the headline

The draft currently on the page is: **"You already know what to build. You keep un-deciding it."**
with the subhead "Koa is an always-on iMessage agent that holds every decision you have made and the
reasoning behind it, so you stop re-deriving your own conclusions and start shipping."

- a) Keep it.
- b) Lead on the outcome instead: "Ship the thing you keep circling."
- c) Lead on the mechanism: "It remembers every decision you made, and why."
- d) Something else, described.

**Recommendation:** a. It names the failure mode in the reader's own language, and un-deciding is a
word he will recognise as his own behaviour. The outcome then arrives in the subhead, which keeps
the promise outcome-led per D019.

### Q32 - what "start an application" actually means

The call to action currently reads "Start an application", chosen for status and positioning. That
word sets an expectation, and we have to honour it.

- a) It is genuinely an application: the agent qualifies against the disqualification list and can
  decline someone.
- b) It is a framing device: everyone who texts is welcome, and the agent sells.
- c) Different wording that does not imply screening, for example "Text to reserve".

**Recommendation:** a. We already wrote a disqualification list into the offer, so screening is real.
Being able to say no is what makes the seat feel scarce, and it protects the refund rate.

### Q33 - the first proof assets

Under D022, proof is staged reconstruction of things that genuinely happened in the owner's own use
of Koa. Which scenarios get built first, in order?

- a) An alignment save: Koa pulling him back from a shiny-object pivot.
- b) Memory recall: an old voice-noted idea resurfacing to power a present decision.
- c) A consistency directive: self-scheduled reach-outs that would not let something drop.
- d) A clarity session: many scattered thoughts narrowed to a few that a product was built from.

**Recommendation:** d, then a. The clarity session is the outcome the offer actually promises, and
it is the one this whole project is a live example of. The alignment save is the most emotionally
recognisable second.

### Q34 - content pillars and cadence

What do we actually post about, and how often?

- a) Build-in-public: what got shipped, what broke, what the system did this week.
- b) The ethos: human truth first, machines on top, why the core is hand-written.
- c) The pain: pressure pivots, re-deciding, perfectionism against time.
- d) Teardowns and craft: opinions about product, systems, and generated software.

Cadence: daily, five a week, or three a week.

**Recommendation:** c and a as the two main pillars, b as the occasional manifesto post, d
opportunistically. Five a week. Pain posts attract the buyer, build-in-public posts are the proof,
and the ethos posts are what make people follow rather than just read.

### Q35 - funnel stage definitions

Under D058 our database is the source of truth, constructed so internal traffic cannot contaminate
it. I need the definitions locked before writing the schema, because these become the numbers we
optimise against.

- Lead: anyone who sends a first inbound message that is not the owner or an operator.
- Qualified: confirmed to be a technical founder actively building, and not disqualified.
- Reserved: deposit paid.
- Lost: explicit no, or no reply after the follow-up sequence completes.

**Recommendation:** adopt as written, with one addition: every stage transition is stored as an
append-only event with a timestamp and a reason, so the funnel can be recomputed later when the
definitions change, rather than being lost.

### Q36 - Discord

Buyers get Discord access immediately on deposit (D017), so it has to exist before the first sale.

- a) Set it up now, minimal: one channel for the cohort, one for build updates.
- b) Set it up now, structured: several channels by topic.
- c) Wait until the first deposit.

**Recommendation:** a. An empty structured server signals a dead community; two channels with the
builder actually in them signals a small one, which is the truth and is attractive at this stage.
Creating it is the owner's action, since it is an external resource.

---

## Planned later rounds

- **Round 5 - copy and design detail.** Section-by-section copy review, the Layer 1 explainer, proof
  placement, the frequently-asked-questions set built from real objections, and the accent colour.
- **Round 6 - sales conversation.** The qualification script, objection handling, escalation
  triggers, follow-up cadence and timing.

---

## Waiting on the owner

- **Resend credentials**, for dashboard login email.
- **Autumn credentials**, for payments.
- **Zernio credentials**, for publishing.
- **Final confirmation of the 2026-11-05 launch date**, once sales are consistent.
- **Approval to submit the domain for categorisation** with URL-filtering vendors, if we want to
  address the TLS-inspection issue in D061. Outbound write, so it needs explicit approval.
