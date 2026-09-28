# Spec Delta

## Purpose

Define the baseline contract for `NOTES.md`, the repository's freeform notes file, so
that its location, required content, and section layout stay predictable for every
later change that appends notes.

## ADDED Requirements

### Requirement: Repository notes file
The system SHALL keep a file named `NOTES.md` at the repository root, and every commit
that touches it SHALL leave it as a non-empty UTF-8 Markdown document.

#### Scenario: Notes file present at repository root
- **WHEN** the repository is checked out at its root directory
- **THEN** a file named `NOTES.md` exists at that root and is a non-empty Markdown file

### Requirement: Purpose is documented in the file
The file SHALL state, in its own words, why the notes file exists, so a reader can tell
without external context whether an entry belongs in it.

#### Scenario: Reader learns the intent
- **WHEN** a contributor opens `NOTES.md` for the first time
- **THEN** the opening text explains the purpose of the notes file

### Requirement: Stable section layout
The file SHALL contain at least one Markdown heading (level 1 or 2) that delimits the
notes area, so later changes can append entries beneath a known anchor.

#### Scenario: Appending an entry later
- **WHEN** a later change adds a note to `NOTES.md`
- **THEN** the entry is added beneath an existing heading without reordering the document's sections

### Requirement: Additive-only edits
Edits to `NOTES.md` SHALL be append-only: earlier entries MUST be preserved verbatim so
the file stays usable as a chronological record.

#### Scenario: Earlier entries preserved
- **WHEN** a new note is appended to an existing `NOTES.md`
- **THEN** all previously present entries are still present and unchanged

