# Tasks

## 1. Author NOTES.md

- [ ] 1.1 Draft `NOTES.md` at the repository root with a short title and
      prose sections covering the repository purpose, the role of
      `orca-companion.json`, and pointers to `README.md` and the
      `openspec/` workflow. Verify the file is non-empty and uses
      plain Markdown headings (no executable code blocks beyond optional
      fenced examples).
- [ ] 1.2 Confirm the resulting `NOTES.md` satisfies every scenario in
      `specs/notes-basics/spec.md`. Verify by re-reading the spec and
      checking each `#### Scenario:` clause against the rendered file
      content, and by running `git status` to confirm only `NOTES.md`
      was added at the repository root.

## 2. Validate the Change

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74`
      and verify the command exits successfully with no validation
      errors against the change directory.
- [ ] 2.2 Run `openspec show e2e-loop-scope-g1-notes-basics-02a5fb74
      --type change --json` and verify the parsed change lists one
      ADDED capability (`notes-basics`) and reports a passing
      validation summary.
