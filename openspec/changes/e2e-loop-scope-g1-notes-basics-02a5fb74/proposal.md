# Proposal: Project Notes Basics

## Why

The `orca-companion` repository currently ships with only a stub `README.md` whose body explicitly defers future sections ("More sections (Installation, Usage, etc.) will be added in later changes."). There is no canonical note that records what this e2e-loop demonstration is for, what its baseline scope covers, or which follow-on changes are already planned. Without that anchor, downstream Work Packages have nothing to extend and the harness cannot demonstrate a notes-driven change loop end-to-end.

This change introduces a single `NOTES.md` file that captures the demonstration purpose, baseline scope, and a forward-looking follow-ups list. It is the smallest, most defensible starting point for the e2e-loop scope test: one new file, no behavior changes, no dependency churn.

## What Changes

- Add a new top-level `NOTES.md` file documenting the project purpose, baseline scope, and planned follow-ups.
- Establish a `project-notes` capability that defines the required sections and content of `NOTES.md`.
- Do not modify `README.md`, `orca-companion.json`, or any other existing file in this Work Package.

## Capabilities

### New Capabilities

- `project-notes`: Defines the presence and required sections of the repository's `NOTES.md` so downstream changes have a stable anchor to extend.

### Modified Capabilities

None. No existing spec-level requirements change in this Work Package.

## Impact

- `NOTES.md` (new file at the repository root). This is the only path inside the Work Package Scope Envelope that this change touches.
- No APIs, dependencies, runtime services, or build tooling are affected.
- No breaking changes.
