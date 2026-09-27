# Tasks

## 1. Create NOTES.md with the required sections

- [ ] 1.1 Create the repository-root file `NOTES.md` and verify it opens with a level-1 Markdown title by inspecting the first non-blank line of the file
- [ ] 1.2 Add the four required level-2 sections (`Overview`, `Conventions`, `Pointers`, `Open Questions`) to `NOTES.md` in the required order and verify by listing the `##` headings of the file
- [ ] 1.3 Add at least one paragraph of content under each required section and verify by counting the non-empty paragraphs in `NOTES.md`

## 2. Verify NOTES.md satisfies the spec

- [ ] 2.1 Run `git check-ignore NOTES.md` and verify it exits non-zero (the file is not gitignored) and that `git ls-files --error-unmatch NOTES.md` exits zero (the file is tracked)
- [ ] 2.2 Compare `NOTES.md` against `README.md` and verify no sentence appears verbatim in both files
- [ ] 2.3 Verify `NOTES.md` contains no step-by-step installation or usage instructions by reading the file end-to-end

## 3. Confirm the change matches the Work Package Scope Envelope

- [ ] 3.1 Run `git status --porcelain` and verify the only added file is `NOTES.md` (no other files added, removed, renamed, or modified)
- [ ] 3.2 Verify the change's `proposal.md` `## Impact` section references only `NOTES.md` and no paths outside the Work Package Scope Envelope
