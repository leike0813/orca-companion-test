# Tasks

## 1. Author the notes document

- [ ] 1.1 Create `NOTES.md` at the repository root with a `#` title heading and a short purpose paragraph stating what the notes cover. Verify with `head -20 NOTES.md` that both the heading and the paragraph are present.
- [ ] 1.2 Add a numbered list of notes to `NOTES.md`, where every entry describes something observable in the repository and no entry names a dependency, script, or command the project does not implement. Verify by reading each entry and confirming the referenced file or convention exists in the repository.
- [ ] 1.3 Close `NOTES.md` with a line naming `README.md` as the place holding the project background. Verify with `grep -n 'README.md' NOTES.md` that the reference is present.

## 2. Verify the change against its scope

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74 --strict` and confirm it reports the change as valid. Verify by the command exiting with a success message.
- [ ] 2.2 Confirm the change touched no file outside the scope envelope. Verify with `git status --porcelain` that `NOTES.md` is the only added or modified tracked file.
