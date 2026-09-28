# Proposal

## Why

The current `README.md` opens with a single `# orca-companion` heading and a
two-line paragraph, so visitors landing on the repository have no visual anchor
that distinguishes the project at a glance. Introducing a small, self-contained
banner block at the top of the readme gives the page a recognizable hero area
that highlights the project name, states its purpose, and signals the
spec-driven, e2e-loop nature of the work — without adding new files or
dependencies.

## What Changes

- Replace the existing top of `README.md` with a Markdown banner block that
  opens the document, contains the project name as a level-1 heading, and ends
  with a horizontal rule before the existing introductory paragraph.
- Introduce the `readme-banner` capability in OpenSpec so the banner's required
  structure can be tracked alongside the rest of the project's specs.
- No existing files outside `README.md` are modified; the change is scoped to a
  single path.

## Capabilities

### New Capabilities

- `readme-banner`: Tracks the shape and required contents of the banner block
  at the top of `README.md`, including its position, framing, level-1 heading,
  tagline strip, and horizontal-rule separator.

### Modified Capabilities

None.

## Impact

- `README.md` (the top of the file is rewritten to introduce the banner block;
  no other paths are touched).
