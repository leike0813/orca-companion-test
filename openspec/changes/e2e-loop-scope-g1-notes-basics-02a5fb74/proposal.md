# Proposal

## Why

The orca-companion project ships a README.md that explicitly defers any
non-summary documentation ("More sections (Installation, Usage, etc.) will be
added in later changes."). Contributors and downstream agents still need a
project-root location to record evolving context such as conventions,
in-progress decisions, and pointers that do not belong on the README. Without a
dedicated file, that context ends up scattered across commits, chat transcripts,
or other untracked locations, and is easy to lose when a worktree is torn down.

This change introduces a minimal NOTES.md at the repository root that fills
that gap. It defines the existence and baseline structure of the file only;
later generations in the e2e-loop-scope graph will fill in its concrete
sections (Installation, Usage, Conventions, etc.). Keeping this Work Package
strictly to "notes basics" makes the e2e-loop graph's first generation reviewable
in isolation and gives later generations a stable target to extend.

## What Changes

- Add a new file NOTES.md at the repository root.
- NOTES.md MUST begin with a top-level heading that identifies it as the
  project's notes file.
- NOTES.md MUST contain a ## Purpose section that explains the role of the
  file for the orca-companion project.
- NOTES.md MAY contain additional empty or stub sections (## Conventions,
  ## Status, etc.) so that later Work Packages in the e2e-loop-scope graph
  can populate them without having to re-edit the file's outline.
- No other files in the repository are added, renamed, or removed by this
  change.

## Capabilities

### New Capabilities
- project-notes: Establishes the existence and minimal, stable structure of a
  project-root NOTES.md file so that later Work Packages can fill in concrete
  sections without redefining the file itself.

### Modified Capabilities
None.

## Impact

- NOTES.md (new file at the repository root; first tracked content for this
  path).

