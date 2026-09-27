# Proposal

## Why

The `orca-companion` repository currently has no internal developer-facing notes document. `README.md` describes the public purpose of the project, but there is no canonical place to record the baseline layout, shared conventions, or follow-up items that downstream changes rely on. Adding `NOTES.md` gives the Orca harness a concrete file to validate against the `notes-basics` scope envelope and gives future changes a stable anchor to extend.

## What Changes

Add `NOTES.md` at the repository root as the project's first baseline developer-notes document. The file is plain Markdown and contains a "Project Layout" section listing the top-level files with their roles plus a "Conventions" section describing the baseline expectations for downstream changes. No other files are added, modified, or removed.

## Capabilities

### New Capabilities

- `notes-basics`: Defines the structure and required sections of the initial `NOTES.md` so future changes have a stable baseline to extend.

### Modified Capabilities

None.

## Impact

- `NOTES.md` (new file, repository root)
