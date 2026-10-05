# Tasks

## 1. Author NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with a level-one title followed by a
  one- or two-sentence statement naming the audience and subject, and verify with
  `head -1 NOTES.md` that the first line is a `# ` heading and that a purpose sentence
  follows it.
- [ ] 1.2 Add a `## Repository layout` section that explains what each top-level path is
  for, naming every referenced path in an inline code span, and verify by extracting the
  paths with `grep -o '`[^`]*`' NOTES.md` and confirming each extracted path exists via
  `test -e`.
- [ ] 1.3 Add a `## Local development workflow` section describing how a contributor
  works in this repository, and verify that every command it claims is runnable appears in
  an inline code span by running that command in the repository root and confirming its
  exit status is 0.
- [ ] 1.4 Add a `## Conventions` section stating the practices contributors are expected
  to follow, and verify the three required headings are all present and non-empty by
  running `grep -c '^## ' NOTES.md` for the count and inspecting each section body.

## 2. Verify the notes against the repository

- [ ] 2.1 Confirm every repository path named in `NOTES.md` still exists by running
  `grep -o '`[^`]*`' NOTES.md | tr -d '`' | while read -r p; do test -e "$p" || echo "MISSING: $p"; done`
  from the repository root and confirming it prints no `MISSING:` lines.
- [ ] 2.2 Confirm `NOTES.md` claims nothing absent from the repository by re-reading it
  end to end against the working tree, and verify the file contains no reference to a
  script, tool, or directory that is not present.
- [ ] 2.3 Confirm the delivered artifact renders as plain-text Markdown by running
  `test -f NOTES.md` and `file NOTES.md`, and verify the output identifies it as a text
  file rather than binary.
