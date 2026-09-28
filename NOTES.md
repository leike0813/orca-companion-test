# Project Notes

This file collects human-authored notes about the `orca-companion` project. It
is a documentation surface only and intentionally does not redefine behavior,
configuration, or commands declared in `README.md` or `orca-companion.json`.

## Project Status

The repository currently ships an isolated project baseline that contains
`README.md`, `orca-companion.json`, and `.gitignore` at the root. `README.md`
describes the project as an end-to-end loop demonstration for the
`orca-companion` agent harness, and explicitly defers richer sections such as
Installation and Usage to later changes. No behavior or configuration in
`orca-companion.json` has been modified by this change.

## Open Questions

- Which `Installation` and `Usage` subsections should land in `README.md`
  first, and in what order, once later changes expand the documentation set?
- Should the `Change Index` below grow into a generated table driven by the
  OpenSpec change set, or remain a manually curated list maintained by
  contributors?
- How should future notes capabilities (`notes-status`, `notes-roadmap`,
  etc.) relate to this baseline `notes-basics` file without duplicating
  content already promised by `README.md`?

## Change Index

- `e2e-loop-scope-g1-notes-basics-02a5fb74` — introduces `NOTES.md` as the
  canonical top-level notes surface for the project, under the
  `notes-basics` capability. Future changes that add further notes
  capabilities are expected to extend this file rather than introduce a
  parallel notes surface.
