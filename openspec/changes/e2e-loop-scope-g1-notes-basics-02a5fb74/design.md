# Design

## Context

The repository has no developer-facing notes file. The only documentation today
is a one-line README, which is too thin to orient a new contributor. This
change introduces a single root-level Markdown file, NOTES.md, and defines the
structural contract it must satisfy.

## Goals

- Give contributors one entry point for project orientation.
- Make the file's required content explicit and checkable, so future edits can
  be validated by a simple command instead of by review opinion.

## Non-Goals

- Replacing or expanding the existing README.
- Automating generation of NOTES.md from other files.
- Documenting anything beyond this repository's own tooling.

## Decisions

**One file at the repository root.** NOTES.md sits next to README.md so it is
discoverable without knowing the internal layout. A single file is enough for
the scope of this change; splitting notes per topic would add navigation cost
without a proven need.

**Structure is specified, prose is not.** The spec pins the headings NOTES.md
must contain and the accuracy rules its content must follow, and leaves the
wording free. This keeps the acceptance check mechanical.

**Accuracy is checkable by command.** The scenarios are written so a shell
command can verify them: file existence, required headings, and absence of
placeholder text.

## Risks / Trade-offs

- Notes can drift from the repository as it changes. The accuracy requirement
  and the verification command are the mitigation; a follow-up change can add
  richer automation if drift becomes a problem.
- Two root-level Markdown files could be seen as redundant. README stays the
  short project blurb; NOTES.md carries orientation detail.

## Migration

None. NOTES.md is additive.

## Open Questions

None.
