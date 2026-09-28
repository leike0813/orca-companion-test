# Design

## Context

The repository is a documentation-and-config demo: `README.md` holds the
project description and `orca-companion.json` holds harness configuration.
There is no source tree, no build, and no test runner. See `proposal.md` for
why the change is wanted and `specs/project-notes/spec.md` for the behavior
contract.

The hard constraint is scope: the Work Package Scope Envelope permits exactly
one file, `NOTES.md`, so the design cannot introduce tooling, a linter, or any
supporting script to enforce the document's shape.

## Goals / Non-Goals

**Goals:**

- Produce a `NOTES.md` that satisfies every requirement in the spec delta by
  hand, so a reader can verify compliance by reading the file.
- Keep the document short enough that its accuracy does not decay quickly.

**Non-Goals:**

- Automated enforcement or validation of `NOTES.md` — outside the scope
  envelope.
- Replacing or editing `README.md`; the notes point at it, they do not
  duplicate it.
- Deciding what later changes will write into the notes.

## Decisions

### Plain Markdown, fixed section order

`NOTES.md` is a plain Markdown file with a `#` title, a short purpose
paragraph, a numbered list of notes, and a closing line naming `README.md`.

*Rationale:* the spec requires exactly these parts, and Markdown with no
template engine or schema is the only form that stays inside a single-file
scope while remaining checkable by eye.

*Alternative considered:* a YAML front-matter block for structured notes was
rejected because nothing in the repository parses front matter, so the
structure would be unenforced convention.

### Notes describe only observable repository state

Every note must be verifiable against files that exist in the repository.
The third requirement forbids claiming dependencies, scripts, or commands the
project does not implement, so notes about absent tooling are deliberately
excluded rather than written as placeholders.

*Rationale:* it is the only way a reader can trust the file without a build
step to cross-check it.

*Alternative considered:* recording planned or upcoming tooling was rejected
as unverifiable at read time and as a likely source of stale statements.

## Risks / Trade-offs

- [Notes drift out of date as the repository changes] → Keep the note list
  minimal and grounded in current files, so there is less to invalidate; later
  changes own their own note updates.
- [The scope envelope leaves no way to check the file automatically] → Accept
  manual review; the required content is small enough to verify by reading.

## Migration Plan

Add `NOTES.md` in a single commit. Rollback is removing that file; nothing
else references it, so no other file needs to change.
