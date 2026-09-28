# Notes

`orca-companion` is an end-to-end demonstration project for the orca-companion
agent harness. This page collects the project's basic purpose, contribution
conventions, and scope so downstream work packages and human readers share a
single reference point. For installation, usage, and other hands-on
sections, see [`README.md`](README.md).

## Purpose

This repository exists to exercise the orca-companion agent harness in an
end-to-end loop. It hosts the demonstration project layout, the harness
configuration, and the change records that the harness plans, implements,
validates, and finalizes. Each change in `openspec/changes/` adds a small,
verifiable increment on top of the previous baseline.

## Conventions

- **Propose changes through OpenSpec.** New work, even documentation-only
  edits, starts as a change proposal under `openspec/changes/`. The proposal
  captures the *why*, the *what*, and the task list that drives
  implementation.
- **Keep documentation in plain Markdown.** Files such as `README.md` and
  `NOTES.md` use UTF-8 Markdown with `.md` extensions so they render in
  standard Markdown viewers without extra tooling.
- **Do not edit archived changes.** Once a change is archived under
  `openspec/changes/archive/`, treat it as history. Open a new change
  instead of amending the archived record.
- **Match the scope of the change.** A single work package should add or
  modify only what its proposal lists. Out-of-scope edits belong in a
  separate change so the diff stays reviewable.

## Scope

This change graph covers the foundational documentation landing page:
`NOTES.md` at the repository root. The file documents the project's
purpose, conventions, and scope, and points readers to `README.md` for
installation, usage, and other sections that will be filled in by later
changes. No source code, configuration, or other files are added, renamed,
or removed by the `notes-basics` change.
