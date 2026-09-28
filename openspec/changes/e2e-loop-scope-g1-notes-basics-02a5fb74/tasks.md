# Tasks: Notes basics

## 1. Establish NOTES.md structure

- [ ] 1.1 Create `NOTES.md` at the repository root with the three required
      level-2 headings (`## Overview`, `## Conventions`, `## Pointers`)
      in that order, and verify the file exists at exactly
      `./NOTES.md` via `ls NOTES.md` or an equivalent filesystem check.
- [ ] 1.2 Fill in the `## Overview` section so it identifies the project
      as an end-to-end loop demonstration for the orca-companion agent
      harness, and verify the section contains at least one non-blank line
      by reading the file.
- [ ] 1.3 Fill in the `## Conventions` section with the repository's
      basic contribution and naming conventions, and verify the section is
      non-empty by reading the file.
- [ ] 1.4 Fill in the `## Pointers` section so it references both
      `README.md` and `orca-companion.json` by their exact
      repository-relative paths, and verify both path references are
      present in the section.
- [ ] 1.5 Verify `NOTES.md` parses as GitHub-flavored Markdown with no
      errors and renders the three required sections as headings, using a
      Markdown parser or markdownlint to confirm (a passing run of the
      parser/linter is the acceptance evidence for this task).

## 2. Validation

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74`
      from a working OpenSpec root that points at this worktree, and
      verify the command exits with no errors and no
      `scope_envelope_exceeded` findings.
