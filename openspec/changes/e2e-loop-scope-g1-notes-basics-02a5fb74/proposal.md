# Proposal

## Why

The repository currently ships only a short `README.md` plus the `orca-companion.json`
configuration file, so contributors and downstream consumers have no dedicated place to
record project notes, conventions, or implementation rationale. Establishing a baseline
`NOTES.md` now gives later e2e-loop work packages a stable, in-repo surface for that
content and keeps the readme focused on its introduction.

## What Changes

- Add a new `NOTES.md` file at the repository root containing the baseline sections
  (`# Notes`, `## Project Context`, `## Conventions`, `## Work Package Notes`).
- Introduce the `project-notes` capability in OpenSpec so future documentation changes
  can extend this file under a single capability path.
- No existing files are modified; the change is additive only.

## Capabilities

### New Capabilities

- `project-notes`: Tracks the shape and contents of the repository-root `NOTES.md` file,
  starting with an introduction, project context, conventions, and a place to record
  work package notes.

### Modified Capabilities

None.

## Impact

- `NOTES.md` (new file at the repository root containing the baseline notes sections).
