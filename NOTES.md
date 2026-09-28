# NOTES

## Current State

This repository currently ships `README.md` as its only top-level document. The OpenSpec change tree lives under `openspec/` and holds the in-flight proposals, tasks, and capability specs used by the e2e-loop validation harness. No further notes have been captured yet.

## Decisions

- Establish a single `NOTES.md` at the repository root as the canonical surface for project state, decisions, and open questions so every follow-on change can append without re-deriving context.
- Fix the baseline layout to three level-2 sections (`Current State`, `Decisions`, `Open Questions`) so downstream tooling and reviewers can rely on a stable structure.
- Keep `NOTES.md` plain Markdown prose without fenced code blocks, scripts, or form elements, since it is read by humans and static parsers rather than executed.

## Open Questions

- Which follow-on change will be the first to append real content under these sections, and how should placeholders be phrased so they read as obvious stubs rather than commitments?
- Should later changes introduce additional top-level sections (for example, `Risks` or `References`), or is the three-section layout expected to stay fixed for the lifetime of the project?
