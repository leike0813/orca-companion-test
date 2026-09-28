# Design

## Context

The baseline repository contains three files at the root: `.gitignore`,
`README.md`, and `orca-companion.json`. There is no general-purpose notes file,
which leaves implementation rationale, conventions, and work-package observations
without a home. The Work Package Scope Envelope restricts this change to
`NOTES.md`, so the design must keep all material inside that single new file.

## Goals / Non-Goals

**Goals:**

- Establish a single `NOTES.md` file at the repository root with a predictable
  section outline that future documentation changes can extend.
- Keep the file content self-contained, in plain Markdown, and free of generated
  artifacts so it remains diff-friendly across work packages.
- Map the file's section outline to the requirements declared in
  `specs/project-notes/spec.md` so the spec, design, and tasks stay aligned.

**Non-Goals:**

- Modifying `README.md`, `orca-companion.json`, `.gitignore`, or any other file
  outside the `NOTES.md` Scope Envelope.
- Introducing tooling, scripts, or CI hooks to validate `NOTES.md` content.
- Backfilling historical notes or migration commentary; later work packages may
  add those entries.

## Decisions

- **Single file at the repository root.** `NOTES.md` lives next to `README.md`
  rather than under a subdirectory so it is discoverable by default and matches
  the conventions of other GitHub-flavored documentation projects. Alternatives
  considered (a `docs/notes.md` subpath, multiple per-topic files) were rejected
  because they expand the Scope Envelope and add navigation overhead for a
  one-section baseline.
- **Four fixed top-level headings.** The file uses `# Notes`, then
  `## Project Context`, `## Conventions`, and `## Work Package Notes`. Each
  section starts with one paragraph so the structure is observable from the
  spec's scenarios. A different fixed outline (e.g., adding `## Risks` now) was
  rejected because the requirements do not yet call for it and adding headings
  speculatively bloats the baseline.
- **Plain Markdown, no embedded HTML or templating.** Keeps the file reviewable
  in any editor and avoids encoding assumptions about downstream renderers.

## Risks / Trade-offs

- **Future sections may outgrow a single file.** → When a future work package
  needs additional structure, it should propose a split under its own capability
  rather than overload `NOTES.md`. The current baseline keeps the surface small
  on purpose.
- **Empty placeholders could be mistaken for documentation.** → The
  `Work Package Notes` section will receive its first concrete entry as part of
  this change so the section is not left as a stub; later work packages append
  their own observations under that same heading.

## Open Questions

None. The Scope Envelope, capability path, and required sections are all fixed
by the work package contract.
