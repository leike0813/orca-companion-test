# Tasks

## 1. Author NOTES.md content

- [ ] 1.1 Create `NOTES.md` at the repository root with UTF-8 Markdown
      content whose first non-empty line is the `# Project Notes` heading.
- [ ] 1.2 Add an introductory paragraph under the heading that names the
      `orca-companion` project and points the reader to `README.md`.
- [ ] 1.3 Add a level-2 `## Upcoming` section listing at least one
      follow-up bullet describing work intended for a later change (for
      example, expanded installation or usage documentation).

## 2. Verify NOTES.md against the spec

- [ ] 2.1 Confirm `NOTES.md` is present at the repository root next to
      `README.md` and `orca-companion.json` and contains a non-empty body.
- [ ] 2.2 Confirm the first non-empty line of `NOTES.md` is the exact
      `# Project Notes` heading.
- [ ] 2.3 Confirm the `## Upcoming` section is present and contains at
      least one bullet item that does not duplicate the scope of this
      change.

## 3. Finalize the change

- [ ] 3.1 Run `openspec validate
      e2e-loop-scope-g1-notes-basics-02a5fb74` and resolve any reported
      issues before requesting archive.
- [ ] 3.2 Do **NOT** run `openspec archive` or move the change into
      `openspec/changes/archive/`; archive is owned by a later
      dispatch/finalizer step.
