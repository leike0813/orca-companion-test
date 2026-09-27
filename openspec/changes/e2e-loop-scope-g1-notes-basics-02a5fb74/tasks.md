# Tasks

## 1. Author NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with top-level headings for project identity (`orca-companion`), `Purpose`, `Installation`, and `Usage`, with the two latter sections containing explicit placeholder copy, and verify the file exists at the root and opens as valid UTF-8 Markdown with no skipped heading levels.
- [ ] 1.2 Confirm `NOTES.md` content against every scenario in `specs/notes-basics/spec.md` and verify the file is parseable as Markdown and lists exactly the required `#` headings in the required order.

## 2. Verify the change set

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74 --strict` (or the equivalent `openspec validate` invocation recognized by the harness) and verify it exits with a clean status, confirming the proposal, specs, design, and tasks artifacts are coherent.
- [ ] 2.2 Run `git status` inside the worktree and verify that the only modified/added tracked path under the work-package scope envelope is `NOTES.md` (plus the OpenSpec change files under `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/`).
