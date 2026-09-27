# Proposal

## Why

The project root currently has only a README.md and configuration files, but it lacks a dedicated NOTES.md for capturing project-specific development notes, conventions, and open questions that do not belong in README.md. Later changes will rely on this baseline so the companion harness and contributors can find a stable, predictable place to record decisions and follow-up items.

## What Changes

- Add a new file `NOTES.md` at the project root that documents the project's development notes baseline.
- Define a minimal, predictable section structure for NOTES.md (Purpose, Conventions, Decisions, Open Questions) that downstream changes can extend.
- Establish NOTES.md as the canonical place for project-internal notes that are out of scope for README.md.

## Capabilities

### New Capabilities

- `notes-basics`: Defines the baseline content and structure of the project-root NOTES.md file, including the required section headings and the role each section plays.

### Modified Capabilities

_None._

## Impact

- Adds `NOTES.md` at the repository root.
- No code, APIs, build tooling, or external systems are affected.

