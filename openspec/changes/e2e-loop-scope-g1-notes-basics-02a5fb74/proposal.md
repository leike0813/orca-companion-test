# Proposal

## Why

The repository currently has only a placeholder README and no place to capture project-wide notes for the orca-companion e2e-loop harness. Without a dedicated `NOTES.md`, conventions, constraints, and day-to-day observations are scattered across chat threads, commit messages, and the temporary memory of each contributor, which makes the project hard to onboard onto and impossible to lint against. This change introduces a single, top-level `NOTES.md` so the harness has an obvious home for those notes starting in generation 1.

## What Changes

- Add a new top-level `NOTES.md` file at the repository root that holds the project's foundational notes.
- Establish a baseline set of note sections (Overview, Conventions, Open Questions) that subsequent changes can extend.
- Document the file under the OpenSpec capability `project-notes` so future changes can add new sections or rules against the same contract.

## Capabilities

### New Capabilities
- `project-notes`: Defines the structure and baseline content of the top-level `NOTES.md` file used to capture project-wide notes for the orca-companion harness.

### Modified Capabilities
- None.

## Impact

- `NOTES.md` (new top-level file created at the repository root).
