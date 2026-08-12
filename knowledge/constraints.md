# Constraints and approvals

The authoritative list of what an agent is allowed to touch. Default is deny. Nothing is added here
without the owner approving it explicitly in the Cursor chat, with the date recorded.

## Approved operations

| Scope | Operation | Approved | Date |
| --- | --- | --- | --- |
| `usealtered/altered-generated-opus` | Full git write: branch, commit, push, PR, self-merge | Yes | 2026-08-12 |
| Any third party | Read-only API calls and documentation fetches | Yes | 2026-08-12 |
| Public package registries | Install dependencies | Yes | 2026-08-12 |

## Explicitly denied until approved

- Vercel: creating or modifying projects, deployments, domains, or environment variables. A
  `VERCEL_TOKEN` is present in the environment; it is read-only by policy.
- GitHub: any write outside this repo. Includes `usealtered/altered` and
  `usealtered/altered-generated`, which are reference material only.
- Creating secrets, API keys, service accounts, or credentials of any kind.
- Provisioning infrastructure: databases, Redis, queues, buckets, domains, phone numbers.
- Any outbound message, post, DM, or email to a real recipient.
- Any payment or charge.
- Cursor Cloud Agents API writes: spawning agents, creating runs.

## Resource inventory

What this project actually has access to right now. Verified 2026-08-12.

| Resource | Status | Notes |
| --- | --- | --- |
| `SHARED_STORAGE_DATABASE_URL` | Present, credentials rejected | Belongs to the `altered` experimental tier, not this project. Password was rolled after a past leak incident. Not needed here. |
| `VERCEL_TOKEN` | Present | Read-only by policy. |
| Database for this project | **Missing** | |
| LLM provider key | **Missing** | |
| iMessage provider (Sendblue or equivalent) | **Missing** | |
| Redis / KV | **Missing** | |
| Queue / scheduler | **Missing** | |
| Payment provider | **Missing** | |
| Social publishing API | **Missing** | |
| Analytics | **Missing** | |
| Domain for this project | **Missing** | |

Nothing that runs against a live service can be built or verified until the relevant credential is
provisioned by the owner. Pure logic, schema, and interface work can proceed without them, and
should be written so that a missing credential fails loudly at startup rather than at first use.

## Reference repositories

Read-only. Cloned on demand, never vendored into this repo.

- `usealtered/altered` - the hand-written product core. Closest thing to a source of truth for what
  the product is. Its conventions are a reference, not an inheritance.
- `usealtered/altered-generated` - the previous, lower-quality attempt at this project. Useful only
  as a record of intent and as a catalogue of mistakes. See `prior-art.md`.

Neither repo's contents are authoritative. Every claim taken from them must be re-confirmed with the
owner before it ships.
