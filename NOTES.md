# Project Notes

## Purpose

This repository is the baseline for the `orca-companion` end-to-end loop
demonstration. It exists to exercise the planning, implementation,
validation, and finalization stages of the OpenSpec-driven workflow on a
small, intentionally minimal project so that subsequent changes can rely
on a stable starting point.

`README.md` stays a short, public-facing description of the project.
`NOTES.md` is the durable home for context that does not belong on the
front page: the baseline scope, conventions, and follow-on items.

## Scope

The baseline intentionally covers only the scaffolding needed to make the
e2e loop runnable:

- a `README.md` describing the project at a glance;
- an `orca-companion.json` describing the harness configuration;
- a `.gitignore` for local artefacts;
- the OpenSpec change that introduces this notes file itself.

Everything beyond the baseline is captured as a deferred follow-on item
below so it is visible without being part of the first change.

## Deferred

The following items are intentionally out of the current baseline and are
expected to land in later, separate OpenSpec changes:

- Additional `README.md` sections (Installation, Usage, Configuration,
  Troubleshooting) that expand the public-facing description.
- A formal command, library, or service entry point for `orca-companion`
  once the harness contracts are exercised end to end.
- Automated checks or CI hooks that validate `NOTES.md` and the OpenSpec
  changes on every commit.
- A multi-file documentation set under a `docs/` directory if the notes
  grow beyond what fits comfortably in a single file.
- Any cross-references or links between `README.md` and `NOTES.md`,
  pending a decision on whether such linking is useful.
