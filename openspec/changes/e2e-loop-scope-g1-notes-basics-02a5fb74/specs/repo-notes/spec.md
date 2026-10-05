## Purpose

Define the contract for the repository's root `NOTES.md` file, so that contributors and agents can
find the project's basic working conventions in one checked-in place.

## ADDED Requirements

### Requirement: Root notes file exists

The repository MUST contain a `NOTES.md` file at its root, written in plain Markdown, and that file
MUST be committed alongside the rest of the project content.

#### Scenario: Notes file is present in a fresh checkout

- **WHEN** a contributor or agent lists the repository root on a fresh checkout
- **THEN** a `NOTES.md` file is listed alongside the other tracked files

### Requirement: Notes cover the project's working basics

`NOTES.md` MUST state, in at most a few short sections, what the repository contains, that the
project is spec-driven through OpenSpec, and the conventions a change is expected to follow. Each
statement MUST be verifiable against the repository as it exists.

#### Scenario: A reader can find the change workflow

- **WHEN** a first-time reader opens `NOTES.md` to learn how changes are made here
- **THEN** the file states that changes are specified as OpenSpec changes under `openspec/changes/`
  before any work is applied

#### Scenario: A reader can find the scope convention

- **WHEN** a first-time reader looks for the rule that limits which files a change may touch
- **THEN** `NOTES.md` states that a change only edits the paths inside its declared scope

### Requirement: Notes stay accurate and minimal

`NOTES.md` MUST stay a short prose document: it MUST NOT embed generated OpenSpec output, task
checklists, or per-change planning detail, and it MUST be updated in the same change as any
convention it describes is introduced or removed.

#### Scenario: No planning artifacts are copied in

- **WHEN** a reviewer diffs `NOTES.md` against the OpenSpec change that introduced it
- **THEN** `NOTES.md` contains conventions only, with no proposal, spec, or task content copied from
  the change directory

#### Scenario: Convention changes are reflected

- **WHEN** a later change introduces or removes a convention that `NOTES.md` describes
- **THEN** that change updates `NOTES.md` in the same commit as the convention itself
