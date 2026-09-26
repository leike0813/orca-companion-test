# Tasks

## 1. Author NOTES.md baseline content

- [ ] 1.1 Create `NOTES.md` at the repository root with the three required sections (`## Release Notes`, `## Design Decisions`, `## Follow-ups`) and seed each section with at least one entry that matches the spec's entry-shape requirement, then verify by opening the file and confirming the headings appear in order and each section is non-empty.

## 2. Verify the change

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74` and verify the output reports no findings (warnings or errors).
- [ ] 2.2 Run `openspec show e2e-loop-scope-g1-notes-basics-02a5fb74 --json` and verify the response lists exactly one capability (`project-notes`) under `newCapabilities` and reports no `modifiedCapabilities`.
