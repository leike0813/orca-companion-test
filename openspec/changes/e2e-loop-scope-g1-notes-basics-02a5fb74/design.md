# Design

## Context

See proposal.md - Why for motivation. The repository currently has
`README.md` (a placeholder pointing at future sections), `orca-companion.json`
(the harness configuration consumed by the orca-companion dispatcher), an
empty `.gitignore`, and the in-flight `openspec/` workflow directory created
by this change. No `NOTES.md` exists yet. The Work Package scope envelope
limits this increment to a single new file, `NOTES.md`, so the design is
constrained to the contents and placement of that file.

## Goals / Non-Goals

**Goals:**
- Produce a single Markdown file at the repository root named `NOTES.md`
  that satisfies every requirement in `specs/notes-basics/spec.md`.
- Keep `NOTES.md` short enough to read in one sitting while still
  covering repository purpose, the role of `orca-companion.json`, and
  pointers to `README.md` and `openspec/`.
- Make the new file the only artifact introduced by this change so the
  validator can confirm scope adherence.

**Non-Goals:**
- Modifying `README.md`, `orca-companion.json`, `.gitignore`, or any
  file under `openspec/` (except for the spec describing this
  capability).
- Introducing or recommending additional documentation files
  (`CONTRIBUTING.md`, `ARCHITECTURE.md`, etc.) in this increment.
- Defining CI, release, or packaging behavior for the project.

## Decisions

- **Single short Markdown document.** `NOTES.md` is plain Markdown with
  a short title and three short prose sections: purpose, harness
  configuration, and pointers to other documentation. Rationale: the
  capability spec calls for orientation prose that any reader can
  understand; a single short document is the simplest shape that meets
  the spec and stays inside the Work Package scope envelope.
  Alternatives considered: (a) a multi-page site generated from a
  template, (b) embedding orientation content inside `README.md`.
  Both were rejected because they would require editing files outside
  the scope envelope or pull in additional tooling not justified by
  the spec.
- **Top-level placement.** `NOTES.md` lives at the repository root
  alongside `README.md` and `orca-companion.json`. Rationale: the
  capability requirement names "the repository root" explicitly, and
  co-locating it with `README.md` makes the pointer trivial.
  Alternatives considered: nesting the file under `docs/`. Rejected
  because the requirement and the existing `README.md` placement
  establish the repository root as the convention.
- **Manual authoring, no generator.** The content of `NOTES.md` is
  written by hand in this change. Rationale: there is no upstream
  source to generate from, the file is small, and a generator would
  expand scope beyond the capability. Alternatives considered: a
  small script that pulls descriptions from `orca-companion.json`.
  Rejected because it would couple `NOTES.md` to the config schema
  and risk drift.

## Risks / Trade-offs

- [Risk] `NOTES.md` content drifts from the actual repository contents
  as later changes land. → Mitigation: keep statements in
  `NOTES.md` deliberately broad ("configure the orca-companion
  harness", "specifications live in `openspec/`") so they remain
  accurate across ordinary evolution, and let later OpenSpec changes
  update the file when concrete details need to be sharpened.
- [Risk] The single-file scope envelope pushes orientation details
  into `NOTES.md` that some readers would expect in `README.md`. →
  Mitigation: the document explicitly defers detailed sections to
  `README.md`, matching the existing README statement that more
  sections will be added in later changes.

## Migration Plan

No migration is required. The change introduces one new file at the
repository root and does not alter any existing file. A subsequent
`openspec archive` will move the change into `openspec/changes/archive/`
and merge the `notes-basics` capability into the main specs tree; that
is outside the scope of this planner dispatch.

## Open Questions

None. The capability spec fully describes the observable behavior of
`NOTES.md`, and the Work Package scope envelope limits the change to
that single file.
