# Notes

## Overview

`orca-companion` is an end-to-end loop demonstration project for the
orca-companion agent harness. It exists to exercise the full planning,
implementation, validation, and finalization loop against a deliberately
small repository so that contributors and downstream agents can verify
handoffs, scope envelopes, and evidence flow without the noise of a real
codebase. Each graph node in the e2e-loop demo is implemented as its own
OpenSpec change and work package, and `NOTES.md` is the shared, stable
baseline that those work packages layer on top of.

This file is intentionally minimal: it documents the cross-cutting
context that does not fit in `README.md`, does not belong to any single
module, and should remain readable on its own with no network access.
Future graph nodes (contributor guides, release notes, change-log
summaries, and similar surfaces) will add their own changes rather than
extending this baseline implicitly.

## Conventions

- Each non-trivial change is implemented through an OpenSpec change under
  `openspec/changes/<change-id>/`, with a `proposal.md`, `tasks.md`, and
  one or more `specs/<capability>/spec.md` deltas.
- Work packages are scoped by an explicit `Scope Envelope` listing the
  repository paths the change is allowed to create or modify; paths
  outside that envelope must not be touched by an implementation worker.
- File names inside the repository follow the existing conventions:
  `README.md` and `NOTES.md` use `SCREAMING_SNAKE_CASE.md`, configuration
  uses lower-case dot-names (`orca-companion.json`), and OpenSpec change
  ids use lower-case kebab-case suffixed with a short digest
  (`e2e-loop-scope-g1-notes-basics-02a5fb74`).
- Markdown files use GitHub-flavored Markdown, are UTF-8 encoded without
  a byte order mark, and must remain self-contained (no required images,
  scripts, or external links) so they render correctly in any viewer.
- Every acceptance task lists the exact verification step (a command,
  file read, or parser invocation) that the validator will run; the
  implementation is only considered complete when that step passes.

## Pointers

- [`README.md`](README.md) — the top-level project introduction and the
  first file a new contributor should read.
- [`orca-companion.json`](orca-companion.json) — the canonical
  configuration for the orca-companion harness, including the planner
  model, execution limits, and the Git tracker settings used by the
  e2e-loop demo.
