# Operating Notes

## Project Overview

`orca-companion` is an end-to-end (e2e) loop demonstration project for the orca-companion agent harness. It exists to exercise the orca orchestration tooling against a deliberately small, version-controlled surface so the harness can be validated, iterated on, and audited without the noise of a real application. The baseline repository ships a stub `README.md`, a single harness descriptor (`orca-companion.json`), and an `openspec/` tree that describes each change in machine-checkable form. Every later change in this repository is expected to flow through the same e2e loop: a planner produces an OpenSpec change, an implementation worker lands the deliverable, and a validator confirms that the deliverable honors the change's scope envelope.

The intended audience is twofold. First, contributors who need to know how to add a new change without breaking the loop. Second, the orchestration tooling itself, which inspects the notes contract documented here to keep planning, implementation, validation, and finalization roles honest.

## Repository Layout

The worktree root contains three tracked baseline files and one OpenSpec tree:

- `README.md` - the public-facing project landing page. It currently declares the e2e-loop nature of the repository and points readers here for operating details.
- `orca-companion.json` - the harness descriptor that orca reads to know which models to use, how to plan, and what execution limits apply. Treat it as configuration, not documentation; this file is the source of truth for runtime knobs.
- `.gitignore` - currently empty but reserved for future artifacts (build outputs, generated change directories, etc.).
- `openspec/` - the spec-driven OpenSpec workspace. It splits into `openspec/specs/` (capability definitions such as `notes`) and `openspec/changes/` (active and archived change proposals). Each active change lives in its own directory named after the change id and contains a `proposal.md`, a `tasks.md`, and a `specs/<capability>/spec.md` delta.
- `NOTES.md` - this file. It is the canonical entry point for contributors who want to understand how the e2e loop operates against the repository.

Changes that need to amend these existing tracked files must list every touched path in the change's `scopeEnvelope.include`. Anything outside the declared envelope is rejected by Admission as `scope_envelope_exceeded`.

## Running the e2e Loop

The e2e loop is driven by the orca orchestration harness described in `orca-companion.json`. Each round begins when the planner receives a goal and emits an OpenSpec change proposal under `openspec/changes/<change-id>/`. The proposal carries a `scopeEnvelope.include` listing the exact paths the change is permitted to touch; the proposal, the matching `specs/<capability>/spec.md` delta, and the human-checkable `tasks.md` together define what the implementation worker is expected to deliver.

Once the change is admitted, the harness dispatches the implementation worker in an isolated worktree. The worker reads the OpenSpec change, performs the in-scope edits (for example, creating or amending this very file when `NOTES.md` is listed in the envelope), records any artifacts, and reports completion back to the coordinator through a single terminal command:

```sh
orca orchestration send --from <terminal> --dispatch-capability <cap> \
  --type worker_done --subject "<short status>" \
  --body "<3-sentence summary>" \
  --task-id <taskId> --dispatch-id <dispatchId> --outcome succeeded \
  [--files-modified "path/a,path/b"] [--report-path "<artifact>"]
```

The `--body` MUST be a three-sentence executive summary describing what the worker did, what it found, and what remains. Sending `worker_done` is required exactly once per dispatch; the coordinator reads the body first and only opens the optional `--report-path` artifact when the summary is not enough. Each dispatch also sends periodic `heartbeat` messages while it is still working, so the coordinator can distinguish a live worker from one that has hung.

After the implementation dispatch completes, a separate validator dispatch runs `openspec validate <change-id> --strict` and re-checks the deliverable against the work package's scope envelope. If validation passes, a finalizer dispatch hands the change off to the archive step. Finalizers do not run `openspec archive` themselves; archiving is owned by a dedicated dispatch that moves the change directory into `openspec/changes/archive/`.

## Conventions

- **OpenSpec is the source of truth.** Every change starts life in `openspec/changes/<change-id>/` with a `proposal.md`, a `specs/<capability>/spec.md` delta, and a `tasks.md`. Edits that do not flow through OpenSpec are out of contract.
- **Scope envelopes are strict.** The set of files the change is allowed to touch is exactly `scopeEnvelope.include`. Anything else is rejected with `scope_envelope_exceeded`. If you need to touch a new file, amend the change proposal first.
- **Markdown uses level-2 sections for canonical headings.** Within `NOTES.md` the canonical sections must be `## Project Overview`, `## Repository Layout`, `## Running the e2e Loop`, `## Conventions`, `## Troubleshooting`, and `## Future Work`, in that order.
- **Worker completion is a single `worker_done` message.** No follow-up chatter, no extra polls; the coordinator already recorded the dispatch as complete the moment it reads that message.
- **Tracked files only.** Anything not currently tracked in git (for example, `openspec/` while a change is being drafted) must be added explicitly by an in-scope commit; do not rely on untracked state.
- **Commit messages name the change id.** Use the change id `e2e-loop-scope-g1-notes-basics-02a5fb74` (or the relevant change id for the current work) in the commit subject so archaeology can link each commit back to its change.

## Troubleshooting

- **`scope_envelope_exceeded` from Admission.** The change modified a path that is not listed in `scopeEnvelope.include`. Add the file to the envelope in the OpenSpec proposal before retrying; do not edit the file outside the change contract.
- **`openspec validate` reports a delta mismatch.** The capability spec delta and the implementation drifted. Re-read `specs/<capability>/spec.md`, run `openspec validate <change-id> --strict`, and align the deliverable with the `ADDED Requirements` before re-running the validator.
- **Heartbeats stop arriving and the coordinator reports the dispatch as hung.** The worker process is likely waiting on a blocked `ask` or has exited without sending `worker_done`. Restart the dispatch from the latest persistent state and confirm that the three-sentence summary message is actually emitted; a missing `worker_done` looks identical to a hang to the coordinator.
- **Unable to find a capability name referenced in a change.** Look under `openspec/specs/`. The capability directory layout mirrors `specs/<capability>/spec.md`; if a folder is missing, the capability has not been added yet and the referencing change must be redesigned.
- **Git ignores `openspec/` after creating new files.** `.gitignore` at the baseline is empty, so untracked files should still be visible. If a file is missing from `git status`, check that the working directory is the worktree root and that `git rev-parse --show-toplevel` matches the expected worktree path.

## Future Work

- **Subsequent generations extend the notes contract.** Later graph generations (for example `e2e-loop-scope#g2`, `g3`, ...) will layer additional capabilities on top of the `notes` capability introduced here. Each new capability should declare its own `specs/<capability>/spec.md` and amend `NOTES.md` only when its scope envelope explicitly includes the file.
- **Automation around `openspec validate` and archive.** A future change is expected to wrap `openspec validate <change-id> --strict` and the archive handoff into reusable dispatcher scripts so the e2e loop can run unattended end-to-end.
- **Populating the README.** The stub `README.md` is intended to gain Installation, Usage, and Contributing sections once the harness behavior stabilizes; until then, `NOTES.md` carries the operating story.
- **Harness descriptor evolution.** `orca-companion.json` will grow new fields as the orchestrator matures (for instance, additional `coordinatorModels` entries or richer `execution.limits`). Changes to that file must be made through an OpenSpec change whose scope envelope lists `orca-companion.json` explicitly.
- **CI guardrails.** A future change may add a CI check that fails the build when an active OpenSpec change is missing one of `proposal.md`, `tasks.md`, or the matching capability spec delta, mirroring the validator checks that the e2e loop already runs locally.
