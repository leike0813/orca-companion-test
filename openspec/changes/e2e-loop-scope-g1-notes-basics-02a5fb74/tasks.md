# Tasks

## 1. Create NOTES.md at the repository root

- [ ] 1.1 Create `NOTES.md` at the repository root with the `# Notes` heading and an
      introductory paragraph and verify the file is present next to `README.md`
      and `orca-companion.json` (`ls -1` shows `NOTES.md` in the output).

- [ ] 1.2 Add the `## Project Context`, `## Conventions`, and `## Work Package Notes`
      sections in that order with at least one paragraph of content under each
      and verify the section order by grepping for the three `## ` headings in
      `NOTES.md` and confirming they appear in the documented sequence.

## 2. Verify the change satisfies the project-notes spec

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74` and
      verify the change passes validation with no errors.

- [ ] 2.2 Run `openspec show e2e-loop-scope-g1-notes-basics-02a5fb74 --type change`
      and verify the rendered change lists the `project-notes` capability under
      `Capabilities → New Capabilities`.

- [ ] 2.3 Confirm the only path referenced in `proposal.md → Impact` is
      `NOTES.md` and verify it by grepping for backtick-wrapped paths in that
      section.
