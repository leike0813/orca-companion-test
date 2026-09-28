## Purpose

Provides a baseline NOTES.md file at the repository root with a fixed
section layout for capturing current state, decisions, and open
questions so contributors and follow-on changes have a single,
predictable place to read and append project context.

## ADDED Requirements

### Requirement: Repository has a NOTES.md file

The repository SHALL contain a `NOTES.md` file located at the
repository root, alongside `README.md`.

#### Scenario: NOTES.md exists at the repository root
- **WHEN** a contributor lists the repository root
- **THEN** `NOTES.md` SHALL be present as a regular file
- **AND** it SHALL be a Markdown document (`.md` extension)

#### Scenario: NOTES.md is not empty
- **WHEN** `NOTES.md` is read
- **THEN** it SHALL contain at least one non-whitespace character

### Requirement: NOTES.md has a fixed baseline section layout

`NOTES.md` SHALL contain the top-level sections `## Current State`,
`## Decisions`, and `## Open Questions`, in that order, each
introduced by a level-2 Markdown heading.

#### Scenario: Required headings are present and ordered
- **WHEN** `NOTES.md` is parsed as Markdown
- **THEN** it SHALL contain the level-2 headings `Current State`,
  `Decisions`, and `Open Questions`
- **AND** `Current State` SHALL appear before `Decisions`
- **AND** `Decisions` SHALL appear before `Open Questions`

#### Scenario: Each section has a placeholder body
- **WHEN** `NOTES.md` is read
- **THEN** every one of the three required sections SHALL contain
  at least one non-empty paragraph of body text after its heading
- **AND** no section SHALL be left empty

### Requirement: NOTES.md is plain Markdown with no executable content

`NOTES.md` SHALL be plain Markdown prose and SHALL NOT contain
executable code blocks, embedded scripts, HTML form elements, or
other content that requires runtime interpretation to read.

#### Scenario: No executable code blocks in NOTES.md
- **WHEN** `NOTES.md` is scanned for fenced code blocks (```)
- **THEN** no fenced code block SHALL be present
- **AND** no inline HTML `<script>` or `<form>` element SHALL be
  present

### Requirement: NOTES.md baseline is stable for follow-on changes

The baseline `NOTES.md` produced by this change SHALL be safe for
follow-on Work Packages to extend without restructuring the three
required sections.

#### Scenario: Section headings can be appended to
- **WHEN** a follow-on change adds bullets or paragraphs under one
  of `Current State`, `Decisions`, or `Open Questions`
- **THEN** the section headings, order, and identifiers SHALL remain
  unchanged
- **AND** the file SHALL still be valid Markdown with the three
  required headings
