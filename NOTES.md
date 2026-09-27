# NOTES

Internal developer notes for the `orca-companion` repository. This file is
maintained alongside `README.md` and captures the baseline layout and
conventions that downstream changes build on.

## Project Layout

The repository currently holds four top-level entries:

- `README.md` — the public-facing overview of the project.
- `NOTES.md` — this file; internal developer notes, layout, and conventions.
- `orca-companion.json` — harness configuration consumed by the Orca tooling.
- `.gitignore` — the standard ignore rules for the working tree.

## Conventions

Downstream changes are expected to follow these baseline rules:

- **Spec-first changes.** Every change proposes a spec (proposal, design,
  tasks, and capability deltas) before any implementation work begins, so
  the intent and scope are reviewable up front.
- **Scope envelopes.** Each work package declares an explicit `include` /
  `exclude` set of paths, and edits outside that envelope are rejected by
  the harness.
- **Public role of `README.md`.** `README.md` remains the only public-facing
  overview of the project; `NOTES.md` is internal and must not duplicate or
  replace its content.
