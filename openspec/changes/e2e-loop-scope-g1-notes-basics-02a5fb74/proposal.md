# Proposal

## Why

The repository currently exposes only a stub `README.md` and no persistent
location for capturing project notes, decisions, or working context. Anyone
reading the repo has no place to discover why early choices were made or
what is intentionally left for later changes, which makes it harder to keep
follow-on changes coherent with the baseline.

## What Changes

- Add a new `NOTES.md` file at the repository root that records the project's
  baseline notes: purpose, scope, and a short list of known follow-on items.
- Establish a small, explicit convention for what `NOTES.md` covers so future
  changes have a stable home for evolving context.

## Capabilities

### New Capabilities
- `notes-basics`: Captures the baseline project notes file `NOTES.md`, its
  purpose, and the minimal content it must contain.

### Modified Capabilities
None.

## Impact

- Adds the file `NOTES.md` at the worktree root.
- No changes to existing tracked files.
- No new runtime dependencies, build steps, or external systems.
