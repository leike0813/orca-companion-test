# Proposal

## Why

The repository has no written record of what it is, how it is laid out, or the conventions contributors are expected to follow, so every newcomer has to reconstruct that context by hand. Adding a single short notes document at the repository root gives the project a durable, discoverable starting point for that context.

## What Changes

- Add a root-level `NOTES.md` document that describes the project's purpose, its top-level layout, the conventions in use, and the day-to-day workflow.
- Define the required structure of that document (title plus a fixed set of sections) so it stays predictable for readers and for any future check that inspects it.
- Require that every repository path the document mentions actually exists, so the notes cannot silently drift away from the tree they describe.
- Add no runtime code, no build configuration, and no new dependencies; this change is documentation only.

## Capabilities

### New Capabilities

- `project-notes`: The project maintains a single root-level notes document that records the project's purpose, layout, conventions, and workflow, with a fixed section structure and only references to paths that exist in the repository.

### Modified Capabilities

None. The project has no existing capability specifications, so this change introduces the first one.

## Impact

- Adds one new file, `NOTES.md`, at the repository root; nothing else in the repository is created, edited, renamed, or deleted by this change.
- Documentation only: no APIs, runtime behavior, dependencies, build configuration, or external systems are affected.
- Consumers are human readers looking for onboarding context, plus any repository check that inspects the notes document's structure and path references.
