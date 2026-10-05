# Tasks

## 1. Write the notes document

- [ ] 1.1 Create `NOTES.md` at the repository root with an `## Overview` section stating in prose what the project is, and verify the file exists at the root and is non-empty with `test -s NOTES.md`
- [ ] 1.2 Add a `## Repository Layout` section describing each top-level directory and what it holds, and verify every backticked path in the section resolves with `for p in $(grep -oE '`[A-Za-z0-9._/-]+/`' NOTES.md | tr -d '`' | grep '/'); do test -e "$p" || { echo "missing: $p"; exit 1; }; done`
- [ ] 1.3 Add a `## Commands` section listing the OpenSpec commands for listing changes, listing specs, and validating a change, each in a fenced `sh` block, and verify every command is runnable as written by executing the validate command from the repository root and confirming it exits 0

## 2. Verify the document against the spec

- [ ] 2.1 Run the acceptance check over `NOTES.md` - `test -s NOTES.md && for h in 'Overview' 'Repository Layout' 'Commands'; do grep -q "^## $h" NOTES.md || { echo "missing heading: $h"; exit 1; }; done && for p in $(grep -oE '`[A-Za-z0-9._/-]+/`' NOTES.md | tr -d '`' | grep '/'); do test -e "$p" || { echo "missing path: $p"; exit 1; }; done` - and confirm it exits 0, covering the root notes file, documented basics, and referenced-path accuracy requirements
- [ ] 2.2 Confirm `git status --short` reports `NOTES.md` as the only added or modified path, verifying the change stayed within the work package scope envelope
