# Tasks

## 1. NOTES.md Baseline

- [ ] 1.1 Create `NOTES.md` at the repository root with the three required level-2 sections (`Current State`, `Decisions`, `Open Questions`) in order, each followed by a short placeholder paragraph, and verify `git status` shows the new file at the repo root.
- [ ] 1.2 Confirm `NOTES.md` is plain Markdown with no fenced code blocks, inline `<script>`, or `<form>` elements, and verify the check by grepping for ```` ``` ````, `<script`, and `<form`.
- [ ] 1.3 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74 --strict` and verify the change passes without errors.

## 2. Scope Guard

- [ ] 2.1 Verify the change does not add, modify, or delete any file outside the Work Package Scope Envelope (`NOTES.md` only) by running `git status --porcelain` and verifying the listed path is exactly `NOTES.md`.
