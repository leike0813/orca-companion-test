# Tasks

## 1. Draft NOTES.md

- [x] 1.1 Create `NOTES.md` at the repository root with a section stating what the project is and what it is used for, and verify by reading the file back that the section is present under its own Markdown heading
- [x] 1.2 Add a section explaining what `orca-companion.json` configures (coordinator model, tracker, execution harness) and verify that every setting named in the section matches the values actually present in that file
- [x] 1.3 Add a section describing the OpenSpec planning loop (changes live in `openspec/changes/<change-name>/` with proposal, spec deltas, and tasks; a change completes when tasks are checked and it is archived) and verify the described layout against the directories that actually exist in the repository
- [x] 1.4 Add a section listing the commands a contributor needs (for example initializing or listing OpenSpec, validating a change, and viewing its status) and verify by running each listed command from the repository root that it succeeds

## 2. Constraints and final check

- [x] 2.1 Add a section recording the constraints contributors must respect (only `NOTES.md` is in scope for this change; `README.md` and `orca-companion.json` are context only) plus any open follow-up work, and verify by re-reading that both constraints and open items are stated
- [x] 2.2 Verify the whole document end to end by checking that every required section from `specs/notes-basics/spec.md` has its own heading, that no section merely restates the README blurb, and that `git status --short` shows `NOTES.md` as the only modified or added tracked-eligible file outside the `openspec/` planning directory
