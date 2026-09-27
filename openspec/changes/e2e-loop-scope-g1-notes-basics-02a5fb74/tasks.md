# Tasks

## 1. Create NOTES.md with baseline sections

- [ ] 1.1 Create the empty `NOTES.md` file at the repository root and verify `git status` shows it as a new untracked file at the root (no nested directory). [verification: `git status --porcelain` lists `NOTES.md` with no path prefix and `ls NOTES.md` exits 0]
- [ ] 1.2 Add the three required baseline headings `## Overview`, `## Conventions`, and `## Open Questions` to `NOTES.md` in that order and verify the order is preserved. [verification: `grep -n '^## ' NOTES.md` prints exactly those three headings in that order]
- [ ] 1.3 Seed each baseline section with at least one prose line and verify each section is non-empty. [verification: `awk '/^## / {section=$0; next} section && NF {count[section]++} END {for (s in count) print s, count[s]}' NOTES.md` reports a positive count for each of `## Overview`, `## Conventions`, and `## Open Questions`]
- [ ] 1.4 Ensure `NOTES.md` is plain UTF-8 Markdown with no scripts or binary content and verify by file inspection. [verification: `file NOTES.md` reports ASCII or UTF-8 text and `grep -E '<script|<\?php' NOTES.md` exits non-zero]

## 2. Stage and validate the change

- [ ] 2.1 `git add NOTES.md` and verify `git status` shows `NOTES.md` staged for commit at the repository root. [verification: `git diff --cached --name-only` prints exactly `NOTES.md`]
- [ ] 2.2 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74 --strict` from the repository root and verify it exits 0 with no findings. [verification: the command exits 0 and prints `Valid: ...` (or equivalent) without listing any failing checks]
- [ ] 2.3 Confirm the change's `## Impact` section in `proposal.md` mentions only paths inside the Work Package Scope Envelope and verify by inspection. [verification: `grep -E '^- ' proposal.md` under `## Impact` lists only `NOTES.md`]
