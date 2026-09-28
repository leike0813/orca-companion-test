# Proposal

## Why

The repository currently explains itself only through `README.md`, which leaves
room for guesswork about the project's conventions and day-to-day working
notes. Contributors arriving from the README have no single place that records
the short, practical notes describing how this demo project is meant to be
used, so we need a `NOTES.md` that states those basics explicitly.

## What Changes

- Add `NOTES.md` at the repository root as the canonical location for basic
  project notes.
- Define the minimum content every `NOTES.md` must carry: a purpose statement,
  a numbered list of basic notes, and a pointer back to the README so the two
  documents do not drift apart silently.
- No runtime code, build pipeline, or dependency changes.

## Capabilities

### New Capabilities
- `project-notes`: Describes what a repository-level `NOTES.md` is, the
  required sections it must contain, and the scenarios a reader or contributor
  can rely on when using or updating it.

### Modified Capabilities

None. `project-notes` is the first capability in this repository; there are no
existing capabilities whose requirements change.

## Impact

- `NOTES.md` (new): the only file this change is permitted to touch; it
  carries the notes themselves.
- Documentation only. No APIs, dependencies, build, or runtime systems are
  affected.
