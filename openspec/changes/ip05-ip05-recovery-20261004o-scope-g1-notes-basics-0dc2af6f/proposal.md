# Proposal

## Why

The repository is a freshly recovered, empty Orca worktree project: its entire tracked content is a two-line README and an Orca companion configuration file, so nothing on disk explains what the project is, how the companion is wired, or which recovery items are still open. Without a notes file the next worker or agent has to reverse-engineer `orca-companion.json` from scratch before it can make any change, and the recovery state lives only in the coordinator's head.

## What Changes

- Add a repository-root `NOTES.md` that records the project basics: what the project is, which files exist and what each one is for, how the Orca companion configuration is wired (connections, models, harness, git target, limits, accepted risks), the working agreements the current configuration imposes, and the open recovery items.
- Establish `NOTES.md` as the durable, human- and agent-readable entry point for project basics, kept deliberately separate from the minimal `README.md` so the two files do not drift into duplicates.
- Add no product code, no build tooling, and no dependency changes. The only repository file this change touches is `NOTES.md`.

## Capabilities

### New Capabilities

- `project-notes`: The repository maintains a single `NOTES.md` at its root that documents the project's purpose, repository layout, companion configuration, working agreements, and open items, and that is kept verifiable with a simple file-and-heading check.

### Modified Capabilities

None. `project-notes` is the first capability in this repository; there is no existing `openspec/specs/` inventory to amend.

## Impact

- Affected file: `NOTES.md` — a new file at the repository root. It is the only product path this change creates or modifies, and the only path in this change's impact.
- No APIs, packages, dependencies, build configuration, or runtime systems are touched.
- No other repository file is created, edited, renamed, or deleted by this change.
- Verification is a read-only command (`test -f NOTES.md` plus a heading grep), so acceptance introduces no build or test dependency.
