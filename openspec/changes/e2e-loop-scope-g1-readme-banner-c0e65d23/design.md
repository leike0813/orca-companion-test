# Design

## Context

The repository starts from the `e2e39` baseline (commit `968671b`) and currently ships a minimal `README.md` that contains an H1 title, a one-sentence description, and an italic placeholder note signalling that more sections will be added later. There is no existing `readme-banner` capability, no spec that owns the README introduction, and no other file is touched by this change, so the design stays narrow: only the banner block at the top of `README.md` is rewritten.

See `proposal.md` for motivation and `specs/readme-banner/spec.md` for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Produce a banner block at the top of `README.md` that satisfies every requirement in `specs/readme-banner/spec.md`.
- Make the banner self-contained — title, tagline, and status line — so later changes can append H2 sections after the banner without touching it.
- Keep the banner plain CommonMark Markdown with no embedded scripts, images, or badge URLs.

**Non-Goals:**
- Wiring `README.md` into any build, lint, or harness configuration.
- Adding badges, shields, or other externally-hosted status widgets.
- Introducing H2 sections (`## Overview`, `## Installation`, etc.) in this change — those belong to later changes with their own scope envelopes.
- Editing `NOTES.md`, `orca-companion.json`, or any other file outside this change's scope envelope.

## Decisions

- **Banner-only rewrite.** Keep the rest of `README.md` (any future H2 sections) untouched in this change. Alternatives considered: rewriting the whole file (rejected — out of scope and would silently break later changes that depend on the placeholder copy).
- **Italic status banner line.** Render the status line using CommonMark `_..._` italics so it visually matches the legacy placeholder copy and signals "soft" forward-looking content without invoking a blockquote, admonition, or HTML element. Alternatives considered: a blockquote (`> ...`) (rejected — blockquotes usually denote quoted material, not status), a fenced callout (rejected — not portable Markdown), and a badge (rejected — adds external dependencies the spec disallows).
- **No images, no badges.** Keep the banner text-only. Alternatives considered: an SVG logo or shields.io badges (rejected — spec forbids non-text constructs and badges create external dependencies on third-party trackers).
- **Re-express the placeholder in plain prose.** The new status banner line keeps the spirit of the original italic placeholder but is owned by the spec rather than left as ad-hoc copy. Alternatives considered: drop the line entirely (rejected — the spec requires a status banner line that announces the project's stage), or keep the exact legacy sentence (rejected — the legacy wording was a placeholder for unspecified "more sections" and does not need to be preserved verbatim).

## Risks / Trade-offs

- [Status banner line drifts from the actual project stage] → Mitigation: keep the line to a generic "further sections will be added in later changes" statement so it stays accurate regardless of which sections land when.
- [Future changes overwrite the banner] → Mitigation: the banner is owned by the `readme-banner` capability, so any change that wants to alter it must reference this spec, making accidental edits visible.
- [README introduction grows too long] → Mitigation: the spec caps the banner at three constructs (H1, paragraph, italic line), so additions must move below the banner as H2 sections owned by later changes.

## Migration Plan

Not applicable. `README.md` already exists; this change rewrites only its banner block and removes one line of placeholder copy. Nothing else depends on the current banner text, so rollback is simply `git checkout README.md`.

## Open Questions

None. The banner's three constructs are fixed by the spec, the file is fixed at the repository root, and no other file in the Work Package Scope Envelope is touched.
