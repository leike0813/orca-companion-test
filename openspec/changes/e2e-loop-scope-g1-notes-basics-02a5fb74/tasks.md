# Tasks

## 1. Notes File

- [x] 1.1 Create NOTES.md at the repository root with a top-level heading and the second-level sections Purpose, Requirements, Getting Started, Repository Layout, and OpenSpec Workflow, in that order; verify with `grep -n '^## ' NOTES.md` that the five sections appear in the specified order
- [x] 1.2 Fill every section with real content about this repository and verify with `awk` that no section between headings is blank
- [x] 1.3 Verify the file is free of unresolved placeholders and names no nonexistent path by running `! grep -nE 'TODO|TBD' NOTES.md` and confirming each path mentioned resolves on disk

## 2. Documentation Verification

- [x] 2.1 Confirm NOTES.md is tracked by version control and that the notes render as plain Markdown by running `git status --porcelain NOTES.md` and checking every heading is ATX-style and no deeper than level three
- [x] 2.2 Cross-read NOTES.md against README.md and confirm the two files do not contradict each other and that README remains the short project blurb
