# `orca-companion` Developer Notes

This document is the durable developer-notes surface for the
`orca-companion` project. It is the canonical reference for what the
baseline of the project looks like and how future Work Packages are
expected to evolve it without losing context. The contract this file
satisfies is described by the OpenSpec `notes-basics` capability.

## Project Purpose

`orca-companion` is an end-to-end loop demonstration target built for
the Orca agent harness. Its role is to give the Orca planner,
implementer, validator, and finalizer a small, well-instrumented
repository against which the full Work Package lifecycle (planning,
apply, validate, archive) can be exercised end to end. The project is
not a product in its own right; it exists so that downstream agents
have a known-stable anchor to reason about, and so that narrow,
single-file Scope Envelopes (such as `["NOTES.md"]`) are sufficient
to make meaningful progress.

## Repository Layout

At the baseline commit (`e951e88`) the repository root contains three
tracked paths and nothing else. The OpenSpec working state
(`openspec/`) and any agent scaffolding (`.agents/`) live outside the
baseline and are not part of this section.

- `README.md` — a minimal introductory Markdown file that explicitly
  defers further sections ("More sections (Installation, Usage, etc.)
  will be added in later changes."). It is the only narrative surface
  shipped at baseline.
- `.gitignore` — present as a placeholder so that future additions
  have a canonical ignore file to extend. The file is intentionally
  empty at baseline.
- `orca-companion.json` — the JSON configuration consumed by the Orca
  harness. It declares which model the coordinator runs, how workers
  are sandboxed, which git remotes and refs are in scope, and the
  per-execution limits the harness must respect.

## `orca-companion.json` Configuration

The `orca-companion.json` file declares, in nested keys, the runtime
contract between the repository and the Orca agent harness. The keys
below are the durable surface that this section must reflect; any
addition, rename, or removal among them requires a corresponding
OpenSpec change under the `notes-basics` capability.

- `execution.harness` is set to `"codex"`, meaning workers run inside
  the Codex harness implementation.
- `execution.workerModel` is set to `"minimax-cn/MiniMax-M3"`, the
  specific Codex worker model this worktree dispatches against.
- `execution.codexSandbox` is `"danger-full-access"`, granting
  workers unconstrained filesystem and network reach inside the
  Codex sandbox.
- `execution.git.remotes` is `["origin"]`, the only git remote the
  harness is allowed to interact with.
- `execution.git.refs` is `["refs/heads/e2e29-integration"]`, the
  integration branch the harness treats as authoritative.
- `execution.limits.maxActiveWorkPackages` is `1`, so the harness
  admits at most one active Work Package at a time.
- `execution.limits.concurrencyLimit` is `1`, so worker execution is
  strictly sequential within an active Work Package.
- `execution.acceptedRisks` lists `["codex-sandbox-danger-full-access"]`,
  declaring the sandbox mode as an explicitly accepted risk for the
  e2e-loop demonstration.

## Current Baseline

The baseline of `orca-companion` is the single commit that introduces
the repository. Any Work Package building on top of this baseline
inherits its tree without modification; any deviation must be
captured by a new OpenSpec change.

```text
e951e8877b1ed12eebf4eb992ea91623b986b05c
```

The baseline commit (`e951e88`, subject `e2e29: isolated project
baseline`) adds the three tracked root files in one go: an empty
`.gitignore`, the minimal `README.md` that defers detailed sections to
later changes, and the `orca-companion.json` harness configuration.
It establishes the clean state against which every subsequent Work
Package is meant to be evaluated.

## Conventions for Future Changes

Future Work Packages that modify `orca-companion` are expected to
follow three conventions so that the baseline described above stays
recoverable and that downstream agents can plan against a stable
target.

1. **Author changes through OpenSpec.** Every change that introduces,
   renames, or removes a durable surface in this repository must be
   expressed as an OpenSpec change under `openspec/changes/`, with a
   `proposal.md`, `design.md`, `tasks.md`, and (when applicable) a
   delta `specs/<capability>/spec.md`. The harness reads from
   OpenSpec, not from ad-hoc commits.
2. **Keep the Scope Envelope narrow and declarative.** Each Work
   Package's `scopeEnvelope.include` list must enumerate precisely
   the tracked paths that change will touch, and nothing else. If a
   Work Package discovers it needs to widen its scope, it opens a
   new Work Package rather than mutating the existing one; widening
   in place is an explicit anti-pattern.
3. **Keep `NOTES.md` in sync.** Whenever a future change moves the
   baseline commit, adds or removes a durable repository surface, or
   alters any of the `orca-companion.json` keys documented above, the
   change MUST update this file in the same Scope Envelope (or a
   dedicated, narrow one) and MUST update the `notes-basics` spec
   via an `ADDED` or `MODIFIED Requirements` block. Stale notes are
   treated as a conformance failure, not a stylistic issue.
