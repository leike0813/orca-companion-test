# Tasks

## 1. Author NOTES.md

- [x] 1.1 Create `NOTES.md` at the repository root with `# Purpose`, `# Baseline Scope`, and `# Follow-ups` sections and verify the file exists at the root with non-empty content via `ls NOTES.md && wc -c NOTES.md`.
- [x] 1.2 Confirm the Baseline Scope section names only files present at the baseline commit (`README.md`, `NOTES.md`, `orca-companion.json`) by re-reading the section and cross-checking each path with `ls <path>`.

## 2. Verify NOTES.md against the project-notes spec

- [x] 2.1 Verify the three top-level headings appear in the order Purpose / Baseline Scope / Follow-ups by running `grep -nE '^# (Purpose|Baseline Scope|Follow-ups)$' NOTES.md` and confirming exactly three matches in that order.
- [x] 2.2 Verify the Follow-ups section contains at least one bullet whose text starts with a verb by running `awk '/^# Follow-ups$/,/^$/' NOTES.md | grep -E '^- '` and visually checking the first word of each bullet.
- [x] 2.3 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74 --strict` and confirm it exits 0 with no reported errors.
