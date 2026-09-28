# Proposal: Notes Basics

## Why

The repository baseline ships `README.md` (project overview) but no
companion `NOTES.md`. Downstream contributors, follow-on changes, and
e2e-loop validation runs all need a minimal, predictable notes surface
at the repository root so the in-flight state, key decisions, and
open questions of the project are visible without scanning the
OpenSpec change tree.

Without `NOTES.md`, every change has to re-derive project context from
scratch, which makes the e2e-loop harder to validate and harder to
reason about across generations. Establishing a baseline notes file in
this change gives later work packages a stable place to append.

## What Changes

- Add `NOTES.md` at the repository root with a fixed section layout
  (`Current State`, `Decisions`, `Open Questions`).
- Each section MUST use a heading and start with a short placeholder
  paragraph that contributors can replace or extend.
- No other files in this Work Package's scope envelope are added,
  modified, or removed.

## Capabilities

### New Capabilities

- `notes-basics`: The repository SHALL provide a `NOTES.md` file at
  the root with a minimal, predictable section layout for capturing
  current state, key decisions, and open questions.

### Modified Capabilities

None.

## Impact

- `NOTES.md` — new file added at the repository root with the
  baseline section layout.
