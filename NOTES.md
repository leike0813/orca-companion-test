# orca-companion notes

This file collects cross-cutting, human-authored notes about the orca-companion
project. It is a documentation surface only and stays consistent with the
declarative facts in `README.md` and `orca-companion.json`.

## Project Status

The repository currently ships the minimal baseline described in `README.md`:
a short project blurb and a note that richer sections (Installation, Usage,
etc.) will be added by later changes. This change introduces `NOTES.md` as a
stable anchor for project-level notes; no other baseline file is modified.

## Open Questions

- Which downstream changes should first extend `NOTES.md` with richer
  status, roadmap, or contributor content beyond the three baseline sections?
- How should future changes reconcile overlapping prose between
  `README.md` and `NOTES.md` without contradicting either file?

## Change Index

- `e2e-loop-scope-g1-notes-basics` — introduces `NOTES.md` and defines the
  `notes-basics` capability that pins its location, filename, and three
  baseline sections (`Project Status`, `Open Questions`, `Change Index`).
