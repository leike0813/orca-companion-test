# Proposal

## Why

The orca-companion repository currently exposes only a placeholder README that
points at future sections and a small `orca-companion.json` configuration file.
Anyone landing on the project today has no concise record of what the
repository is for or how the harness configuration is organized. A short
`NOTES.md` at the repository root captures that orientation in one place so
newcomers do not have to assemble it from the existing documentation. This
change is the first increment in the e2e-loop scope and intentionally scopes
to that single documentation file.

## What Changes

- Add a new top-level `NOTES.md` that records the purpose of the
  orca-companion repository, summarizes the harness configuration, and
  points readers to the existing `README.md` and the `openspec/` workflow
  directory for additional detail.
- The `NOTES.md` content is plain Markdown describing observable repository
  facts; no executable code, schema, or tooling behavior changes.
- No existing files are modified, renamed, or removed in this increment.

## Capabilities

### New Capabilities

- `notes-basics`: Provide a top-level `NOTES.md` document that orients readers
  to the orca-companion repository, summarizes the harness configuration in
  `orca-companion.json`, and points to the existing `README.md` and the
  `openspec/` workflow as places to learn more.

### Modified Capabilities

- None. No existing capability has its requirements altered by this change.

## Impact

- `NOTES.md` is the only file added by this change, and it lives at the
  repository root, which keeps the change entirely inside the Work
  Package scope envelope (`NOTES.md`).
- No code, API, dependency, runtime system, or other repository file is
  modified, renamed, or removed by this increment.
