# Proposal

## Why

The repository currently has no canonical, human-authored surface for project-level notes. Contributors and downstream automation rely on `README.md` and `orca-companion.json` for declarative facts, but cross-cutting notes (current status, open questions, a pointer to in-flight changes) have nowhere stable to live. This change introduces the initial `NOTES.md` so future changes have a fixed anchor and the harness can refer to a single, well-known file at the repository root.

## What Changes

- Add a new file `NOTES.md` at the repository root, as a direct sibling of `README.md`.
- The initial `NOTES.md` ships with three baseline level-2 sections in this exact order: `Project Status`, `Open Questions`, `Change Index`. Each section contains at least one non-heading line of body content.
- No existing file in the repository is modified, renamed, or removed.

## Capabilities

### New Capabilities
- `notes-basics`: defines the existence, location, and minimum structural contract of the top-level `NOTES.md` so it can be referenced as a stable surface by downstream specs and harnesses.

### Modified Capabilities
None.

## Impact

- `NOTES.md` — new file added at the repository root. This is the only path inside the Work Package Scope Envelope, so no other file in the repository is touched by this change.
