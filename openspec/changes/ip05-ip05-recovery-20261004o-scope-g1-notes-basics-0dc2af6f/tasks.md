# Tasks

## 1. Notes skeleton

- [x] 1.1 Create `NOTES.md` in the repository root whose first line is the top-level heading `# NOTES`; verify with `test -f NOTES.md && head -n 1 NOTES.md | grep -q '^# '` (exits zero) and with `rm -f`-free negative control by checking the same command against a non-existent path returns non-zero.
- [x] 1.2 Add the five required section headings in order — `## Overview`, `## Repository Layout`, `## Companion Configuration`, `## Working Agreements`, `## Open Items`; verify with `grep -n '^## ' NOTES.md` and confirm the output lists exactly those five headings in that order.

## 2. Content of the project basics

- [x] 2.1 Write `## Overview`: what `ip05-recovery-20261004o` is, and that `NOTES.md` is the place its basics and recovery state are recorded. Verify the section names the project and states that no product code exists yet.
- [x] 2.2 Write `## Repository Layout` as a table of the tracked files (`README.md`, `orca-companion.json`, `NOTES.md`) with the purpose of each. Verify by diffing the table's file list against `git ls-files` so no tracked file is missing and no untracked file is claimed.
- [x] 2.3 Write `## Companion Configuration`: provider connections and models, the default coordinator model, `planning.maxMutations`, `context.maxInputTokens`, the execution harness and sandbox, the git remote and integration ref, the `limits` block, and the accepted risk. Verify each described value by reading it back out of `orca-companion.json` (for example `jq '.execution.limits.concurrencyLimit' orca-companion.json`) and confirming the prose matches.
- [x] 2.4 Write `## Working Agreements`: what the configuration imposes on whoever works here — one work package at a time, the two-attempt implementation and single-repair validation budgets, changes specified under `openspec/changes/` before implementation, and commits targeting the integration branch. Verify each agreement traces back to a value already stated in task 2.3 rather than introducing a new claim.
- [x] 2.5 Write `## Open Items`, stating that the repository has no product code, that `NOTES.md` is the only file this work package covers, and that further notes organization is deferred. Verify the section is non-empty and names `NOTES.md` as the covered path.

## 3. Drift guards

- [x] 3.1 Confirm `NOTES.md` does not duplicate the README or the companion configuration: verify with `grep -n '"' NOTES.md` returning no JSON structure and by reading `NOTES.md` against `README.md` to confirm the project title is their only shared content.
- [x] 3.2 Confirm every configuration claim in `NOTES.md` names its JSON path so it can be maintained by a one-line edit; verify by re-reading the Companion Configuration section and checking each paragraph cites a path that resolves in `orca-companion.json`.

## 4. Acceptance check

- [x] 4.1 Run the read-only acceptance command `test -f NOTES.md && head -n 1 NOTES.md | grep -q '^# '` in the worktree and confirm exit status zero, then run `openspec validate ip05-ip05-recovery-20261004o-scope-g1-notes-basics-0dc2af6f --strict` and confirm the change reports valid.
- [x] 4.2 Confirm the change touches no product file other than `NOTES.md`: verify with `git status --porcelain` that the only added or modified tracked path outside the specification directory is `NOTES.md`.
