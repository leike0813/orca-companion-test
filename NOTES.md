# Purpose

`orca-companion` is an end-to-end (e2e) loop demonstration for the
`orca-companion` agent harness. The repository exists to exercise the full
OpenSpec-driven change lifecycle (proposal, spec delta, tasks, apply,
verify, archive) on a deliberately small repository so the harness can be
validated against realistic planning, implementation, and finalization
turns. It is needed now because the e2e test path is the most direct way to
confirm that the orchestrator's planner, worker, validator, and finalizer
roles cooperate around real code changes, and it must do so on a codebase
small enough to inspect by hand yet structured enough to expose the edges
the harness is supposed to handle.

# Baseline Scope

The baseline commit for this demonstration (`42cb8b9`) ships three files
that together make the project inspectable and reproducible without any
runtime dependencies:

- `README.md` — the human-facing entry point that names the repository and
  defers future sections to later changes.
- `NOTES.md` — this file, which anchors the demonstration and seeds the
  later note-driven changes.
- `orca-companion.json` — the harness configuration that names the
  coordinator model, harness, and execution limits used to drive this
  e2e loop.

No other paths (no source tree, no build manifest, no runtime service) are
part of the baseline; everything beyond these three files is introduced
by later Work Packages.

# Follow-ups

- Add an `Installation` section to `README.md` that describes how to clone
  the repository, prepare credentials, and run the OpenSpec validation flow
  locally.
- Add a `Usage` section to `README.md` that walks through a sample
  `openspec new change` to `openspec apply` to `openspec archive` run end
  to end.
- Add a `Contributing` section to `README.md` that documents the note-driven
  Work Package conventions and the contract between planner, worker, and
  validator roles.
