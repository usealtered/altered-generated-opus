# Product primitives (unconfirmed reference)

**Status: not confirmed.** Under D012 nothing taken from the reference repositories or the owner's
notes is treated as true. This file exists so that the 2,000-note archive does not have to be mined
again, and so the copy and sales-agent rounds have raw material to confirm against. Every claim here
needs the owner's sign-off before it reaches a prospect.

Sourced from the notes archive in `usealtered/altered-no-code-1-week-gtm`, weighted toward the most
recent entries where they conflict with older ones.

## What ALTERED is

A database for your thoughts, with layers on top for organisation, transformation, and use. The
owner's own phrasings: "knowledge systems for the obsessed", and "a relational database for your
thoughts and content, with layers on top for dynamic composition, tooling, functionality". The
shape he keeps returning to is store, transform, use.

The stated ambition is infrastructure rather than an app: a personal context layer that other things
are built on. That is the reason the core is hand-written (D016).

## The primitives

- **Thought** - the atom. Minimum viable shape is an alias plus content. Something with content but
  no alias is a draft.
- **Dataset** - a tag, not a folder. A thought belongs to many datasets, which is what avoids
  duplicating content across use cases. Datasets are broken into the smallest composable words, so a
  thought sits in several narrow datasets rather than one broad one.
- **Attribute** - a schema-validated data point attached to a thought. Dataset schemas define which
  attributes exist and what values they accept.
- **Relation** - typed links between thoughts: parent and child, similar, preceding and subsequent,
  and equivalence. Composition happens through relations rather than duplication.
- **Backlink** - a positional reference into a source document, so a distilled thought points at the
  exact span it came from. Sources include iMessage threads, Apple Notes, Cursor chats, voice notes,
  and chat transcripts.
- **Interface** - a rendering definition that selects thoughts and decides how they are displayed,
  kept separate from storage.
- **Brain** - the scope a thought belongs to, distinguishing a user's own thoughts from system-level
  ones.

## Distillation

The pipeline that turns raw source material into thoughts: split a source into standalone ideas,
rewrite each minimally and precisely, generate keyword tags, then save the thought with its backlink
and its cost and token metrics.

An important nuance for copy: distillation is explicitly *not* the same as clarity. Automatic
distillation indexes and compresses; deciding what matters is the human's job. Overpromising
"clarity, automatically" would misrepresent the mechanism.

## Where Koa sits

Koa is the iMessage surface over this: it captures thoughts, remembers them, and reaches out on its
own schedule. The memory claim rests on structured, queryable thought rows with real references,
rather than on vector similarity alone. That distinction is the honest answer when a prospect says
this sounds like every other retrieval chatbot.

## Liminal

A separate concept in the same family: conceptual version control for code. Instead of versioning
files, you version intent, and code is only permitted where it traces to a declared piece of it. The
owner has described it as "ALTERED but for code" and, at one point, as a candidate first high-ticket
offer for perfectionist developers.

He has repeatedly deferred building it in favour of memory and distillation, and the `liminal` repo
is an empty scaffold. This repo's feature graph is the small, practical expression of the idea. Per
D049 it is not part of any offer until we have used it ourselves.
