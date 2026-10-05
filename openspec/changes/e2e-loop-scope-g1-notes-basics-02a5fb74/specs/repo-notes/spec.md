# Spec Delta

## Purpose

The repository ships a root-level `NOTES.md` that orients new contributors by describing
the repository layout, the local development workflow, and the conventions contributors
are expected to follow.

## ADDED Requirements

### Requirement: Root notes file exists

The repository SHALL contain a file at the path `NOTES.md`, and that file SHALL be the
single root-level entry point for contributor orientation material.

#### Scenario: Notes file is present at the repository root

- **WHEN** a contributor lists the files at the repository root
- **THEN** a file named `NOTES.md` is listed

#### Scenario: Notes file is readable as plain text

- **WHEN** a contributor opens `NOTES.md`
- **THEN** the file renders as readable plain-text Markdown

### Requirement: Notes file carries a title and purpose

`NOTES.md` SHALL open with a level-one heading, and that heading SHALL be followed by a
short statement explaining who the file is for and what it covers.

#### Scenario: Title and purpose are present

- **WHEN** a contributor reads the first lines of `NOTES.md`
- **THEN** the first line is a level-one heading naming the file's subject
- **AND** a statement describing the file's audience and subject follows the heading

### Requirement: Notes file covers the required sections

`NOTES.md` SHALL contain all of the following sections, each as a level-two heading
identified by its subject: repository layout, local development workflow, and contributor
conventions. Each of the three sections SHALL contain at least one sentence of content.

#### Scenario: All required sections are present and non-empty

- **WHEN** a contributor scans the level-two headings of `NOTES.md`
- **THEN** a heading for the repository layout is present
- **AND** a heading for the local development workflow is present
- **AND** a heading for the contributor conventions is present
- **AND** none of the three sections is left without content

#### Scenario: Each section is findable by topic

- **WHEN** a contributor looking for the layout of the repository searches `NOTES.md`
- **THEN** the layout section answers what the top-level paths in the repository are for

### Requirement: Notes statements are grounded in the repository

Every claim made in `NOTES.md` SHALL be verifiable by inspecting the repository contents
at the time the file is written. `NOTES.md` SHALL NOT describe capabilities, tooling, or
workflow steps that are absent from the repository.

#### Scenario: Documented paths exist

- **WHEN** `NOTES.md` names a path inside the repository
- **THEN** that path exists in the repository at the time the claim is read

#### Scenario: Documented commands are real

- **WHEN** `NOTES.md` states that a command is run to perform a development task
- **THEN** that command is one the repository's current contents support

#### Scenario: No unimplemented functionality is promised

- **WHEN** a contributor reads `NOTES.md` expecting a documented tool or script
- **THEN** that tool or script is present in the repository rather than merely described
