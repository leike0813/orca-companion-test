# Notes Basics

## ADDED Requirements

### Requirement: Root project notes document

The repository MUST provide a `NOTES.md` file at its root as a human-readable place to preserve concise project context and contributor notes.

#### Scenario: Contributor opens the project notes

- **WHEN** a contributor opens `NOTES.md` from the repository root
- **THEN** the document identifies the project using information supported by the repository
- **AND** provides distinct sections for working notes and decisions

### Requirement: Notes can be extended over time

The notes document MUST use readable Markdown headings and allow contributors to add dated entries under the working notes and decisions sections.

#### Scenario: Contributor records a note

- **WHEN** a contributor records new project information
- **THEN** they can add a dated entry under the appropriate section without changing the document's basic structure
- **AND** the entry does not present unverified assumptions as established project facts
