# Design

## Context

The baseline worktree contains only `README.md`, `orca-companion.json`,
`.gitignore`, and the `.git` directory. There is no existing notes file
and no existing OpenSpec specs. The first OpenSpec change is intentionally
small: add `NOTES.md` and define its minimal contract.

See `proposal.md` for motivation and `specs/notes-basics/spec.md` for the
behavioral contract.

## Goals / Non-Goals

**Goals:**
- Introduce `NOTES.md` with a Purpose section and a deferred-items list.
- Keep the change additive: only one new tracked file, no edits to the
  baseline.
- Define a reusable capability (`notes-basics`) so future changes can
  extend or replace the notes file without redefining its purpose.

**Non-Goals:**
- No new tooling, scripts, or CI hooks.
- No edits to `README.md`, `orca-companion.json`, or `.gitignore`.
- No multi-file documentation set, no `docs/` directory, no linking
  between files.

## Decisions

- **Single file at repository root.** `NOTES.md` lives next to
  `README.md` rather than inside a `docs/` subdirectory. The baseline
  has no `docs/` directory and the project is small; a single
  top-level file keeps discovery trivial. Alternative considered: a
  `docs/notes.md` location — rejected because it adds a directory for
  one file and the spec describes the file as "at the worktree root".
- **Markdown only, no HTML or remote resources.** Keeps the file safe
  to render on GitHub, local editors, and any Markdown viewer without
  introducing security or privacy surface. Alternative considered:
  embed an image badge — rejected because the spec explicitly forbids
  remote resources.
- **Capability name `notes-basics`.** Mirrors the work package name so
  the spec path is predictable for future changes. Alternative
  considered: a more generic `project-notes` — rejected to keep the
  name aligned with the work package's `notes-basics` envelope.

## Risks / Trade-offs

- [Risk] Future changes may need to split `NOTES.md` into multiple
  files once content grows. → Mitigation: the capability is named
  `notes-basics` so a future change can introduce a separate spec for
  additional note sections without colliding.
- [Risk] Content drift between `README.md` and `NOTES.md`. → Mitigation:
  `README.md` stays a short project description; `NOTES.md` carries
  longer context and deferred items. The spec only requires the
  purpose and deferred-items sections, leaving wording flexible.

## Migration Plan

None. The change is purely additive: one new tracked file. Rollback is
"remove the file" if needed.

## Open Questions

None.
