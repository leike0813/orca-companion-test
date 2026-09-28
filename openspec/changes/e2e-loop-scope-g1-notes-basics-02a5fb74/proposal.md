# Proposal

## Why

The project currently ships only a one-line README, so a newcomer has no written record of what this repository is for, how it is configured, or which workflows the orca-companion harness drives. Without a durable notes file, that context lives only in conversations and is lost or re-derived each time the project is opened.

## What Changes

- Add `NOTES.md` at the repository root as the project's developer notes and orientation entry point.
- Document what the project is, what role `orca-companion.json` plays, and how the OpenSpec planning loop works for this repository.
- Record the day-to-day commands a developer needs to work in this worktree, plus known constraints and open follow-ups.

## Capabilities

### New Capabilities

- `notes-basics`: The repository maintains a root-level `NOTES.md` that states the project's purpose, describes the harness configuration, explains how the OpenSpec-driven planning loop operates, and lists the working commands and known constraints for contributors.

### Modified Capabilities

None. This change introduces the first spec in the project; no existing capability changes.

## Impact

- Affected path: `NOTES.md` only. It is a new root-level document created by this change, and it is the only product path this change modifies.
- No API, dependency, or runtime behavior changes. This change is documentation-only: no code executes against `NOTES.md` and no existing file is altered.
- Consumers affected: contributors reading the repository, who gain a written orientation record they did not have before.
