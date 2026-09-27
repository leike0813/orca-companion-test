# Proposal

## Why

The repository currently ships only a stub `README.md` plus the harness configuration (`orca-companion.json`) and no other project-level documentation. Contributors and downstream tooling have no canonical, project-rooted place to record orientation, conventions, and pointers that do not belong in a hand-written `README`. This change introduces `NOTES.md` as the first such document so later changes (Installation, Usage, etc.) can extend it incrementally without re-shaping the root documentation layout.

## What Changes

- Add a new file `NOTES.md` at the repository root.
- `NOTES.md` MUST contain a top-level title, an Overview section, a Conventions section, and a Pointers section.
- `NOTES.md` MUST be plain Markdown, repository-rooted, and checked into version control with the change.
- No other files in the repository are introduced, renamed, deleted, or restructured by this change.
- No runtime, build, or API behavior changes.

## Capabilities

### New Capabilities
- `project-notes`: A canonical, repository-rooted Markdown document (`NOTES.md`) that records the project's orientation, conventions, and pointers for contributors.

### Modified Capabilities
None. This change introduces a single new capability and does not modify any existing capability's requirements.

## Impact

- Adds the file `NOTES.md` at the repository root.
- No other files, directories, configuration, dependencies, build steps, or runtime behavior are affected by this change.
