# Tasks

## 1. Write the notes file

- [ ] 1.1 Create `NOTES.md` at the repository root with sections for repository layout, the OpenSpec
  change flow (`openspec/changes/` holds one directory per change, each with `proposal.md`, specs,
  and `tasks.md`), and the scope convention that a change only edits the paths it declares.
  Verify: `NOTES.md` exists at the repository root, and each of the three topics above appears as a
  heading with at least one sentence under it.
- [ ] 1.2 Re-read `NOTES.md` top to bottom and delete anything that cannot be checked against the
  current tree (no roadmap items, no copied proposal/spec/task text, no invented tooling). Verify:
  a review pass finds every remaining statement traceable to a path that exists at this commit.

## 2. Verify the delivered file

- [ ] 2.1 Confirm the whole change touched only `NOTES.md` and that the file renders as plain
  Markdown with no broken links or empty sections. Verify: `git status --short` lists only
  `NOTES.md` among tracked source paths, and every relative path mentioned inside the file resolves
  in the repository.
