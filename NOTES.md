# NOTES

## Overview

`ip05-recovery-20261004o` is a recovered Orca worktree project whose only tracked content is a title, an Orca companion configuration file, and this notes file. There is no product code yet: no application source, no package manifest, no build tooling, no test suite. An empty repository is easy to misread as a lost one, so it is worth stating plainly — if you go looking for a codebase here, you will not find it.

This file is the durable entry point for the project's basics. It records what the project is, what each file is for, how the companion configuration is wired, the working agreements that wiring imposes on whoever works here, and the open recovery items. Recovery state lives here so the next worker or agent does not have to reverse-engineer `orca-companion.json` or ask the coordinator.

## Repository Layout

| Path | Purpose |
| --- | --- |
| `README.md` | The project title, and nothing else. Kept minimal so it cannot drift into a duplicate of this file. |
| `orca-companion.json` | The Orca companion configuration (schema version 2): provider connections, models, worker profiles, planning and context budgets, git integration target, and execution limits. The machine-readable authority for how work runs here. |
| `NOTES.md` | This file. The human- and agent-readable record of the project basics; it describes the configuration by reference and never copies it. |
| `.gitignore` | Empty placeholder, so ignore rules have a home once the project grows. |

Specification material is not product content: each in-flight change is proposed under `openspec/changes/`, and accepted capability specifications live under `openspec/specs/`. Those files describe work that has not been implemented and are not part of the product surface.

## Companion Configuration

`orca-companion.json` is the authority for every value in this section. Nothing below is a copy of it — each item names the JSON path it describes, so a configuration change is a one-line edit here rather than a rewrite. Read any path with jq, for example:

    jq .execution.limits.concurrencyLimit orca-companion.json

**Provider connections and models.** Two connections are declared in `providerConnections`: `acceptance-coordinator` (labelled 本机 OAuth Coordinator) and `acceptance-worker` (labelled 本机 OAuth Worker Harness). Both use the OpenAI provider integration `@langchain/openai#ChatOpenAI` at temperature 0 against the local base URL in `providerConnections[].modelOptions.configuration.baseURL`, and both entries in `models[].model` name the same underlying model. The coordinator connection holds a managed credential (`providerConnections[0].credential.kind`); the worker connection authenticates through the harness login (`providerConnections[1].credential.kind`) and additionally carries the `companion-oauth` Codex provider block (`providerConnections[1].codex`). Credential references and model identifiers are intentionally not itemized here — they live in `providerConnections[].credential` and `models[].model`, because the notes exist to explain how work happens, not to enumerate secrets.

**Coordinator model.** `defaultCoordinatorModelRef` selects the `planning-default` entry in `coordinatorModels`, which reuses the coordinator connection and its `acceptance-model`. A separate entry, `acceptance-worker-model`, is the model the worker profiles run on.

**Tracker.** `tracker` is a GitHub tracker, and `tracker.routeMapIssueNumber` is the single issue the run is mapped onto.

**Planning and context budgets.** `planning.maxMutations` is 8 — a plan may introduce at most eight file mutations. `context.maxInputTokens` is 20000 — that is the input budget an agent context is built to.

**Execution harness and sandbox.** `execution.harness` is `codex`, and every profile in `execution.workerProfiles` repeats that harness; `execution.workerProfileRefs` binds the five roles — planner, implementation, validator, finalizer, and recovery_utility — to their profiles. Every profile runs the worker-side model. `execution.codexSandbox` is `danger-full-access`, so agents run without filesystem or network containment.

**Git integration.** `execution.git.remotes` lists only `origin`, and `execution.git.refs` names one integration branch, `refs/heads/ip05-recovery-20261004o-integration`. Work lands there; do not invent side branches.

**Limits.** `execution.limits.concurrencyLimit` is 1: one work package executes at a time, even though `execution.limits.maxActiveWorkPackages` tracks up to 8 active ones. The per-attempt budget in the same block is `execution.limits.implementationAttempts` = 2, `execution.limits.validatorRepairs` = 1, `execution.limits.graphRevisions` = 2, `execution.limits.specificationRevisions` = 2, and `execution.limits.maxRecoveriesPerWorkerAttempt` = 1.

**Accepted risk.** `execution.acceptedRisks` records `codex-sandbox-danger-full-access`. The full-access sandbox is a deliberate decision, not an oversight, and should not be reported as a finding.

## Working Agreements

Each agreement below restates a constraint already stated above; none of them is new policy.

- **One work package at a time.** `execution.limits.concurrencyLimit` is 1, so work packages queue behind each other instead of running in parallel.
- **Two implementation attempts, one validation repair.** `execution.limits.implementationAttempts` and `execution.limits.validatorRepairs` cap the retries, and `execution.limits.maxRecoveriesPerWorkerAttempt` allows one recovery per attempt. Plans and specifications may each be revised twice (`execution.limits.graphRevisions`, `execution.limits.specificationRevisions`).
- **Specify before implementing.** Every change is proposed under `openspec/changes/` with a proposal, design, task list, and spec delta, and is checked with `openspec validate <change-id> --strict` before implementation starts.
- **Keep plans inside eight mutations.** `planning.maxMutations` is 8; split a larger goal into separate work packages rather than widening one plan.
- **Work within the context budget.** `context.maxInputTokens` is 20000, which is why large files are described by path and section instead of pasted in full.
- **Commit to the integration branch.** Work goes to the branch in `execution.git.refs` through the remote in `execution.git.remotes`.
- **Act deliberately inside the sandbox.** `execution.codexSandbox` is `danger-full-access` and that risk is accepted, which is exactly why a destructive or outward-facing action still needs a real reason.

## Open Items

- **No product code exists.** The repository has no application source, no dependencies, and no tests. The only product file this work package covers is `NOTES.md`; it creates, edits, renames, and deletes no other file.
- **Further notes organization is deferred.** Whether the notes should later be split per work package, once more than one work package exists, is an open question that does not affect this file today.
- **Remaining recovery work is specified, not implemented.** Outstanding items live in the OpenSpec change under `openspec/changes/`, and each one must be implemented and validated in its own work package.

