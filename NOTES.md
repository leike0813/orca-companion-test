# Developer Notes

This file is the orientation record for the repository: what the project is,
how the harness is configured, how the planning loop runs, which commands a
contributor needs, and what boundaries apply. The README stays the one-line
description of the project; this file holds everything else.

## What this project is

This repository is a working demonstration of the orca-companion agent harness
end to end. A coordinator reads a planning graph, dispatches workers into
isolated worktrees, and drives each change from proposal through validation to
archive without a human editing files by hand. The point of the repository is
to exercise that machinery end to end, so its contents are deliberately small:
there is no application code to run and nothing to deploy. What actually
changes here is documentation and the OpenSpec planning artifacts under
`openspec/`.

Read `README.md` for the project's single-sentence description; this section
explains what working on it involves rather than repeating that blurb.

## Harness configuration (`orca-companion.json`)

`orca-companion.json` at the repository root is the harness manifest. It tells
the coordinator which model to plan with, where issues are tracked, and how
workers are executed. The settings currently in force:

- **Coordinator model** — the `planning-default` configuration ref, served
  through `@langchain/openai#ChatOpenAI` against a `MiniMax-M3.1-Flash-Preview`
  deployment at `https://api.minimax.cn/v1` with `temperature: 0`. It is the
  default coordinator model via `defaultCoordinatorModelRef`.
- **Credentials** — the coordinator reads the `smoke-key` credential ref.
- **Tracker** — GitHub issues, with routed work starting at issue number 1.
- **Planning** — at most 8 mutations per planning run.
- **Context** — a 20,000 token input budget per context assembly.
- **Execution harness** — workers run under `codex`, on the
  `minimax-cn/MiniMax-M3.1-Flash-Preview` worker model, with a
  `danger-full-access` Codex sandbox. That sandbox choice is recorded as an
  accepted risk (`codex-sandbox-danger-full-access`).
- **Git** — work is integrated against the `origin` remote and the
  `e2e70-integration` branch ref.
- **Concurrency limits** — at most 8 active work packages, 1 running at a time,
  2 implementation attempts per task, 1 validator repair, and 1 recovery per
  worker attempt.

## The OpenSpec planning loop

Changes are planned as OpenSpec change directories and landed only after their
artifacts are complete. The layout on disk:

```
openspec/
  config.yaml                       # schema: spec-driven, plus artifact rules
  specs/                            # accepted capability specs, after archiving
  changes/
    <change-name>/
      proposal.md                   # why, what changes, capabilities, impact
      design.md                     # decisions and trade-offs
      tasks.md                      # the checklist to implement against
      specs/<capability>/spec.md    # spec delta for this change
    archive/                        # completed changes, moved here
```

The lifecycle:

1. A change is drafted under `openspec/changes/<change-name>/` with a proposal,
   a design, a task checklist, and a spec delta naming the capability it adds
   or modifies.
2. Planning artifacts are validated before any implementation work starts.
3. Implementation follows the checked tasks in `tasks.md`.
4. A change is complete once every task in `tasks.md` is checked, at which
   point it is archived into `openspec/changes/archive/` and its spec deltas
   are folded into `openspec/specs/`.

Until the first change is archived, `openspec/specs/` is empty and
`openspec list --specs` reports no specs; that is expected, not a broken setup.

## Working commands

All of these run as written from the repository root, the directory holding
`orca-companion.json`.

```sh
# List active changes, and accepted specs
openspec list
openspec list --specs

# Validate a change against its spec delta and task checklist
openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74

# See which planning artifacts of a change are complete
openspec status --change e2e-loop-scope-g1-notes-basics-02a5fb74

# Read a change's artifacts, and get its apply instructions
openspec show e2e-loop-scope-g1-notes-basics-02a5fb74
openspec instructions apply --change e2e-loop-scope-g1-notes-basics-02a5fb74

# Re-initialize OpenSpec in a fresh clone. Without --tools the command opens an
# interactive picker, so always pass the target tool set:
openspec init --tools codex --force

# Archive a completed change (all tasks checked) and fold its specs in
openspec archive e2e-loop-scope-g1-notes-basics-02a5fb74
```

Substitute the change id for any other active change; the id is whatever
directory name sits under `openspec/changes/`.

## Constraints

- Keep changes inside their declared scope envelope. For the change that
  introduced this file, that meant `NOTES.md` only: `README.md` and
  `orca-companion.json` were read for context but were not modified.
- Treat the files under `openspec/changes/` as planning artifacts, not product
  code. Rewriting a proposal or task checklist after it has been reviewed is a
  scope change, not an implementation detail.
- Keep every command listed above runnable as written. If a command needs a new
  dependency or wrapper, add it here rather than assuming it is present.
- Workers run with a `danger-full-access` Codex sandbox, which the manifest
  records as an accepted risk. Do not rely on the sandbox to contain a bad
  command.
- The coordinator plans with temperature 0 against a hosted MiniMax endpoint,
  so planning output is deterministic per input but still depends on a network
  service being reachable.

## Open follow-ups

- The README still promises Installation and Usage sections that do not exist
  yet. Writing them is left to a later change.
- This file documents the planning loop as it behaves today. Re-check the
  layout and command sections whenever the loop or the harness manifest
  changes, since neither is enforced by tooling.
- No capability specs have been accepted into `openspec/specs/` yet, because no
  change has been archived. The first archived change will populate it.
