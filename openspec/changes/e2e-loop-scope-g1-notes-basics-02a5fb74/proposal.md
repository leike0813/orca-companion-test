# Proposal

## Why

The `orca-companion` e2e-loop demonstration project currently has only a
sparse `README.md` and no dedicated notes file. Adding a baseline `NOTES.md`
gives downstream tooling and human readers a single canonical place to find
project purpose and current status, and it lets later changes extend the
notes surface without re-establishing the file. This change keeps the
content intentionally minimal so future work packages can layer in detail.

## What Changes

- Add a new `NOTES.md` file at the repository root with two short sections
  describing the project's purpose and its current status.
- Introduce a new `notes-basics` capability that defines the contract for
  this baseline `NOTES.md`.

## Capabilities

### New Capabilities

- `notes-basics`: Defines the baseline `NOTES.md` shipped at the repository
  root, including its required sections and its relationship to `README.md`.

### Modified Capabilities

None.

## Impact

- `NOTES.md`: new file at the repository root containing the project's
  baseline notes. This is the only path in this change's scope envelope.
