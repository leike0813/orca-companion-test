# NOTES — orca-companion

This document records project basics for the `orca-companion` e2e-loop
demonstration project. `README.md` is the landing page that orients a new
reader; `NOTES.md` is the durable home for the maintainer scope rules,
contributor guidance, and agent-facing conventions that dispatched workers
and follow-on contributors need to follow while operating in this
repository. Anything that is not orientation belongs here.

## Maintainer scope rules

The Orca companion harness enforces a Work Package Scope Envelope on every
change. The rules below are enforced at admission time, not as a polite
reminder.

- **Work Package Scope Envelope.** Every change is admitted with a fixed
  set of paths it is allowed to touch: `scopeEnvelope.include` is the
  allow-list and `scopeEnvelope.exclude` is the deny-list. A change MUST
  NOT add, modify, or delete any path outside that envelope.
- **`proposal.md` `## Impact`.** The `## Impact` section of a `proposal.md`
  may only reference paths that are inside the current Work Package Scope
  Envelope. Referencing a path outside the envelope is an admission error,
  not a content preference.
- **`scope_envelope_exceeded` admission rejection.** When a change's
  effective path set extends beyond the declared envelope — including the
  `## Impact` rule above — the harness rejects admission with the
  `scope_envelope_exceeded` reason. The change must be re-scoped and
  re-submitted; it is not "fixed" by trimming prose after the fact.
- **Dependency-change restriction.** Follow-on changes MUST NOT add,
  remove, or rewrite declared dependencies outside their Work Package
  Scope Envelope. `dependencyChanges: false` is the default, and a change
  that wants to alter dependencies MUST negotiate that explicitly through
  its scope envelope rather than editing manifest files in passing.

## Contributor guidance

Follow-on OpenSpec changes live under a change directory. The shape below
is the contract every new change has to satisfy before it can be
validated, implemented, or archived.

- **Where new change proposals live.** A change lives at
  `openspec/changes/<change-id>/` while it is open. Once archived it is
  moved to `openspec/changes/archive/<change-id>/`. The change id is what
  the harness and `openspec` CLI refer to; do not rename it after
  submission.
- **Specification Unit structure.** Each change directory holds a
  `proposal.md`, a `tasks.md`, and one or more capability folders under
  `specs/<capability>/spec.md`. A capability folder with no `spec.md` does
  not exist as far as the harness is concerned.
- **`proposal.md` expectations.** `proposal.md` explains the *why*, lists
  the *What Changes*, enumerates the affected capabilities under
  `## Capabilities`, and ends with an `## Impact` section. As above, the
  `## Impact` section may only reference paths inside the current Work
  Package Scope Envelope — anything outside that envelope belongs in a
  different change.
- **`tasks.md` expectations.** `tasks.md` breaks the change into
  numbered, checkable tasks. The task list is the implementation
  checklist; tasks are expected to be small enough that a single worker
  attempt can complete them within the declared budget.
- **Spec delta header rules.** A capability folder's `spec.md` MUST use
  one of the four delta headers — `## ADDED Requirements`,
  `## MODIFIED Requirements`, `## REMOVED Requirements`, or
  `## RENAMED Requirements` — to declare what that change contributes.
  The header name is the contract; mixing delta sections without the
  matching header is rejected at validation time.
- **Scenario blocks are mandatory.** Every requirement under a delta
  header MUST include at least one `#### Scenario:` block. A requirement
  without scenarios is incomplete: it cannot describe the behavior it is
  asserting, and the validator will not accept it.

## Agent-facing conventions

Dispatched workers operate on top of the rules above. The conventions
below describe how a worker is expected to read, write, and cite inside
this repository.

- **Read-first order.** When onboarding to a change, read in this order:
  `README.md` for orientation, then `NOTES.md` (this file) for project
  basics, then the active change directory under `openspec/changes/`
  (`proposal.md`, `tasks.md`, and the capability folders under
  `specs/`) for the specific scope you have been dispatched to implement.
  Do not start editing from the change directory without first reading the
  project basics here.
- **Citation expectation.** Every non-trivial claim in a worker report,
  plan, or review MUST point to a file path, a heading, or a line inside
  the active change. A claim without a citation is treated as
  unverified, even if it happens to be correct. Cite the change's own
  `spec.md` for capability claims; cite `NOTES.md` for project-basics
  claims; cite the worker's evidence (a command, a diff, a file listing)
  for state claims.
- **No-archive directive.** A worker operating inside a planning dispatch
  MUST NOT execute `openspec archive` and MUST NOT move the change into
  `openspec/changes/archive/`. Archiving is a separate, later step owned
  by the change's finalizer — not by the implementation worker. This is a
  hard rule: there is no silent exception for partial completion, failed
  validation, or "just cleaning up the directory," and a worker that
  reaches the end of its task with the change still in
  `openspec/changes/` has done the right thing.
- **Scope discipline.** Touch only the paths in the Work Package Scope
  Envelope declared by the dispatch. New files belong inside the
  envelope; renames, deletes, and edits outside the envelope belong in
  a different change. If a task appears to require touching something
  outside the envelope, escalate instead of acting.

## Self-containment

`NOTES.md` is meant to be readable in isolation. The rules below keep it
that way as the project grows.

- **No required external references.** Every link that `NOTES.md` asks a
  reader to follow MUST resolve inside the worktree. No required link
  points at a private system, an external service, or a repository that
  is not part of the public `orca-companion` tree.
- **No dependency on later changes.** Every statement in `NOTES.md` MUST
  remain true even if no change in the `e2e-loop-scope` series has been
  archived yet. `NOTES.md` describes the project as it is, not the
  project as some future change promises it will be.
