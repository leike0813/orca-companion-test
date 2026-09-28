# Tasks

## 1. Draft NOTES Basics Content

- [ ] 1.1 Draft the H1 heading and an introductory body under `# Notes`
  and confirm the heading is the first non-blank line of the file and
  that the body introduces the file's purpose in plain English (verify
  by reading the draft against proposal.md and the `Notes Heading`
  requirement).
- [ ] 1.2 Draft the H2 section topics and bodies and confirm each H2
  section has a plain-English heading and at least one sentence of body
  content, and that no `TODO`, `TBD`, `<placeholder>`, or
  `lorem ipsum` markers appear anywhere in the draft (verify by reading
  the draft against design.md and the `Topic Sections` and `No
  Placeholder Or TODO Content` requirements).

## 2. Create NOTES.md

- [ ] 2.1 Create `NOTES.md` at the repository root with the drafted
  content so the line `# Notes` is the first non-blank line and at
  least one H2 section follows with body content (verify by reading
  `NOTES.md` and confirming it satisfies the `Notes Heading` and
  `Topic Sections` requirements).
- [ ] 2.2 Confirm `NOTES.md` parses as valid CommonMark, contains
  exactly one H1 heading, contains no `TODO` / `TBD` /
  `<placeholder>` / `lorem ipsum` markers, and ends with exactly one
  trailing newline character (verify with a CommonMark-aware linter
  or by manual inspection of heading lines and the file's final bytes
  against the `Markdown Well-Formedness` requirement).

## 3. Verify Spec Conformance

- [ ] 3.1 Re-read `NOTES.md` against each `#### Scenario:` block in
  `specs/notes-basics/spec.md` and confirm the file passes every
  scenario (verify by walking through each scenario and recording
  pass/fail).
- [ ] 3.2 Run `git status --porcelain` from the repository root and
  confirm the only modified or untracked path is `NOTES.md` plus this
  change directory `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/`
  (verify by matching the output to the Work Package Scope Envelope,
  which is exactly `["NOTES.md"]`).
