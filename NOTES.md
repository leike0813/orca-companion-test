# Notes

This file collects the most basic, durable observations about the
`orca-companion` fixture worktree. It is intentionally short: contributors
can land here first when they want to orient themselves, and the rest of
the project's documentation lives elsewhere.

## Project Stage

This worktree is a fixture used to exercise the Orca multi-agent harness.
It has no source code, no test suite, and no runtime of its own; every
file in the worktree exists to support that harness rather than to ship
a product. New capabilities are introduced through future OpenSpec
changes rather than by editing this file directly.

## Repo Layout

The repository root contains a single-line `README.md` that carries the
project banner, an empty `.gitignore`, the `orca-companion.json` harness
configuration, and the `openspec/` directory that holds change proposals
and capability specs. Contributors should treat any new top-level file
as out of scope for this change unless an OpenSpec change explicitly
adds it.
