# Tasks — `e2e-loop-scope-g1-notes-basics-02a5fb74`

> Scope Envelope (this Work Package): `["NOTES.md"]`.
> Anything outside this list is out of scope. If a future refinement
> proves necessary, open a new Work Package rather than widening this
> one.

## 1. Author the `NOTES.md` content

- [ ] 1.1 Write the `Project Purpose` paragraph identifying
  `orca-companion` as the Orca e2e-loop demonstration target.
- [ ] 1.2 Write the `Repository Layout` section enumerating every
  tracked path at the repository root (`README.md`,
  `orca-companion.json`, `.gitignore`, and any other root-level file
  present at apply time), with a one-sentence role description each.
- [ ] 1.3 Write the `\`orca-companion.json\` Configuration` section
  summarising, in one sentence each, at minimum:
  - `execution.harness`
  - `execution.workerModel`
  - `execution.codexSandbox`
  - `execution.git.remotes`
  - `execution.git.refs`
  - `execution.limits.maxActiveWorkPackages`
  - `execution.limits.concurrencyLimit`
  - `execution.acceptedRisks`
- [ ] 1.4 Write the `Current Baseline` section including a fenced
  code block containing the 40-character baseline SHA
  (`e951e8877b1ed12eebf4eb992ea91623b986b05c`) plus a one-line
  summary of that commit.
- [ ] 1.5 Write the `Conventions for Future Changes` section
  stating the OpenSpec authoring, narrow-Scope-Envelope, and
  `NOTES.md` synchronisation obligations.

## 2. Format and structure verification

- [ ] 2.1 Confirm `NOTES.md` parses as valid CommonMark.
- [ ] 2.2 Confirm the five required `##`-level headings appear, in
  order, each followed by at least one non-blank body line.
- [ ] 2.3 Confirm there is exactly one `NOTES.md` and that it lives
  at the repository root (no nested copies).

## 3. Spec–artifact alignment check

- [ ] 3.1 Confirm every durable surface named in
  `## \`orca-companion.json\` Configuration` still exists in the
  on-disk `orca-companion.json`.
- [ ] 3.2 Confirm the baseline SHA recorded in `## Current Baseline`
  matches `git rev-parse HEAD`.
- [ ] 3.3 Confirm `Repository Layout` mentions every unique
  top-level path returned by
  `git ls-tree -r HEAD --name-only | awk -F/ '{print $1}' | sort -u`.

## 4. Final conformance

- [ ] 4.1 Run `openspec change validate
  e2e-loop-scope-g1-notes-basics-02a5fb74 --strict` and confirm the
  change validates cleanly.
- [ ] 4.2 Confirm no file outside the Work Package Scope Envelope
  (`NOTES.md`) has been created, modified, or deleted (compare
  `git status` against the baseline `e951e88`).
- [ ] 4.3 Confirm `openspec/specs/notes-basics/spec.md` is **not**
  committed to `openspec/specs/` — it remains inside
  `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/specs/`
  until archive.
