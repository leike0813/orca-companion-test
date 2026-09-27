# Proposal

## Why

The orca-companion repository ships as the baseline for the e2e-loop demonstration project, but it has no dedicated notes file capturing the project's identity, purpose, and the placeholder scope that future changes will fill in. Without a NOTES.md, downstream readers and follow-up changes lack a single canonical place to record project-level notes, leading to ad-hoc placement in README or scattered comments.

## What Changes

- Add a new top-level `NOTES.md` file at the repository root that records the project name, purpose statement, and placeholder sections reserved for future expansions (Installation, Usage, and similar follow-up topics).
- Define the `notes-basics` capability that governs the existence and minimal structural contract of `NOTES.md`, so future changes have a stable spec target when they extend or amend the file.

## Capabilities

### New Capabilities

- `notes-basics`: Defines the baseline `NOTES.md` artifact at the repository root, including the required headings for project identity, purpose, and reserved future sections, plus the Markdown validity contract.

### Modified Capabilities

_None — no existing capability has its requirements changed._

## Impact

- Creates `NOTES.md` at the repository root (within the work-package scope envelope).
- No other files in the work-package scope envelope are modified.
