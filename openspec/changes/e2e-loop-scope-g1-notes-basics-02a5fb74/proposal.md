## Why

The `orca-companion` project is an end-to-end loop demonstration target
for the Orca agent harness. Its baseline commit (`e951e88`) currently
ships only a minimal `README.md` and an empty `.gitignore`, with the
README explicitly deferring further sections ("More sections
(Installation, Usage, etc.) will be added in later changes.").

To make later, narrow-scope Work Packages tractable — and to give the
planner and implementer a stable anchor when reasoning about the
baseline — we need a dedicated `NOTES.md` that records durable
developer-facing context: project intent, current baseline shape, the
`orca-companion.json` harness configuration that governs how agents
execute against this worktree, and the conventions future changes are
expected to follow.

This Work Package establishes the `notes-basics` capability: the
contract that `NOTES.md` must satisfy. Future Work Packages may
extend or restructure notes (for example split into per-topic files)
without having to relitigate what "baseline notes" means.

## What Changes

- **Add** a top-level `NOTES.md` file documenting the `orca-companion`
  baseline: project purpose, repository layout, the
  `orca-companion.json` configuration surface, the baseline commit,
  and conventions for future changes.
- **Define** a new OpenSpec capability `notes-basics` that captures
  the required content and formatting contract of `NOTES.md`, so
  subsequent changes can reference and extend it.
- **No source code, configuration, or other tracked files are
  modified.** This Work Package Scope Envelope restricts all changes
  to `NOTES.md`, and the change is intentionally narrow so that
  downstream Work Packages can be admitted against a known clean
  baseline.

## Capabilities

### New Capabilities
- `notes-basics`: Defines what `NOTES.md` is, where it lives, and the
  required sections (Project Purpose, Repository Layout,
  `orca-companion.json` Configuration, Current Baseline, Conventions
  for Future Changes). Any future change that produces a `NOTES.md`
  (or its successors) must remain conformant with this capability.

### Modified Capabilities
- _(none — `NOTES.md` does not yet exist, and no other capability
  references it at baseline.)_

## Impact

- New file: `NOTES.md` at the repository root (the only path inside
  the Work Package Scope Envelope).
- No other tracked file is created, modified, or deleted.
- No new runtime dependencies, no external services, no breaking
  changes for any consumer — the file is purely informational for
  human readers and downstream agents.
- Future changes that touch `NOTES.md` MUST update the `notes-basics`
  spec via an OpenSpec `MODIFIED Requirements` block rather than
  rewriting the contract implicitly.
