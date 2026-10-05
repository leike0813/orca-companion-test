# Proposal

## Why

The repository currently ships only a placeholder README, so contributors have
no single place to look up the basics of working in this project: what the
repository is for, how to run its tooling, and where specifications live. A
root-level NOTES.md gives that shared orientation without duplicating the
OpenSpec change history.

## What Changes

- Add a root-level NOTES.md that documents project purpose, prerequisites,
  common commands, and the OpenSpec workflow.
- Define the `project-notes` capability so NOTES.md has a maintained structural
  contract rather than being an unconstrained scratch file.
- Require NOTES.md to name the OpenSpec directory so readers can navigate from
  notes to specifications.

## Capabilities

### New Capabilities

- `project-notes`: The structure and required content of the repository-root
  NOTES.md file, including the required sections and the OpenSpec workflow
  pointer.

### Modified Capabilities

None. No existing capability changes its requirements.

## Impact

- Adds `NOTES.md` at the repository root.
- No runtime code, API, dependency, or configuration behavior changes; the
  change is documentation-only.
