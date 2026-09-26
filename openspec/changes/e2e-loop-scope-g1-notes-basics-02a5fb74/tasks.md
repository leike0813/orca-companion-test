# Tasks

## 1. Author the NOTES.md baseline

- [ ] 1.1 Create `NOTES.md` at the repository root containing the three required top-level sections (`## Overview`, `## Conventions`, `## Open Items`) and verify the file appears in `git status` after `git add NOTES.md`.
- [ ] 1.2 Populate `## Overview` with a two-to-three sentence summary of the orca-companion project and verify a fresh reader can state the purpose after reading only that section.
- [ ] 1.3 Populate `## Conventions` with the dated-heading entry format, the Markdown-only content rule, and the append-at-end rule and verify each rule is mentioned at least once.
- [ ] 1.4 Populate `## Open Items` with a single placeholder bullet that explains how new items should be appended and verify the section still reads as useful even with no real items.

## 2. Verify NOTES.md against the spec

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74 --strict` and verify the change passes with no deltas, schema, or required-section errors.
- [ ] 2.2 Run `wc -l NOTES.md` and verify the line count is at most 200 to satisfy the content-stability requirement.
- [ ] 2.3 Grep `NOTES.md` for secret markers and HTML tags and verify no matches are found, satisfying the content-stability and formatting requirements.
- [ ] 2.4 Confirm the change does not modify any file other than `NOTES.md` by running `git status --porcelain` and verifying the only added entry is `NOTES.md`.
