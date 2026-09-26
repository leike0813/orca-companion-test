# Proposal: Add a basic NOTES.md

## Why

The repository currently exposes only a placeholder README and the orca-companion.json harness configuration. There is no canonical, in-repo location for contributors to record day-to-day observations, handoff context, or scratchpad items that should survive between work packages. Without a dedicated `NOTES.md`, project notes either live in out-of-tree scratch files or get lost, which makes it harder for downstream work packages in the e2e-loop scope to share context.

This change introduces a single `NOTES.md` file at the repository root that establishes the conventions and required sections every contributor must populate. It is intentionally narrow: it sets up the document structure and baseline content only, so later work packages can build on it without expanding scope.

## What Changes

- Add a new `NOTES.md` at the repository root with three top-level sections: `## Overview`, `## Conventions`, and `## Open Items`.
- `## Overview` records the project's purpose in two or three sentences so future readers do not need to re-read the README.
- `## Conventions` documents the minimum note-taking conventions (entry format, dated headings, Markdown only) that subsequent work packages inherit.
- `## Open Items` starts with a single placeholder bullet explaining how new items should be appended, so the file remains useful even before any real items are logged.
- No other files are created, modified, or removed. No tooling, CI, or configuration is added.
- No breaking changes.

## Capabilities

### New Capabilities

- `project-notes`: Defines the structure and minimum content of the root-level `NOTES.md` so every contributor follows the same conventions when logging project notes.

### Modified Capabilities

None. This change introduces a brand-new capability; no existing spec requirements change.

## Impact

- Adds a new tracked file: `NOTES.md` (at the repository root).
- No existing tracked files are modified.
- No public APIs, dependencies, configuration files, build steps, or external systems are affected.
- This change is scoped exclusively to the `NOTES.md` path declared in the work-package scope envelope.
