# Proposal

## Why

The repository currently has only `README.md` to describe the project, and that file explicitly defers the next sections ("Installation, Usage, etc.") to future changes. We need a complementary `NOTES.md` file as the foundation for project-level engineering notes (release notes, design decisions, and follow-up tasks) so that downstream changes can build on a consistent baseline without re-inventing the structure each time.

## What Changes

- Introduce a `NOTES.md` file at the repository root that hosts three top-level sections: **Release Notes**, **Design Decisions**, and **Follow-ups**.
- Define a stable, observable layout for `NOTES.md` (section ordering, section headings, and the requirement that each entry under the sections be a dated bullet) so subsequent changes can extend it without ambiguity.
- Require the file to exist at the repository root and to be non-empty once this change is applied.

## Capabilities

### New Capabilities
- `project-notes`: Defines the contract for the repository's `NOTES.md` engineering notes file — its location, required top-level sections, and the shape of entries under each section.

### Modified Capabilities
- _None._ This change introduces a new capability and does not modify any existing spec.

## Impact

The only path touched by this change is `NOTES.md` (created at the repository root). No existing source files, APIs, dependencies, or systems outside the Scope Envelope are affected.
