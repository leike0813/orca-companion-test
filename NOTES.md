# NOTES

## Purpose

The `orca-companion` repository is a small end-to-end demonstration project
for the orca-companion agent harness. It exists to give the harness a
realistic workspace to operate on while exercising the loops that drive
planning, implementation, validation, and finalization. Reading this file
is the fastest way to get oriented before exploring the rest of the
repository.

## Harness configuration

The repository ships with `orca-companion.json` at the root. That file is
the harness configuration consumed by the orca-companion dispatcher: it
declares the coordinator models it can use, the tracker settings that
connect work to GitHub, and the planning, context, and execution knobs
that bound each loop. Treat it as the single source of truth for how the
harness should run against this project; if a value there seems to
contradict what you read elsewhere, the configuration file wins.

## Where to go next

- `README.md` carries the project landing page. Today it is a short
  placeholder that promises more sections (Installation, Usage, and so
  on) in later changes, so treat it as a stub rather than a reference.
- The `openspec/` directory holds the OpenSpec workflow that drives
  change management for this repository. Active change proposals live
  under `openspec/changes/`, the merged specifications live under
  `openspec/specs/`, and the workflow itself is configured by
  `openspec/config.yaml`. When you want to understand, propose, or
  review a change to this project, that is where the work happens.
