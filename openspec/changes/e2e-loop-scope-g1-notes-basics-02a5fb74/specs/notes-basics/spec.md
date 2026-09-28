# Spec Delta: notes-basics

## Purpose

Provides the foundational `NOTES.md` document for the orca-companion demo project so that
contributors and downstream Work Packages have a stable place to read project context,
contributor conventions, and a short e2e-loop note.

## ADDED Requirements

### Requirement: Project Notes Document Exists

A `NOTES.md` file MUST exist at the repository root and be a UTF-8 encoded Markdown
document. The file MUST be readable as plain text and MUST not be empty.

#### Scenario: Repository root NOTES.md exists

- **WHEN** a contributor lists the files in the repository root
- **THEN** `NOTES.md` is present as a regular file with non-zero size

### Requirement: Notes Include Project Context

`NOTES.md` MUST contain a `## Project Context` section that briefly explains what
orca-companion is and that the repository serves as an end-to-end demonstration project for
the orca-companion agent harness.

#### Scenario: Project Context section is present

- **WHEN** a contributor reads `NOTES.md`
- **THEN** a `## Project Context` heading is present and the section names orca-companion
  as an e2e-loop demonstration project

### Requirement: Notes Include Contributor Conventions

`NOTES.md` MUST contain a `## Conventions` section that states, in prose, the basic
expectations for contributors: edit files in scope, keep changes scoped to the active Work
Package, and coordinate through the harness rather than the Git remote.

#### Scenario: Conventions section is present

- **WHEN** a contributor reads `NOTES.md`
- **THEN** a `## Conventions` heading is present and the section names at least the
  edit-in-scope, stay-in-scope, and coordinate-through-harness expectations

### Requirement: Notes Include E2E Loop Note

`NOTES.md` MUST contain an `## E2E Loop` section that briefly describes how this repository
is exercised through the orca-companion agent harness end-to-end loop and that the active
change artifacts live under `openspec/changes/`.

#### Scenario: E2E Loop section is present

- **WHEN** a contributor reads `NOTES.md`
- **THEN** an `## E2E Loop` heading is present and the section references the
  orca-companion harness loop and the `openspec/changes/` directory
