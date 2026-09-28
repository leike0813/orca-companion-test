# Tasks

## 1. Author NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with a single H1 title and a
  non-empty paragraph stating what the project is; verify with
  `test -s NOTES.md && grep -c '^# ' NOTES.md` returning 1.
- [ ] 1.2 Add a `## Repository Layout` section whose body is non-empty and
  describes the root entries that actually exist; verify by resolving every
  path named in that section with `test -e` against the repository root.
- [ ] 1.3 Add a `## Verification` section describing how a reviewer checks the
  repository; verify the section body is non-empty with
  `awk '/^## Verification/{f=1;next} /^## /{f=0} f' NOTES.md | grep -q '[^[:space:]]'`.
- [ ] 1.4 Cross-reference `README.md` from `NOTES.md` and verify with
  `grep -q 'README.md' NOTES.md && test -f README.md`.

## 2. Verify the document against the specs

- [ ] 2.1 Confirm no path named in `NOTES.md` is dangling by extracting
  backticked paths and testing each with `test -e`; verify the loop exits 0
  with no failures printed.
- [ ] 2.2 Confirm every claim in `NOTES.md` matches the tree by reviewing the
  document against `ls -a` output; verify no statement describes a file,
  command, or feature absent from the repository.
- [ ] 2.3 Confirm the change stayed in scope by running `git status --porcelain`
  and verifying `NOTES.md` is the only path outside
  `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/` that is
  modified or added.
