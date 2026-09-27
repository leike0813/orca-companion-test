# Tasks

## 1. Author NOTES.md baseline

- [ ] 1.1 Create `NOTES.md` at the repository root with "Project Layout" and "Conventions" sections and verify both headings appear in the rendered Markdown file
- [ ] 1.2 Populate the "Project Layout" section with the four top-level files (`README.md`, `NOTES.md`, `orca-companion.json`, `.gitignore`) and verify each is named in the section
- [ ] 1.3 Populate the "Conventions" section with the three baseline expectations (spec-first changes, scope envelopes, public role of `README.md`) and verify each expectation is stated
- [ ] 1.4 Run `ls -la` at the repository root and verify that `NOTES.md` is the only newly added top-level file in this change

## 2. Validate change artifacts

- [ ] 2.1 Run `openspec status --change e2e-loop-scope-g1-notes-basics-02a5fb74` and verify all four artifacts (proposal, specs, design, tasks) are marked complete
- [ ] 2.2 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74` and verify the change passes without errors
