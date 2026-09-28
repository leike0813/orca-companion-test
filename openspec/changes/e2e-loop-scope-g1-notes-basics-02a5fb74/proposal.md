# Proposal

## Why

The repository currently ships with only a `README.md` stub that explicitly
defers future sections to "later changes." Downstream work packages in this
graph generation will add installation, usage, and other documentation, but
they have no stable landing page in the project root to point at. We need a
foundational `NOTES.md` that captures the project's basic purpose,
contribution conventions, and scope so subsequent work packages and human
readers share a single reference point.

## What Changes

- Add a new `NOTES.md` file at the repository root.
- `NOTES.md` documents the project's purpose, contribution conventions, and
  scope, and points readers at the `README.md` for installation, usage, and
  other sections that will be filled in by later changes.
- No source code, configuration, or other files are added, renamed, or
  removed by this change.

## Capabilities

### New Capabilities

- `notes-basics`: A `NOTES.md` file at the repository root that captures the
  project's basic notes — purpose, conventions, scope, and pointers to other
  documentation — using plain UTF-8 Markdown.

### Modified Capabilities

- `n/a`

## Impact

- New file: `NOTES.md`
