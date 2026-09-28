# Proposal

## Why

The repository currently has no canonical, human-authored surface for project-level notes. Contributors and downstream automation rely on the README and `orca-companion.json` for declarative facts, but cross-cutting notes (current status, open questions, a pointer to in-flight changes) have nowhere stable to live. This change introduces the initial NOTES.md so future changes have a fixed anchor and the harness can refer to a single, well-known file at the repository root.

## What Changes

- Add a new file `NOTES.md` at the repository root, sibling of `README.md`.
- The initial `NOTES.md` ships with three baseline level-2 sections in this exact order: `Project Status`, `Open Questions`, `Change Index`. Each section has at least one non-heading line of content.
- No existing file in the repository is modified, renamed, or removed.

## Capabilities

### New Capabilities
- `notes-basics`: defines the existence, location, and minimum structural contract of the top-level `NOTES.md` so it can be referenced as a stable surface by downstream specs and harnesses.

### Modified Capabilities
None.

## Impact

- `NOTES.md` — new file added at the repository root. This is the only file the Work Package Scope Envelope permits, so no other path in the repository is touched by this change.

