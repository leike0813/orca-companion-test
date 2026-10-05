# ip05-cc-04

## Purpose

This repository is the isolated working copy of the `ip05-cc-04` acceptance project. It exists to host one
OpenSpec-driven change at a time inside a Git worktree managed by the Orca orchestration runtime, and to record
the artifacts that describe that change. There is no application code here yet: the deliverable of a work package
is normally a change proposal, its design, its task list, its capability spec, and whatever the change actually
implements. Contributors use this file as the orientation point: what the project is, how the tree is arranged,
which conventions apply, and how work flows through it.

## Project Layout

- `README.md` — the project stub. One line, nothing more; substantive orientation lives here in `NOTES.md`.
- `NOTES.md` — this document: purpose, layout, conventions, and workflow.
- `.gitignore` — currently empty, kept so future ignore rules have a home.
- `orca-companion.json` — Orca companion runtime configuration: provider connections, model references, and the
  coordinator and worker wiring used by the acceptance harness. It is runtime configuration, not project code.
- `openspec/` — the OpenSpec scaffold that holds the change process.
- `openspec/config.yaml` — project-level OpenSpec settings and the hooks for artifact rules and operation guidance.
- `openspec/changes/` — one directory per active or finished change, each holding its own planning artifacts.
- `openspec/changes/archive/` — completed changes, moved here once they are archived.
- `openspec/specs/` — the current, archived state of the project's capabilities, as opposed to pending deltas.

## Conventions

- Every change lives in its own directory under `openspec/changes/`, named for the work package it implements, and
  holds a proposal, a design, a task list, and a capability spec delta.
- Specification text is written as requirements plus scenarios. A requirement states one SHALL-level rule; the
  scenarios under it give the reader a concrete trigger and observable outcome.
- Task lists carry the verification command inline with each task, so a reviewer can rerun the check without
  reconstructing the intent.
- Paths are written relative to the repository root, with no leading slash and no leading dot-slash, and every path
  the documentation names is a path that exists in the working tree.
- Shell commands quoted inline contain no path separators, so a reader can tell a command apart from a path at a
  glance and neither is mistaken for the other.
- Markdown uses one level-one title per document and level-two sections for its parts; section order is fixed where
  a check depends on it.

## Workflow

1. Read `README.md` and this file first, then read the change directory you are working in before touching anything.
2. Plan the change: write the proposal (why and what), the design (decisions and trade-offs), the task list, and the
   spec delta. Keep each artifact to the decisions it actually owns.
3. Implement the tasks in order, running the verification command recorded on each task as you go rather than at the
   end.
4. Review the diff with `git status` and `git diff` and confirm the change touches only the paths its scope allows.
5. Commit with a short, specific message, then archive the change so its spec delta is folded into `openspec/specs/`.
