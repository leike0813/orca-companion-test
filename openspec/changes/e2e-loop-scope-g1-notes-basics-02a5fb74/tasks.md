# Tasks

## 1. Author NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with the four required H2 sections (`Purpose`, `Conventions`, `Decisions`, `Open Questions`) in order and at least one sentence of body content under each, and verify the file exists at `./NOTES.md` and is UTF-8 encoded Markdown.
- [ ] 1.2 Keep each section body short (one or two sentences) and avoid duplicating any user-facing material already covered by `README.md`, and verify by re-reading the produced `NOTES.md` and confirming no README.md-only content (project description, installation steps, usage examples) is reproduced.

## 2. Verify Spec Compliance

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74` from the worktree root and verify the command exits successfully with no validation errors against the proposal, design, specs, and tasks artifacts.
- [ ] 2.2 Spot-check the produced `NOTES.md` against the four requirements in `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/specs/notes-basics/spec.md` and verify every requirement's WHEN/THEN scenarios are satisfied (file at root, sections in order, each non-empty, level-two headings, role separation from README.md).

