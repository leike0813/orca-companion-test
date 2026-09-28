# Proposal: NOTES Basics

## Why

The fixture worktree currently exposes only a single-line `README.md`, an
empty `.gitignore`, and an `orca-companion.json` configuration file.
Contributors landing on this isolated worktree have no dedicated,
predictable place to record short, durable observations about the
project's most basic facts — conventions, layout, scratch decisions —
without confusing those notes with the project banner in `README.md` or
with a future changelog. A small, well-formed `NOTES.md` filling that
gap keeps the "basics" surface scoped, readable, and easy to keep
honest.

## What Changes

- Add a new file `NOTES.md` at the repository root of this worktree. The
  file SHALL:
  - Begin with a single H1 heading whose visible text is exactly `Notes`,
    and that heading SHALL be the first non-blank line of the file.
  - Contain one or more H2 sections that introduce a basic topic with a
    plain-English heading and at least one sentence of body content
    beneath each H2 heading.
  - Avoid the marker substrings `TODO`, `TBD`, `<placeholder>`, and
    `lorem ipsum` anywhere in the file.
  - Be valid CommonMark and end with exactly one trailing newline
    character (LF, `\n`).
- No other file in the repository is created, modified, or removed by
  this change. In particular `README.md`, `.gitignore`, `.git`, and
  `orca-companion.json` SHALL remain untouched.

## Capabilities

### New Capabilities

- `notes-basics`: Defines the minimal structure and content of the
  project's `NOTES.md` so contributors know where to record the most
  foundational observations about this fixture worktree and what shape
  those notes must take.

### Modified Capabilities

None. No existing capability's requirements change; this change
introduces a new note-keeping contract rather than altering an
established one.

## Impact

- `NOTES.md` — a new file created at the repository root by this change.
  The file SHALL contain the required `# Notes` H1 heading, one or more
  H2 topic sections with at least one sentence of body content under
  each, no `TODO` / `TBD` / `<placeholder>` / `lorem ipsum` markers,
  and SHALL end with exactly one trailing newline character.
