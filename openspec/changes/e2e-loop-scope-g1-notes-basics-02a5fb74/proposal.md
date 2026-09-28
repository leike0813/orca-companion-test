# Proposal

## Why

The repository currently documents its purpose in a one-line `README.md` and
explicitly defers any further sections to later changes. Contributors and
reviewers therefore have no single place that records the project basics
(what the project is, how it is laid out, how to verify it). Adding `NOTES.md`
gives that shared, discoverable starting point.

## What Changes

- Add a top-level `NOTES.md` that captures the project basics for this
  repository.
- Define the required sections and content rules for `NOTES.md` so the file
  stays a stable, reviewable reference rather than free-form prose.

No existing capability changes, and nothing is removed or made incompatible.

## Capabilities

### New Capabilities

- `notes-basics`: Specifies the required structure and content of the
  repository's top-level `NOTES.md` reference document.

### Modified Capabilities

None.

## Impact

- `NOTES.md`: new file created at the repository root; this is the only path
  this Work Package is permitted to touch.

No runtime code, public API, dependency, or build configuration is affected.
