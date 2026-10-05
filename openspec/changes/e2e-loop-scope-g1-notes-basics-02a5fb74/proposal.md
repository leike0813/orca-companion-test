# Proposal

## Why

The repository currently ships only a one-line README and a bare OpenSpec skeleton, so a newcomer has no single place that explains what the project is, how its directories are laid out, or which commands to run. Adding a `NOTES.md` at the repository root gives contributors and agents one discoverable entry point for those basics, instead of forcing them to reconstruct the layout by browsing the tree.

## What Changes

- Add a `NOTES.md` file at the repository root that records the project overview, the repository layout, and the commands used for everyday work.
- Require the notes to stay factually accurate: every repository path they mention must exist, so the file cannot drift into describing structure that was never added or has since been removed.
- No runtime code, build configuration, or dependency changes are introduced. The change is documentation only.

## Capabilities

### New Capabilities

- `repo-notes`: The repository maintains a single root-level `NOTES.md` that documents the project overview, the repository layout, and the everyday development commands, and that stays accurate with respect to the paths it references.

### Modified Capabilities

None. The project has no existing capability specs, and this change does not alter the requirements of any existing one.

## Impact

- `NOTES.md`: new file at the repository root; this is the only path this change creates or modifies.
- No APIs, dependencies, build systems, or existing files are affected.
