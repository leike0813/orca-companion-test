# Repository notes

These notes are written for contributors who have just joined the project: they say what
each top-level path is for, how work is done locally, and which conventions are expected.
Every statement below describes the repository as it currently stands, so anything here
that no longer matches the working tree is a defect in this file.

## Repository layout

- `README.md` - the project's front door. It currently holds the project title and little
  else, so the orientation material lives here instead.
- `NOTES.md` - this file, the single root-level entry point for contributor orientation.
- `.gitignore` - present but empty, so the repository currently ignores nothing.
- `orca-companion.json` - the Orca companion configuration. It records the provider
  connections, the selectable models, and the tracker, planning, and execution settings
  that the Orca tooling reads.
- `openspec/` - the change-management directory. `openspec/config.yaml` declares the
  project schema, `openspec/specs/` holds the accepted specifications, and
  `openspec/changes/` holds one directory per in-flight change, each carrying its own
  README, proposal, design, task list, and spec deltas. `openspec/changes/archive/` is
  where completed changes are moved.

There is no source tree, package manifest, build script, or test runner in the repository.
The tracked content is documentation and configuration only.

## Local development workflow

Because there is nothing to build and no test suite to run, the loop is: make the edit,
read the diff, commit. These commands cover it:

    git status
    git diff
    git log --oneline -10
    ls openspec/changes

Run them from the repository root. All four are plain git and shell commands; the
repository ships no wrapper scripts of its own.

Work that is driven by a spec-driven change follows the directory layout under
`openspec/changes/`. Start by reading that change's README and proposal, read the design
before implementing, work through the items in its task list, and mark each item off as it
lands. When the change is complete, move its directory into `openspec/changes/archive/`.

## Conventions

- Keep documentation grounded. Describe only paths, settings, and commands that exist in
  the working tree; do not promise a tool, script, or workflow step that is not here yet.
- Write repository paths in inline code spans. The repository has no link checker, so the
  paths in this file are verified by extracting the spans and testing each one, which only
  works if paths are always formatted as code.
- Keep one change per directory under `openspec/changes/`, with the full artifact set, so
  a reviewer can follow the reasoning from proposal to design to tasks.
- Keep commits scoped to a single change, and describe the user-visible effect in the
  commit message rather than listing files.
- If generated output ever appears in the working tree, add an ignore rule to
  `.gitignore` in the same change that introduces it; the file is empty today.
