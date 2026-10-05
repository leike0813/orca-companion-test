# Spec Delta

## Purpose

Defines the repository-root NOTES.md file that orients contributors: where it
must exist, which sections it must carry, and the rules that keep its content
consistent with the repository itself.

## ADDED Requirements

### Requirement: Root notes file

The repository SHALL contain a Markdown file named NOTES.md at its root, and
that file SHALL be tracked by version control.

#### Scenario: Fresh checkout contains the notes file

- **WHEN** a contributor lists the files at the repository root
- **THEN** NOTES.md is present alongside README.md

#### Scenario: Notes file is committed

- **WHEN** the working tree is inspected with git status
- **THEN** NOTES.md is tracked and has no unstaged or uncommitted deletion

### Requirement: Required sections

NOTES.md SHALL contain a top-level heading followed by these second-level
sections, in this order: `Purpose`, `Requirements`, `Getting Started`,
`Repository Layout`, and `OpenSpec Workflow`. Sections SHALL NOT be empty.

#### Scenario: All required sections are present in order

- **WHEN** the second-level headings of NOTES.md are listed
- **THEN** they are Purpose, Requirements, Getting Started, Repository Layout, and OpenSpec Workflow, in that order

#### Scenario: No section is left empty

- **WHEN** each required section is inspected
- **THEN** it contains at least one line of non-whitespace content

### Requirement: Content accuracy

NOTES.md SHALL describe the repository as it actually is. It SHALL NOT contain
unresolved placeholder markers such as TODO or TBD, and any path it names SHALL
match an existing path in the repository.

#### Scenario: No placeholder markers remain

- **WHEN** NOTES.md is searched for placeholder markers
- **THEN** no TODO or TBD marker is found

#### Scenario: Named paths exist

- **WHEN** each repository path mentioned in NOTES.md is resolved
- **THEN** every one of them resolves to an existing file or directory

### Requirement: Plain Markdown structure

NOTES.md SHALL be written as plain Markdown using ATX headings and list
syntax, with no heading nested deeper than level three.

#### Scenario: Headings use ATX style and stay shallow

- **WHEN** the headings of NOTES.md are extracted
- **THEN** each is written with leading hash characters and none is deeper than level three

#### Scenario: Lists use Markdown list markers

- **WHEN** enumerated content appears in NOTES.md
- **THEN** each item is introduced by a Markdown list marker rather than manual indentation or numbering
