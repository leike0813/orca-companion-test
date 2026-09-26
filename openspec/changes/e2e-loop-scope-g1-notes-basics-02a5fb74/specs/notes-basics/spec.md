# Spec Delta

## Purpose

Provides a baseline `NOTES.md` at the repository root that captures the
`orca-companion` project's purpose and current status in a format later
changes can extend.

## ADDED Requirements

### Requirement: Repository ships a baseline NOTES.md

The repository SHALL contain a `NOTES.md` file at the repository root that
documents the project's purpose and current status.

#### Scenario: NOTES.md exists at the repository root

- **WHEN** a reviewer lists the repository's top-level Markdown files
- **THEN** `NOTES.md` is present alongside `README.md`

### Requirement: NOTES.md includes a Project Purpose section

`NOTES.md` MUST contain a section titled `## Project Purpose` that
describes, in at least one sentence, why the project exists.

#### Scenario: Project Purpose section is present

- **WHEN** a reader opens `NOTES.md`
- **THEN** a `## Project Purpose` heading appears and the section that
  follows it explains the project's reason for existing

### Requirement: NOTES.md includes a Current Status section

`NOTES.md` MUST contain a section titled `## Current Status` that states,
in at least one sentence, the present state of the project.

#### Scenario: Current Status section is present

- **WHEN** a reader opens `NOTES.md`
- **THEN** a `## Current Status` heading appears and the section that
  follows it summarizes the project's current state

### Requirement: NOTES.md does not duplicate README.md content

`NOTES.md` MUST NOT repeat content that already lives in `README.md`; it
MUST focus on notes that complement the README rather than restating it.

#### Scenario: NOTES.md content is complementary to README.md

- **WHEN** a reviewer compares `NOTES.md` against `README.md`
- **THEN** the information in `NOTES.md` is not a verbatim copy of any
  paragraph in `README.md`
