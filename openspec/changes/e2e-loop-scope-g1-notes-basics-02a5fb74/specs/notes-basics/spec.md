# Spec Delta: notes-basics

## Purpose

Defines the minimal structure and content of the project's `NOTES.md` so
contributors have a single, predictable landing spot for the project's
most foundational notes and so downstream readers know what shape to
expect from that file.

## ADDED Requirements

### Requirement: Notes Heading

`NOTES.md` SHALL begin with a single H1 heading whose visible text is
exactly `Notes`, and that heading SHALL be the first non-blank line of
the file. No second H1 heading SHALL appear anywhere in the file.

#### Scenario: First non-blank line is the Notes heading
- **WHEN** a reader opens `NOTES.md` at the repository root
- **THEN** the first non-blank line of the file is `# Notes`
- **AND** the file contains exactly one H1 heading line that matches
  `^# Notes\s*$`

#### Scenario: No second H1 heading is present
- **WHEN** a reader scans every line of `NOTES.md` for lines that match
  the pattern `^# .+$`
- **THEN** exactly one such line exists in the file
- **AND** no other line in the file begins with the `#` character
  followed by a space

### Requirement: Topic Sections

`NOTES.md` SHALL contain at least one H2 section. Each H2 section SHALL
introduce a basic topic with a plain-English heading and SHALL contain
at least one sentence of body content beneath that heading.

#### Scenario: At least one H2 section is present
- **WHEN** a reader scans `NOTES.md` for headings below the H1
- **THEN** they find at least one H2 heading whose line matches
  `^## .+$`
- **AND** the body beneath that H2 heading contains at least one
  sentence of plain prose

#### Scenario: Section headings are plain English
- **WHEN** a reader inspects the text of every H2 heading in `NOTES.md`
- **THEN** each heading is plain English composed of letters, digits,
  spaces, and basic punctuation
- **AND** no heading contains fenced code blocks, inline backticks, or
  raw HTML tags

### Requirement: No Placeholder Or TODO Content

`NOTES.md` SHALL NOT contain the substrings `TODO`, `TBD`,
`<placeholder>`, or `lorem ipsum` anywhere in the file. Implementers
and reviewers SHALL treat any such marker as a failure of this
requirement.

#### Scenario: No placeholder markers are present
- **WHEN** a reader scans the entire contents of `NOTES.md`
- **THEN** no line contains the case-sensitive substrings `TODO`,
  `TBD`, `<placeholder>`, or `lorem ipsum`
- **AND** the scan covers every byte of the file, including headings,
  body paragraphs, list items, and the trailing newline

### Requirement: Markdown Well-Formedness

`NOTES.md` SHALL be valid CommonMark. Every heading line SHALL match
the pattern `^#{1,6} .+$`, every list item SHALL begin with `- ` or a
digit followed by `. `, and the file SHALL end with exactly one
trailing newline character (LF, `\n`).

#### Scenario: File renders as valid CommonMark
- **WHEN** the file is rendered by a CommonMark parser
- **THEN** it parses without syntax errors
- **AND** every heading line in the parsed result matches the pattern
  `^#{1,6} .+$`

#### Scenario: File ends with a single trailing newline
- **WHEN** a reader inspects the final bytes of `NOTES.md`
- **THEN** the file ends with exactly one LF newline character
- **AND** the file does not end with zero, two, or more trailing
  newline characters
