# Spec Delta

## Purpose

Establishes the baseline `NOTES.md` artifact at the repository root so that the orca-companion project records its identity, purpose, and the placeholder scope reserved for future changes in a single canonical place.

## ADDED Requirements

### Requirement: NOTES.md Existence

The repository MUST contain a `NOTES.md` file located at the repository root (sibling of `README.md`).

#### Scenario: NOTES.md present at root

- **WHEN** a reviewer inspects the repository root
- **THEN** a file named `NOTES.md` exists alongside `README.md`

### Requirement: NOTES.md Identity and Purpose Headings

The `NOTES.md` file MUST contain, in order, top-level Markdown headings for the project name and a purpose statement. The project name heading MUST match the repository name `orca-companion` and the purpose heading MUST label the project as an e2e-loop demonstration project.

#### Scenario: Required headings are present and ordered

- **WHEN** a reader scans `NOTES.md` from the top
- **THEN** the first top-level heading identifies the project as `orca-companion`
- **AND** a subsequent top-level heading labelled `Purpose` describes the project as an e2e-loop demonstration project

### Requirement: NOTES.md Reserved Future Sections

The `NOTES.md` file MUST include top-level headings named `Installation` and `Usage` whose bodies are reserved placeholders for follow-up changes.

#### Scenario: Reserved headings exist as placeholders

- **WHEN** a reader inspects the section list of `NOTES.md`
- **THEN** a top-level heading named `Installation` is present
- **AND** a top-level heading named `Usage` is present
- **AND** each reserved heading contains a placeholder note indicating that its content will be filled in by a future change

### Requirement: NOTES.md Markdown Validity

The `NOTES.md` file MUST be a syntactically valid UTF-8 Markdown document with consistent top-level heading levels (no skipped levels between consecutive top-level headings).

#### Scenario: Markdown structure is valid

- **WHEN** a Markdown parser renders `NOTES.md`
- **THEN** the document parses without error
- **AND** consecutive top-level headings do not skip levels (e.g. `#` followed directly by `###`)
