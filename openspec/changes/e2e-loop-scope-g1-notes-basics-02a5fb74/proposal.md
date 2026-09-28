# Proposal

## Why

The `orca-companion` baseline currently exposes a README that openly promises
"_More sections (Installation, Usage, etc.) will be added in later changes._"
but no companion `NOTES.md` exists to capture the lightweight project notes
that downstream work packages will reference. Without a canonical notes file,
future specs have nowhere to anchor ad-hoc project knowledge (release
checklists, demo scripts, contributor pointers) inside the work-package scope
envelope, so this change introduces the first, deliberately minimal version
of that file.

## What Changes

- Add a new `NOTES.md` at the repository root containing the initial
  "Project Notes" content: a short overview, a placeholder section for
  upcoming release notes, and a pointer to `README.md`.
- Declare a new `notes-basics` capability describing what `NOTES.md` must
  contain when this change ships.
- No other files are added, renamed, or modified by this change.

## Capabilities

### New Capabilities

- `notes-basics`: Initial structural requirements for the repository's
  `NOTES.md`, including required top-level sections and the minimum content
  the file must carry on first introduction.

### Modified Capabilities

None. No existing capability's requirements are changing.

## Impact

- `NOTES.md` (new file): introduces the initial project notes document at the
  repository root.
