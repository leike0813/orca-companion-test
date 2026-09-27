# Proposal

## Why

The project's baseline ships only with a one-paragraph `README.md` and an
`orca-companion.json` manifest. A first-time reader can therefore discover
almost nothing about how the repo is organised, what the next planned work
is, or where to look for authoritative information beyond those two files.
A separate top-level `NOTES.md` provides a stable, human-authored "first
read" that complements the placeholder README without bloating it, and
that later changes can keep extending.

## What Changes

- Add a new `NOTES.md` file at the repository root containing a concise
  baseline orientation: project scope, current status, immediate next steps,
  and pointers to other sources of truth (`README.md`, `orca-companion.json`,
  `openspec/`).

## Capabilities

### New Capabilities

- `project-notes`: A top-level `NOTES.md` file that documents the project's
  baseline intent, current status, and orientation for first-time readers.

### Modified Capabilities

None. This change introduces a brand-new capability and does not alter the
behavior described by any existing capability in `openspec/specs/`.

## Impact

- `NOTES.md` — new file at the repository root documenting the project's
  baseline notes, current status, next steps, and pointers to other
  authoritative files. (Only path within the Work Package Scope Envelope;
  no other files are touched by this change.)
