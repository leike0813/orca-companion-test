# Proposal

## Why

The repository ships only a one-line `README.md` and no written record of how contributors and
agents are expected to work here, so every participant re-derives the same conventions from scratch.
A single checked-in notes file gives the project a durable, reviewable place for those basics.

## What Changes

- Add `NOTES.md` at the repository root: a short, plain-Markdown record of the project's working
  notes (layout, the OpenSpec-driven change flow, and the conventions a change must follow).
- No build, runtime, dependency, or API behavior changes; this change is documentation only.

## Capabilities

### New Capabilities

- `repo-notes`: The repository ships a root `NOTES.md` that records the project's basic working
  conventions and stays accurate as the project changes.

### Modified Capabilities

None. The project has no existing specs, so nothing is being changed.

## Impact

- `NOTES.md` (new file at the repository root) - the only file this change touches.
