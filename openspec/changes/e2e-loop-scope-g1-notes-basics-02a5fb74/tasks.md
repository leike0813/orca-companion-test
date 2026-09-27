# Tasks

## 1. Author the change proposal and spec delta

- [ ] 1.1 Draft `proposal.md` describing the motivation, the new `notes` capability, and an `## Impact` section that names only `NOTES.md` (in-scope per the work package scope envelope).
- [ ] 1.2 Author `specs/notes/spec.md` with the six `ADDED Requirements` covering existence, canonical sections, e2e-loop narrative, cross-references, scope-envelope enforcement, and Markdown well-formedness.
- [ ] 1.3 Confirm `proposal.md` `## Impact` lists only paths inside `scopeEnvelope.include` (`["NOTES.md"]`) so Admission does not reject the change for `scope_envelope_exceeded`.

## 2. Define the implementation tasks for the implementation worker

- [ ] 2.1 Create `NOTES.md` at the repository root with the six canonical sections in the declared order: Project Overview, Repository Layout, Running the e2e Loop, Conventions, Troubleshooting, Future Work.
- [ ] 2.2 Populate each canonical section with at least one paragraph or list, cross-reference `openspec/`, `orca-companion.json`, and `README.md`, and describe how `orca orchestration send --type worker_done` reports completion.
- [ ] 2.3 Commit `NOTES.md` with a message that names the change id `e2e-loop-scope-g1-notes-basics-02a5fb74` so future archaeology can link the file back to this change.

## 3. Define the validator task

- [ ] 3.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74 --strict` and confirm the proposal, spec delta, and tasks pass without errors.
- [ ] 3.2 After implementation, verify `NOTES.md` exists at the worktree root, contains the six canonical `##` headings in order, has no empty canonical sections, and stays within the work package scope envelope.
- [ ] 3.3 Re-run `openspec validate` on the change after implementation to ensure no spec drift was introduced.

## 4. Define the finalizer task

- [ ] 4.1 Verify the worktree contains the new `NOTES.md` and the `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/` directory tree with `proposal.md`, `specs/notes/spec.md`, and `tasks.md`.
- [ ] 4.2 Hand off to the change archive step (executed by a separate dispatch); this dispatch does NOT run `openspec archive` or move the change into `archive/`.
