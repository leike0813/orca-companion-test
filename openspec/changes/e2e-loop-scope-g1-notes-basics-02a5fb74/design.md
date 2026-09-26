# Design

## Context

The repository currently contains a minimal `README.md` and an
`orca-companion.json` configuration. There is no `NOTES.md` and no
existing spec under `openspec/specs/`. This change introduces the first
notes artifact without touching any other path in the work-package scope
envelope.

## Goals / Non-Goals

**Goals:**

- Add a single `NOTES.md` file at the repository root.
- Establish a `notes-basics` spec capability whose requirements
  describe the file's structure and its non-duplicating relationship
  with `README.md`.

**Non-Goals:**

- Expanding `README.md` or any other documentation file outside the
  scope envelope.
- Adding tooling, scripts, automation, or tests beyond the file itself.
- Defining long-form content; later work packages can extend the
  notes surface.

## Decisions

- Place `NOTES.md` at the repository root next to `README.md` so it is
  discoverable in the same way readers expect the README to be.
  Alternatives considered: a `docs/notes.md` subdirectory - rejected
  because the work-package scope envelope only authorizes `NOTES.md`,
  and a nested path would either need a different filename or violate
  the envelope.
- Use only two top-level sections (`Project Purpose`, `Current Status`)
  in the baseline so future changes can layer in additional sections
  without rewriting the file's structure.
- Express the file's contract as a `notes-basics` spec capability with
  one requirement per structural guarantee, instead of a single combined
  requirement, so each guarantee has its own scenario.

## Risks / Trade-offs

- Future changes that want to add new sections must respect the existing
  `Project Purpose` and `Current Status` headings. → Mitigation: the
  tasks list checks that new sections, if any, are appended rather than
  inserted above the baseline sections.
- A future change that needs richer notes might outgrow the two-section
  baseline. → Mitigation: `notes-basics` is intentionally minimal so a
  follow-on capability can replace or extend it without restructuring.

## Migration Plan

No migration is required. `NOTES.md` is a brand-new file, and no
existing path in the work-package scope envelope is modified.

## Open Questions

None. All decisions follow directly from the work-package scope
envelope.
