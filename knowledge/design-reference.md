# Design reference

What the owner has actually said he likes, drawn from roughly 1,500 notes, ranked by how strongly he
endorsed it. This exists so design decisions are grounded in his stated taste rather than in an
agent's guess, and so the archive does not have to be mined again.

Under D012 none of this is binding until he confirms it. The gaps at the end are the things he has
never stated, which are therefore open questions rather than assumptions to make quietly.

## The single clearest specification he wrote himself

On Pierre Computer Company, 2026-03-02:

> "We should have it very minimalistic like the company, the website for Pierre's computer company.
> Where it's very minimalistic, a dark gray background with basically just a font and some padding.
> Even stuff like forms doesn't need special attributes or anything... the idea is to keep it so
> minimal that we reduce the overhead in which we need to make it perfect."

That last clause is the reasoning behind the whole aesthetic: minimalism is chosen partly because it
lowers the cost of being perfect. He also separately admired the naming: "come up with a parent
company name as sleek as Pierre Computer Company, Inc."

Note that he wrote "Pierre's computer company" rather than the domain, so the `pierre.computer` URL
came from conversation, not the notes. Both point at the same site.

## Inspiration, ranked by endorsement strength

**Strongest, tied directly to ALTERED's own identity:**

- `sutera.ch` - "this one's insaneeee (it switches realities)"
- `zernio.com` - "amazingly simple monospaced website"
- `langfuse.com` - "this site is beautiful and should be inspo for altered"
- `asciistudio.space/showcase` - "huge inspo for altered", grouped with `pixel-perfect.space` and
  Vercel's pixel font
- `tinkerer.club` - "this website is insane, the design, marketing, etc"
- `code.storage` - "woah inspiration"
- `paper.pro/dev` - "this article is a masterclass"
- `sonner.emilkowal.ski` - "study this shit (web design)"
- `polar.sh` - "amazingly simple beautiful website inspiration"
- `rocket.new` - "marketing site is gold for copy"
- `factory.ai` and `ampcode.com` - "incredible branding and style"

**Strong but narrower:** `braintrust.dev` ("beautifully balanced"), `supermemory.ai` (concise
marketing page), `pullfrog.com` (serif reference), `v0.app` brutalist SaaS template,
`linqapp.com` ("great balanced web inspo"), `ped.ro/shooting`, `shumer.dev` (minimalist blog),
`soloterm.com` (terminal aesthetic), and Midday for product UI specifically.

**Moderate mentions:** terminal.shop, eden.so, chanhdai.com, coreline.vc, pinecone.io, letta.com,
liquid.ai, alignerr.com, invisibletech.ai, fluidfunctionalism.com, app.messages.dev, alpic.ai,
clarissemichard.com.

The pattern across the top tier is consistent: dark, minimal, monospaced, concise, with craft in the
details rather than in decoration. Not glossy, not illustration-heavy, not marketing-heavy.

## Typography

- **Berkeley Mono v2** is the only typeface he has stated an intent to buy, more than once, and he
  paired that intent with acquiring a `.computer` domain. It is the primary face.
- **Hoefler Text** is his named serif, reserved for literary moments: an ad headline over an iMessage
  background in the style of Poke's advertising, verses rendered as images, a quote on the back of a
  hoodie. Not for body text.
- **PX Grotesk** appears exactly once, in a list of fonts installed on a Mac in 2024. He has never
  argued for it or compared it to Berkeley Mono, and PX Grotesk Mono is never mentioned at all. Its
  status is weaker than the conversation implied.
- **Geist and Geist Mono** are installed but secondary. **Saans** is never mentioned.
- He has a cross-project note to default to `text-rendering: optimizeLegibility`, with the caveat
  "research first". Not adopted: the property has real performance and rendering pitfalls, so it
  needs a deliberate decision rather than a default.

## Visual system

**Dark first.** The Pierre specification says dark gray background. Monochrome is the repeated
preference, with a colour toggle as the exception rather than the default. Light mode appears once,
in a personal note about mirrors and outgoingness, not about the product.

**Brutalist means, concretely:** monochromatic hero, ASCII and dithering, CRT or LCD pixel
distortion, black and white height maps. He has asked for these specific effects more than once. He
also noted "change palette to oklab".

**Layout rules he has stated:**

- Centre the core component and build outward, rather than laying out a document from top to bottom.
  Written in January 2026 about the app and chat interface.
- A hero of text on the left with a terminal interface on the right, vertically centred.
- Navigation padded 1.5 times as much horizontally as vertically, from the Liminal notes.
- Minimal padding generally: "basically just a font and some padding".

**Colour.** There is no locked accent. There is a semantic map from 2026-05-06: human is orange or
yellow, controlled is blue or black, knowledge is purple, orchestration is white, black or green,
agents are red, physical is brown or green, digital is blue. When colour is used at all, he has
suggested taking values from the Cursor theme.

## Conversion beliefs

- **Anti-perfectionism on copy**, June 2026: "I need to have the headline right, or if one word is
  wrong in the headline, nothing will sell... all of that literally needs to go out the window."
  This is recent and directly supports shipping a draft page and iterating.
- **Massive promise plus proof, not a feature dump.** From the pre-sale notes: "a confident price
  point with a massive promise and an inevitable explanation. Bank on them self-answering questions,
  novelty factor, and micro-demo proof."
- **He deprioritises web UI work**: "for me, web UI is the most time-intensive endeavour." He has
  suggested generating a seventy-five percent accurate page and refining it. Which is exactly what
  this repo is for.
- **A VSL funnel** appears in April 2026 notes: video, then a call, then a high ticket close. This is
  superseded by D032 and D042, which close in iMessage with no call. A video could still live on the
  page later; the call cannot come back without re-opening a locked decision.

## Conflicts with what is currently built

Recorded honestly rather than quietly resolved.

1. **The landing page is a top-to-bottom document**, which the January 2026 note argues against. That
   note was about the app and chat interface, and every marketing site he ranked highest is a
   conventional scrolling page, so the rule most likely applies to product UI. Worth confirming.
2. **The page currently follows the system colour scheme** through `light-dark()`, which is what
   Pierre's own site does. His stated preference is dark first. Open question.
3. **Zero border radius was asserted as a brutalist default** when the graph was written. He has
   never stated a radius rule anywhere. That was an agent assumption and is now an open question.
4. **The accent is a warm amber**, which happens to land on "human" in his semantic map. That is a
   defensible rationale given the ethos, but it was arrived at by taste, not by his map.
5. **No ASCII, dither, or CRT treatment exists yet.** These are among his most repeated visual
   requests and the hero is currently plain text.

## Gaps he has never stated

Dark-first versus system preference for this site. Any border radius rule. A single accent value.
Berkeley Mono versus PX Grotesk, which he has never compared. Whether the marketing page should
follow the centre-narrow rule or the conventional scroll of the sites he admires.
