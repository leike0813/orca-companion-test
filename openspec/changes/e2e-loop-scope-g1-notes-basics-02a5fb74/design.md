# Design

## Context

The repository baseline ships with only `README.md`, `.gitignore`, and
`orca-companion.json` at the top level. The README states that "more
sections (Installation, Usage, etc.) will be added in later changes"
and carries no information about how the project relates to the Orca
harness or what its current status is. A separate top-level `NOTES.md`
is the lowest-friction way to record orientation content without
forcing the placeholder README to grow before any richer content is
ready to land.

## Goals / Non-Goals

**Goals:**
- Provide a concise, human-authored orientation document at the
  repository root.
- Establish a single, stable home for cross-cutting project notes that
  is independent of `README.md`.

**Non-Goals:**
- Reproducing the existing `README.md` content inside `NOTES.md`.
- Replacing `README.md` as the project's landing page.
- Documenting any individual change inside `NOTES.md`; that is the
  role of OpenSpec changes under `openspec/changes/`.

## Decisions

- `NOTES.md` lives at the repository root, not under `openspec/`,
  `docs/`, or any other subdirectory, so it is discoverable next to
  `README.md` and `orca-companion.json` without an extra directory
  hop.
- The file uses plain markdown headings (`## Project`, `## Status`,
  `## Next Steps`, `## References`) rather than a custom schema, so
  contributors can edit it without learning a template.
- The "Next Steps" section enumerates active OpenSpec changes by
  identifier, which keeps `NOTES.md` and `openspec/changes/` in
  agreement without duplicating change detail.

## Risks / Trade-offs

- [Future drift between `README.md` and `NOTES.md`] -> Keep the two
  files' scopes distinct: `README.md` is the formal landing page,
  `NOTES.md` is the working orientation document. Drift is acceptable
  in tone, not in the shared fact that both files name the project.
- [`NOTES.md` becomes a dumping ground] -> Limit the mandatory sections
  to four; route any detailed change record to `openspec/changes/`.

## Open Questions

None.
