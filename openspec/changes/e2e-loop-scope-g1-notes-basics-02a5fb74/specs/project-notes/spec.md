# Spec Delta

## Purpose

Define the repository-level `NOTES.md` document so contributors can find the
project's basic working notes in a predictable place and know what that file
is required to contain.

## ADDED Requirements

### Requirement: Project notes document

The repository MUST provide a `NOTES.md` file at its root that records basic
working notes for the project, and that file MUST contain a title, a short
purpose statement, and a numbered list of notes.

#### Scenario: Reader opens the notes document

- **WHEN** a contributor opens `NOTES.md` at the repository root
- **THEN** the file shows a title heading, a purpose statement, and at least
  one numbered note entry

#### Scenario: Notes document is added to the repository

- **WHEN** `NOTES.md` does not exist and this change is implemented
- **THEN** `NOTES.md` is created at the repository root with all three
  required parts

### Requirement: Notes reference the README

`NOTES.md` MUST contain a reference that points readers to `README.md` so the
reader can tell which document is authoritative for project description.

#### Scenario: Reader wants project background

- **WHEN** a reader finishes `NOTES.md` and needs background on the project
- **THEN** `NOTES.md` names `README.md` as the place holding that background

### Requirement: Notes stay in scope of documentation

`NOTES.md` MUST contain prose only: it MUST NOT declare dependencies,
scripts, or configuration values that the project does not implement.

#### Scenario: Notes are reviewed for accuracy

- **WHEN** a reviewer checks each note against the repository contents
- **THEN** every note describes something observable in the repository, and
  no note claims a build, dependency, or command that does not exist
