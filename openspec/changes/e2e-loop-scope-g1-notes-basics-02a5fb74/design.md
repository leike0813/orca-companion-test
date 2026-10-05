# Design

## Context

See `proposal.md` - Why. The repository currently has a one-line `README.md`, an `openspec/` tree
with an empty `specs/` directory, and no other prose. There is no build system, test runner, or
tooling to integrate with, so the system here is a documentation file and its acceptance is a
review of that file's content.

## Goals / Non-Goals

- Goals: a root `NOTES.md` that a newcomer can read in under a minute and that stays true.
- Non-Goals: restructuring the OpenSpec layout, expanding `README.md`, or capturing per-change
  planning state (that belongs in the change directory, not in the notes file).

## Decisions

- **Single file, no directory.** `NOTES.md` is one file rather than a notes directory. The content
  is short enough that a directory would add structure without adding navigation value. A directory
  is the obvious alternative if the notes later grow past a few screens.
- **Plain Markdown with fixed section order.** Use stable headings (project layout, the OpenSpec
  change flow, conventions) so diffs stay small and links from other docs remain valid. Alternative
  considered: a free-form outline, which makes review noise larger for no benefit.
- **Facts are copied from the repository, never invented.** Every statement in the file must be
  checkable against the tree at the current commit, so a reader can trust it and a reviewer can
  verify it. This is why the file documents conventions rather than a roadmap.

## Risks / Trade-offs

- [Notes drift from reality as the project changes] -> Each convention names the place it comes from
  (`openspec/changes/`, the repository root), and the tasks require a review pass to confirm every
  claim still matches the tree.
- [The file becomes a dumping ground] -> Keep it short and conventions-only; planning detail belongs
  in the change that is doing the planning.

## Migration Plan

None needed: the file is new and nothing reads it at build or run time. Removing it is a clean
rollback.

## Open Questions

None.
