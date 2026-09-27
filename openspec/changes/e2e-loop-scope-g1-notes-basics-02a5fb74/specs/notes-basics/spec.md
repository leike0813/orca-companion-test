# Spec Delta

## Purpose

Defines the baseline presence, location, and required section structure of the project-root `NOTES.md` file so that downstream changes and contributors have a stable contract for the document.

## ADDED Requirements

### Requirement: NOTES.md Presence

The repository root MUST contain a Markdown file named exactly `NOTES.md` (case-sensitive) at the top level of the working tree, alongside `README.md`.

#### Scenario: File exists at the project root
- **WHEN** a contributor inspects the project root
- **THEN** a file named `NOTES.md` is present at the top level of the repository.

#### Scenario: Filename is exactly NOTES.md
- **WHEN** the file is located
- **THEN** its name is exactly `NOTES.md` with no additional extension, prefix, or suffix.

### Requirement: NOTES.md Required Sections

`NOTES.md` MUST contain, in this order, H2 sections titled exactly `Purpose`, `Conventions`, `Decisions`, and `Open Questions`. Each section MUST be non-empty.

#### Scenario: All required headings appear in order
- **WHEN** `NOTES.md` is parsed as Markdown
- **THEN** it contains the H2 headings `## Purpose`, `## Conventions`, `## Decisions`, and `## Open Questions` in that order.

#### Scenario: Every required section has body content
- **WHEN** a reviewer inspects `NOTES.md`
- **THEN** each of the four required H2 sections has at least one line of body content below its heading.

### Requirement: NOTES.md Markdown Formatting

`NOTES.md` MUST be encoded as UTF-8 text and MUST use `##` for the four required section headings (no `#` for those headings) so that the document remains compatible with the project's other Markdown files.

#### Scenario: Headings use level-two syntax
- **WHEN** the headings are inspected
- **THEN** the four required sections begin with `## ` rather than `# `.

#### Scenario: File is UTF-8 Markdown
- **WHEN** the file is opened as text
- **THEN** it decodes as UTF-8 and is rendered as Markdown.

### Requirement: NOTES.md Role Separation from README.md

`NOTES.md` MUST be the canonical home for project-internal development notes, conventions, decisions, and open questions. It MUST NOT duplicate the content already maintained in `README.md` (project description, installation, usage, and similar user-facing material).

#### Scenario: User-facing content stays in README.md
- **WHEN** a contributor looks for the project description, installation steps, or usage examples
- **THEN** those items are found in `README.md` and not reproduced in `NOTES.md`.

#### Scenario: Development notes live in NOTES.md
- **WHEN** a contributor records a new development convention, decision, or open question
- **THEN** the entry is added to the matching section of `NOTES.md`.

