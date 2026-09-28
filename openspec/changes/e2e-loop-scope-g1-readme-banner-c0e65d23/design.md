# Design

## Context

`README.md` ships today as a five-line placeholder: a `# orca-companion`
title, a one-sentence description, a blank line, an italicised note
about future sections, and a trailing newline. Its companion
`NOTES.md` already documents scope, intent, and conventions under fixed
level-2 headings and cross-links back to `README.md`. The proposed
change adds a single Markdown blockquote banner at the top of
`README.md` so that the user-facing file mirrors the developer-facing
file's discoverability loop, without duplicating its prose. See
`proposal.md` — *Why* for the motivation, and the capability
`readme-banner` under
`openspec/changes/.../specs/readme-banner/spec.md` for the requirements.

## Goals / Non-Goals

**Goals:**

- Land a Markdown blockquote banner at the top of `README.md` that
  satisfies every ADDED requirement of the `readme-banner` capability.
- Keep the implementation surface minimal: one blockquote added to an
  existing file, no edits to any other file in the repository.
- Make the banner's placement stable (first non-empty content) and its
  link target stable (`NOTES.md`) so future tooling can lint for both.

**Non-Goals:**

- Restructuring `README.md` beyond inserting the banner. The existing
  `# orca-companion` title, the description, and the italicised
  placeholder note all remain untouched in their current order.
- Adding badges, shields, HTML markup, or images. The banner is plain
  Markdown blockquote text plus a single relative link; that keeps it
  parseable by every Markdown renderer the project already supports.
- Touching `NOTES.md` or `orca-companion.json`. The Scope Envelope
  permits only `README.md`, and no requirement in `readme-banner` calls
  for edits elsewhere.

## Decisions

- **Blockquote, not HTML or ASCII art.** The banner uses the Markdown
  blockquote syntax (`> ...`) with continuation lines for visual flow.
  This trades maximal visual flourish for renderer portability: every
  Markdown tool used in the project ecosystem — GitHub, `grip`, plain
  text `cat` — renders a blockquote the same way, so the banner stays
  discoverable regardless of viewing medium.
- **Banner above the title.** The blockquote is placed above the
  existing `# orca-companion` heading so it is the first thing a
  reader sees when they open `README.md` after cloning. This matches
  the convention used by many OSS "status" banners and keeps the
  project's canonical title visually anchored at the top of the
  document body.
  *Alternatives considered*: (a) putting the banner below the title —
  rejected because a status callout has more impact above the title
  and because the spec pins "first non-empty content"; (b) replacing
  the title with the banner — rejected because the title is the
  canonical heading downstream tooling indexes.
- **Cross-link to `NOTES.md`, not duplicate.** The banner includes a
  Markdown link whose target is `NOTES.md`; it never reproduces the
  scope/intent/conventions prose byte-for-byte. This mirrors the
  cross-link already carried by `NOTES.md` back to `README.md` and
  honours the `Conventions` rule in `NOTES.md` that the two files
  must remain complementary rather than mirror one another.
  *Alternatives considered*: inlining the scope/intent/conventions
  summaries — rejected as a duplicate-prose risk and as unnecessary
  given the link target.
- **No new tooling, no new files.** The whole change is one
  blockquote inserted into `README.md` because the Scope Envelope
  (`["README.md"]`) forbids touching anything else. There is no
  template, schema bump, or build hook.
  *Alternatives considered*: extracting the banner to a `partials/`
  include — rejected because `README.md` is a flat Markdown file with
  no include mechanism today, and the surface area would exceed the
  Scope Envelope.

## Risks / Trade-offs

- **Banner wording may tempt editors to over-expand.** Risk: future
  changes keep appending to the banner until it eats the title and
  description. Mitigation: the spec pins the banner's position as
  "first non-empty content above the `# orca-companion` title," so any
  edit that buries the title under banner lines becomes a spec
  violation rather than a stylistic concern.
- **Single file, single link target.** Risk: if `NOTES.md` is ever
  renamed, the banner link silently breaks. Mitigation: the spec pins
  the link target as the literal relative string `NOTES.md` and the
  acceptance command greps for that target, so a rename forces a
  coordinated change rather than a silent drift.
- **Blockquote readability on narrow viewports.** Risk: long
  blockquote lines wrap awkwardly on mobile GitHub. Mitigation: the
  banner is kept to two short lines, each well under the common 80–100
  character soft-wrap threshold.

## Migration Plan

Not applicable. There is no prior banner to migrate from and no
existing consumer that depends on `README.md` having no top-of-file
callout. The change is purely additive: once the banner lands, later
changes may extend it (for example, adding a status badge) only if their
own proposals and Scope Envelopes permit the additional surface.

## Open Questions

None. All decisions are pinned by the capability requirements and the
Scope Envelope.
