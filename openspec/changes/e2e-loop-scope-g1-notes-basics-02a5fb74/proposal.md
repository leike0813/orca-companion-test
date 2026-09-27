# Proposal

## Why

The orca-companion baseline repository currently ships with only a stub `README.md` ("More sections will be added in later changes") and an `orca-companion.json` harness descriptor. New contributors and downstream automation have no single place that explains how the project is laid out, how the orca e2e loop exercises the harness, or which conventions the loop expects. Without a baseline note file, every later change repeats the same discovery work and reviewers cannot tell whether a work package touched anything outside its declared scope.

This change introduces a baseline `NOTES.md` so the rest of the e2e-loop scope envelopes can reference a stable notes contract rather than re-deriving it.

## What Changes

- Add `NOTES.md` at the repository root as the canonical baseline notes file for orca-companion.
- Populate `NOTES.md` with the canonical sections: Project Overview, Repository Layout, Running the e2e Loop, Conventions, Troubleshooting, Future Work.
- Document the relationship between `NOTES.md`, the OpenSpec change under `openspec/changes/`, and the `orca-companion.json` harness descriptor.
- Establish that future changes may add to `NOTES.md` only via a change whose scope envelope explicitly lists `NOTES.md`; out-of-scope edits are rejected by Admission with `scope_envelope_exceeded`.

## Capabilities

### New Capabilities
- `notes`: Defines the canonical `NOTES.md` baseline content and the contract every notes-aware change must follow.

### Modified Capabilities
- None.

## Impact

- `NOTES.md` — newly created at the repository root with the canonical baseline sections defined by the `notes` capability.
