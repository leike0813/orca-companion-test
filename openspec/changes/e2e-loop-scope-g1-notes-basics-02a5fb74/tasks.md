# Tasks

## 1. Author the baseline NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with a `## Project Purpose` section and a `## Current Status` section, then verify the file is present at the repo root via `git status` / `ls NOTES.md`.
- [ ] 1.2 Ensure neither section is a verbatim copy of any paragraph already in `README.md`, then verify by reading both files and confirming the wording differs.

## 2. Validate the change

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74` and verify it exits with no validation errors.
- [ ] 2.2 Run `openspec status --change e2e-loop-scope-g1-notes-basics-02a5fb74` and verify all four artifacts (proposal, specs, design, tasks) report complete.
