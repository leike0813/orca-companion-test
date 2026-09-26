# Design

## Context

See `proposal.md` (Why and What Changes) for motivation; this section only
covers the current state that shapes the approach.

- The orca-companion worktree ships with a placeholder `README.md` whose
  body explicitly defers all non-summary documentation
  ("_More sections (Installation, Usage, etc.) will be added in later
  changes._"). That deferral creates an immediate need for a separate
  home for project-level context.
- `orca-companion.json` already fixes the repository as the planning
  root for the e2e-loop-scope graph, so the new file's location is
  implicit and does not need to be negotiated.
- The `.gitignore` is empty, so `NOTES.md` will not be silently
  excluded by accident; tracking the file is a single `git add`.

## Goals / Non-Goals

**Goals:**
- Land the first tracked `NOTES.md` at the repository root with the
  baseline outline spelled out in `specs/project-notes/spec.md`.
- Make the file's existence, top-level heading, `## Purpose` section,
  and at least one reserved heading the four mechanical checks a
  downstream worker can run without re-reading this design doc.
- Leave the file's body stub-only so that later generations of the
  e2e-loop-scope graph can fill in the substantive content (Installation,
  Usage, Conventions, etc.) without touching the outline.

**Non-Goals:**
- Authoring the actual content of `Conventions`, `Status`,
  `Open Questions`, or any other section. Filling those in is the job
  of later Work Packages whose scope envelopes explicitly cover them.
- Editing `README.md` (out of this Work Package's scope envelope).
- Editing `orca-companion.json` or any tooling configuration. The
  NOTES file is plain Markdown with no runtime effect.
- Linking `NOTES.md` from `README.md`. That cross-link is a
  documentation-shape decision reserved for the Work Package that owns
  the README.

## Decisions

- **Place the file at the repository root, next to `README.md`.**
  Alternatives considered: a `docs/` subdirectory, or a `.github/`
  location. `docs/` adds a directory purely for one file and would
  force later generations to negotiate that prefix; `.github/` would
  tie notes to GitHub-specific tooling that the project does not use.
  The repository root is where every contributor already looks for
  `README.md`, so co-locating `NOTES.md` there minimises navigation
  cost.
- **Use a single level-1 heading whose text contains the word "Notes".**
  Alternatives: a level-1 heading with the project name
  ("# orca-companion Notes") or a heading-free preamble. The spec only
  requires the word "Notes" so that later generations can rename the
  project word without invalidating earlier checks; requiring a level-1
  heading (rather than free-form preamble) keeps the file
  Markdown-lint friendly.
- **Reserve `## Conventions` as the primary stub section.** The
  e2e-loop-scope graph's later generations are expected to need a
  conventions section first (Installation and Usage both depend on
  project conventions being pinned down). The spec permits
  `Conventions`, `Status`, or `Open Questions`, but committing to
  `Conventions` makes the file's intent obvious to readers.
- **Use a single empty body under the reserved heading.** A longer
  placeholder would commit the project to prose it has not agreed on;
  an empty body is the least committal and is explicitly permitted by
  the spec.

## Risks / Trade-offs

- **[Risk] Later Work Packages may want a different top-level heading
  word.** → Mitigation: the spec only requires the substring "Notes",
  so any later rename is additive.
- **[Risk] The reserved `## Conventions` heading may turn out to be
  the wrong choice for the graph's second-generation work.** →
  Mitigation: the spec also accepts `Status` or `Open Questions`, and
  the validator only checks that at least one of the three is present.
  A later Work Package can introduce additional headings by editing
  `NOTES.md`; that edit is additive and does not invalidate this
  change's scope envelope.
- **[Risk] `NOTES.md` may be confused with `README.md` by new
  contributors.** → Mitigation: the `## Purpose` section (required by
  the spec) explicitly contrasts the two files, and the spec's first
  requirement pins the file's location next to `README.md` so any
  agent listing the project root sees both together.

## Migration Plan

None. This change adds one tracked file; it does not rename, move, or
remove anything, and there is no existing `NOTES.md` in the repository
to migrate from. The file becomes visible to consumers only after the
implementation Work Package commits it, which is intentional.

## Open Questions

None. All design-level unknowns (heading text, reserved section choice,
stub-vs-prose body) are resolved above; later Work Packages will surface
their own questions when filling in concrete sections.

