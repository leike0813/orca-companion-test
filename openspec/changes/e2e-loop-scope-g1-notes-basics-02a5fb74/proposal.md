# Proposal

## Why

The orca-companion repository currently ships only `README.md` (a short
placeholder) and `orca-companion.json` (the harness manifest). It has no
canonical, machine-discoverable location for developer-facing project notes
covering scope, intent, and conventions. Without such a file, future
changes must either retrofit a notes section into a populated `README.md`
or scatter rationale across commit messages and PR descriptions. Introducing
`NOTES.md` now — while the surface is still tiny — locks in a stable target
for downstream tooling and gives new readers a single place to learn how
the project intends to evolve.

## What Changes

- Add a new file `NOTES.md` at the repository root (the same directory as
  `README.md`).
- `NOTES.md` documents the project's scope, intent, and developer-facing
  conventions under fixed Markdown headings.
- `NOTES.md` cross-links back to `README.md` so a reader can move from
  user-facing overview to internal notes without guessing.
- No other file in the repository is added, removed, renamed, or modified
  by this change.

## Capabilities

### New Capabilities

- `notes-basics`: Defines the required presence, location, heading
  structure, and cross-link conventions of `NOTES.md` at the repository
  root.

### Modified Capabilities

None.

## Impact

This change introduces exactly one new path: `NOTES.md` at the repository
root. The change does not declare, require, or imply any modification,
deletion, or creation of any other path. Per the Work Package Scope
Envelope, `NOTES.md` is the only file added by this proposal; every
reference to additional context lives inside the file content itself and
does not extend the surface of the change.
