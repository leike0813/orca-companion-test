# Design

## Context

The work package scope envelope for this change allows exactly one path to be created or modified: `NOTES.md`. See `proposal.md` for the motivation and `specs/repo-notes/spec.md` for the normative requirements.

Two constraints shape the approach. First, the deliverable is a single Markdown file, so there is no code architecture to design; the design questions are about document structure and how the accuracy requirement is actually checked. Second, the acceptance evidence for this unit is a command that covers `NOTES.md`, so the structure of `NOTES.md` has to be machine-checkable, not just readable by a human reviewer.

The repository's only existing root content is `README.md` (a one-line project header), `openspec/` (the spec-driven OpenSpec workspace), and `.gitignore`. The top-level directories that exist today and therefore can be described accurately are `openspec/` and its subdirectories.

## Goals / Non-Goals

**Goals:**

- Give `NOTES.md` a small, fixed set of top-level sections that a check can assert on by heading text.
- Make every repository path mentioned in the document resolvable, so the accuracy requirement is verifiable mechanically.
- Keep the file short enough that it stays correct; accuracy is enforced by restricting it to a fixed section skeleton.

**Non-Goals:**

- No automated drift detection in CI, and no new tooling, scripts, or dependencies. The accuracy check is a one-off command, not a pipeline stage.
- No link from `README.md` to `NOTES.md`, and no other file is touched, per the scope envelope.
- No deep content: the notes cover project basics only, not architecture, conventions, or contributor onboarding material.

## Decisions

**Fixed heading skeleton over free-form prose.** The document uses exactly these top-level sections: `Overview`, `Repository Layout`, `Commands`. The verification command greps for these headings, so a stable skeleton is what makes the requirement checkable. The alternative - validating only that the file is non-empty - was rejected because it would pass for a file that answers none of the reader's questions.

**Paths written in backticks, commands written as fenced shell blocks.** Referenced repository paths appear as inline code spans (`` `openspec/changes/` ``) and runnable commands appear in fenced `sh` blocks. The verification command extracts candidate paths from inline code spans and tests each with `-e`, and skips tokens that are not paths. Quoting the paths in a single, predictable form keeps the check simple and avoids parsing Markdown structure.

**Only describe directories that exist at authoring time.** The layout section documents the top-level entries that are present in the baseline commit rather than a directory layout the change itself would introduce. Describing an intended future tree would make the document fail its own accuracy check on day one. The alternative - adding a new directory so the notes have more to describe - was rejected because the scope envelope permits no path other than `NOTES.md`.

**Verification is a single shell command, not a test file.** The unit's acceptance evidence is a command covering `NOTES.md`, so the check is expressed as one `sh` invocation that (a) asserts the file exists and is non-empty, (b) asserts each required heading is present, and (c) asserts every backticked path resolves. A checked-in test script was rejected as out of envelope.

## Risks / Trade-offs

- [Notes drift as the repository changes] → The accuracy requirement plus the heading check make drift a visible, checkable failure; the same command is re-run whenever `NOTES.md` is edited.
- [Path extraction over-matches inline code that is not a path] → The check only tests tokens containing a `/`, so prose code spans such as `-e` are skipped rather than reported as missing.
- [A short document is less useful than a full contributor guide] → Accepted trade-off. Depth was explicitly out of scope; this change establishes the file and its baseline content only.

## Migration Plan

Not applicable. The change adds a new documentation file and modifies nothing else, so rollback is deleting `NOTES.md`.

## Open Questions

None. Every decision that would affect the specs, the document structure, or the task breakdown is settled above.
