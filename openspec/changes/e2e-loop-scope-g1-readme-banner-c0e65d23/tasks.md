# Tasks

## 1. Rewrite README.md as a banner-style front page

- [ ] 1.1 Replace the body of `README.md` so it begins with the existing `# orca-companion` title and the existing lead description sentence "An e2e-loop demonstration project for the orca-companion agent harness." and verify both appear in the first four lines of the file.
- [ ] 1.2 Add a `## Status` section immediately after the lead description that contains a paragraph explicitly stating the project is an end-to-end demonstration of the orca-companion agent harness and is not a production-ready release, and verify no other level-2 heading appears before it.
- [ ] 1.3 Add a `## Quick Links` section after `## Status` that contains exactly three bullets linking, in order, to `NOTES.md`, `openspec/`, and `orca-companion.json`, and verify each bullet includes a short label describing what the reader will find there.
- [ ] 1.4 Add a `## Project Status` section after `## Quick Links` that states deeper sections such as Installation, Usage, and Configuration will be added in later changes, and verify the previous placeholder italic sentence ("_More sections (Installation, Usage, etc.) will be added in later changes._") no longer appears in the file.

## 2. Verify README.md against the spec

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-readme-banner-c0e65d23 --strict` and verify the change passes with no deltas, schema, or required-section errors.
- [ ] 2.2 Run `wc -l README.md` and verify the line count is at most 200 to satisfy the formatting and content rules requirement.
- [ ] 2.3 Grep `README.md` for `<script`, `<iframe`, and other raw HTML tags and verify no matches are found, satisfying the formatting and content rules requirement.
- [ ] 2.4 Run `git status --porcelain` and verify the only entry is `README.md`, confirming the scope discipline requirement that no other tracked file is created, modified, or removed.
- [ ] 2.5 Run `git diff NOTES.md openspec/config.yaml orca-companion.json` and verify the command reports no changes, confirming that referenced files are described in `README.md` but not modified.
