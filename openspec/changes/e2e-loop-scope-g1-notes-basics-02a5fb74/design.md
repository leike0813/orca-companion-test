# Design

## Context

The repository starts with two tracked files: `README.md` (a placeholder
description of the orca-companion project) and `orca-companion.json` (the
agent-harness manifest). Adding `NOTES.md` does not introduce a new
architectural pattern, external dependency, or data model; the only
artifact produced is a single Markdown file living at the repository
root. See `proposal.md` — *Why* for the motivation, and the capability
`notes-basics` under `openspec/changes/.../specs/notes-basics/spec.md`
for the requirements.

## Goals / Non-Goals

**Goals:**

- Land a single `NOTES.md` file at the repository root that satisfies
  every ADDED requirement of the `notes-basics` capability.
- Keep the implementation surface minimal: one new file, no edits to
  existing files.
- Make the file's heading structure stable so downstream tooling can
  parse it by anchor (`## Scope`, `## Intent`, `## Conventions`).

**Non-Goals:**

- Rewriting or expanding the user-facing `README.md`. Sections such as
  *Installation* and *Usage* are explicitly deferred to later changes,
  per the existing `README.md` prose.
- Introducing CI linting for Markdown content; out of scope for this
  change.
- Hooking `NOTES.md` into `orca-companion.json` or any other manifest;
  the file stands alone.

## Decisions

- **Heading set is fixed, not free-form.** The capability pins
  `## Scope`, `## Intent`, `## Conventions` as the only required
  sections in that order. This trades expressive freedom for a stable
  parse surface that future tooling can rely on.
  *Alternatives considered*: (a) a single free-form `## Notes`
  section — rejected because it gives no anchorable surface; (b) more
  rigid sections such as `## Architecture`, `## Roadmap` — rejected as
  premature for a placeholder-era project.
- **Cross-link to `README.md`, not duplicate.** `NOTES.md` includes a
  Markdown link to `README.md`; it never copies prose byte-for-byte.
  This keeps the user-facing overview authoritative and avoids two
  sources of truth drifting apart.
  *Alternatives considered*: inlining the README content — rejected
  for the duplication reason above and for inviting drift.
- **Single new file.** No scripts, no template directory, no schema
  bump. The whole change is one file because the scope envelope
  (`["NOTES.md"]`) forbids touching anything else.
  *Alternatives considered*: a `docs/notes/` subtree — rejected
  because the Scope Envelope only permits `NOTES.md`, and a single
  root-level file is the simplest stable target.

## Risks / Trade-offs

- **Section wording may tempt editors to over-expand.** Risk: future
  changes keep appending to `NOTES.md` until it duplicates `README.md`.
  Mitigation: the cross-link requirement and the duplicate-prose
  scenario together make duplication a spec violation, not a stylistic
  concern.
- **A single root-level file is visible immediately on clone.** Risk:
  some readers may expect a `docs/` folder and miss `NOTES.md`.
  Mitigation: the cross-link target pinned by the spec points readers
  from `README.md` and back, providing a discoverable loop.

## Migration Plan

Not applicable. There is no prior `NOTES.md` to migrate from, and no
existing consumer that needs to switch formats. The change is purely
additive: once `NOTES.md` lands, later changes may add or split
sections behind their own OpenSpec proposals.

## Open Questions

None. All decisions are pinned by the capability requirements.
