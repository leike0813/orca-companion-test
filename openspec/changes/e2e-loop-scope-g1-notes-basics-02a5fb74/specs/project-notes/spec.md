# Spec Delta

## Purpose

Defines the baseline structure and required sections of the repository-root `NOTES.md`
file so contributors can rely on a stable location and predictable outline for
project notes.

## ADDED Requirements

### Requirement: NOTES.md file exists at the repository root
The system SHALL provide a `NOTES.md` file located at the top level of the working
copy, next to `README.md` and `orca-companion.json`.

#### Scenario: NOTES.md present in a fresh checkout
- **WHEN** a contributor clones the repository and lists the top-level files
- **THEN** `NOTES.md` is present alongside `README.md` and `orca-companion.json`

#### Scenario: NOTES.md is plain Markdown
- **WHEN** a renderer opens `NOTES.md`
- **THEN** the file is parsed as GitHub-flavored Markdown and renders headings,
  paragraphs, and bullet lists without errors

### Requirement: NOTES.md begins with a top-level Notes heading and introduction
The system SHALL ensure `NOTES.md` starts with a single `# Notes` heading followed
by an introductory paragraph that states the file's purpose in plain language.

#### Scenario: First heading is `# Notes`
- **WHEN** a reader opens `NOTES.md`
- **THEN** the first heading is `# Notes` and is followed by one or more sentences
  explaining that the file collects project notes

### Requirement: NOTES.md contains required baseline sections
The system SHALL ensure `NOTES.md` includes the following `##` level sections, in
this order, each with at least one paragraph of content: `## Project Context`,
`## Conventions`, `## Work Package Notes`.

#### Scenario: All baseline sections are present
- **WHEN** a contributor reads `NOTES.md` from top to bottom
- **THEN** the file contains the sections `Project Context`, `Conventions`, and
  `Work Package Notes` as level-2 headings, each followed by prose content

#### Scenario: Baseline sections appear in the documented order
- **WHEN** a reader scans the level-2 headings of `NOTES.md`
- **THEN** `Project Context` precedes `Conventions`, which precedes
  `Work Package Notes`
