# Tasks

## 1. Author NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with the three required
      level-2 headings `## Scope`, `## Intent`, `## Conventions` in that
      order, each followed by real prose (not placeholder text), and verify
      with `test -f NOTES.md && [ "$(wc -c < NOTES.md)" -ge 64 ]` that the
      file exists and is at least 64 bytes.
- [ ] 1.2 Add a Markdown link from `NOTES.md` to `README.md` using the
      relative target `README.md`, and verify with
      `grep -E "\]\(README\.md\)" NOTES.md` that the link is present.
- [ ] 1.3 Ensure no prose block in `NOTES.md` is a byte-for-byte copy of
      any prose block in `README.md`, and verify by diffing the prose
      sections of both files and confirming `diff NOTES.md README.md`
      reports differences in the comparison surfaces.

## 2. Verify the change against its spec

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74
      --strict --json` and verify the response reports zero validation
      errors for the `notes-basics` capability and zero violations of
      the Impact scope envelope.
- [ ] 2.2 Run `openspec status e2e-loop-scope-g1-notes-basics-02a5fb74
      --json` and verify every required artifact (`proposal`, `specs`,
      `design`, `tasks`) is reported as `done`.
