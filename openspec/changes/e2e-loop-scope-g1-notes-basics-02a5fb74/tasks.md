# Tasks

## 1. Scaffold NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with a top-level heading naming it as
      the orca-companion notes document and a one-line intro paragraph.
- [ ] 1.2 Ensure the file is committed UTF-8 Markdown and contains no non-ASCII
      boilerplate that would break downstream tooling.

## 2. Add Project Context Section

- [ ] 2.1 Add a `## Project Context` section that names orca-companion as an e2e-loop
      demonstration project for the orca-companion agent harness.
- [ ] 2.2 Keep the section to two or three short paragraphs; defer deeper project
      background to later Work Packages.

## 3. Add Conventions Section

- [ ] 3.1 Add a `## Conventions` section that documents, in prose, the three expectations
      from the spec: edit only files inside the active Work Package scope, keep changes
      scoped to the active Work Package, and coordinate through the harness rather than
      via the Git remote.
- [ ] 3.2 Keep the section actionable: each expectation should be stated as a single
      sentence a contributor can follow without further context.

## 4. Add E2E Loop Section

- [ ] 4.1 Add an `## E2E Loop` section that names the orca-companion harness loop and
      points contributors at the `openspec/changes/` directory for active change
      artifacts.
- [ ] 4.2 Keep the section short; do not duplicate information that lives in
      `openspec/config.yaml` or `orca-companion.json`.

## 5. Verify Against Spec

- [ ] 5.1 Read the resulting `NOTES.md` end-to-end and confirm the four spec scenarios
      (file exists, Project Context present, Conventions present, E2E Loop present) all
      hold.
- [ ] 5.2 Run `openspec validate --change e2e-loop-scope-g1-notes-basics-02a5fb74`
      and confirm no diagnostics.
