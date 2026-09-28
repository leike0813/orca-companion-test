# orca-companion notes

Project-level notes for contributors working in the orca-companion demo repository.

## Project Context

orca-companion is an e2e-loop demonstration project for the orca-companion agent
harness. It exists to exercise the full loop that the harness is designed to run:
plan, apply, validate, and archive.

The repository is intentionally minimal. It starts with only a placeholder
`README.md`, the harness configuration in `orca-companion.json`, and an empty
`.gitignore`. Subsequent Work Packages build on top of this baseline, each adding
a small, scoped slice of content or capability.

This document is the first such slice. `NOTES.md` sits alongside `README.md` and
captures the conventions and harness context that contributors need before any
larger content changes land.

## Conventions

- Edit only files inside the active Work Package scope; every Work Package declares
  what it is allowed to touch.
- Keep each change scoped to the active Work Package; do not bundle unrelated
  edits into the same patch.
- Coordinate through the orca-companion harness rather than the Git remote; the
  harness owns dispatch, validation, and archiving, and pushing directly to the
  remote bypasses that loop.

## E2E Loop

This repository is exercised through the orca-companion agent harness end-to-end
loop. Each iteration plans a Work Package, applies it in an isolated worktree,
validates the result against an OpenSpec change, and archives the change once it
passes.

Active change artifacts live under `openspec/changes/`. Each change directory
contains the proposal, design, tasks, and spec deltas that describe what the
Work Package is meant to deliver and how it is validated. Archived changes move
into `openspec/changes/archive/` once implementation is complete.
