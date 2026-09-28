# Tasks

## 1. Draft NOTES.md content

- [ ] 1.1 Write the introductory paragraph that names the project and its
  purpose, citing `README.md` as the authoritative entry point.
- [ ] 1.2 Write a `Purpose` section summarizing what the project is for.
- [ ] 1.3 Write a `Conventions` section listing basic contribution conventions
  (propose changes via OpenSpec, keep documentation in plain Markdown, and
  do not edit archived changes).
- [ ] 1.4 Write a `Scope` section that names the in-scope artifact for this
  change (`NOTES.md`) and points readers to `README.md` for installation,
  usage, and other deferred sections.
- [ ] 1.5 Save the draft as `NOTES.md` at the repository root using UTF-8
  encoding and a trailing newline.

## 2. Verify NOTES.md against the spec

- [ ] 2.1 Confirm `NOTES.md` exists at the repository root and is a regular
  file.
- [ ] 2.2 Confirm the file is valid UTF-8 and parses as Markdown.
- [ ] 2.3 Confirm the `Purpose`, `Conventions`, and `Scope` sections are
  present with the required content from task 1.
- [ ] 2.4 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74` (or
  equivalent) and resolve any reported findings before handoff.

## 3. Stage and hand off the change

- [ ] 3.1 Confirm `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/`
  contains `.openspec.yaml`, `proposal.md`, `tasks.md`, and
  `specs/notes-basics/spec.md`.
- [ ] 3.2 Confirm `git status` reports the new `NOTES.md` and the new change
  directory as the only modifications relative to the baseline head
  `b0200dfcc5bdd52450c7f941691a6ac3c7e35364`.
- [ ] 3.3 Leave the change unarchived and in
  `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/` for the
  validator and finalizer.
