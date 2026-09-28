# Spec Delta

## Purpose

Establishes a stable, top-level `NOTES.md` in the repository that holds human-authored project notes and is referenced by downstream specs and automation as a fixed anchor. `NOTES.md` is a documentation surface only and MUST NOT override behavior described elsewhere in the repository.

## ADDED Requirements

### Requirement: NOTES.md exists at the repository root

The repository SHALL contain a file named exactly `NOTES.md` at the repository root, as a direct sibling of `README.md`. The file SHALL be plain UTF-8 Markdown.

#### Scenario: File present at repository root
- **WHEN** a reader enumerates the files at the repository root
- **THEN** a file named exactly `NOTES.md` is present

#### Scenario: File is non-empty Markdown
- **WHEN** the file `NOTES.md` is opened from the repository root
- **THEN** it contains at least one non-empty line of Markdown content

### Requirement: NOTES.md includes the baseline sections in a fixed order

`NOTES.md` MUST contain, in this exact order, three level-2 Markdown headings named exactly `Project Status`, `Open Questions`, and `Change Index`. No other level-2 heading MAY appear between any two of these three headings. Each of the three sections MUST contain at least one non-heading line of content.

#### Scenario: Required headings appear in order
- **WHEN** a reader scans the level-2 headings of `NOTES.md`
- **THEN** the document contains, in ascending order, exactly the headings `Project Status`, `Open Questions`, and `Change Index`, with no other level-2 heading interleaved between them

#### Scenario: Each baseline section has body content
- **WHEN** a reader opens any of the three required sections
- **THEN** the section contains at least one line that is not a Markdown heading

#### Scenario: Sections are not empty placeholders
- **WHEN** a reader inspects the body of each required section
- **THEN** no section consists solely of a heading followed by another heading or by end of file

### Requirement: NOTES.md is a documentation-only surface

`NOTES.md` MUST NOT contradict or override the declarative facts already documented in `README.md` or `orca-companion.json` at the change's baseline commit. Statements in `NOTES.md` describe notes about the project; they MUST NOT redefine behavior, configuration values, or commands already declared by those files.

#### Scenario: No behavioral override of README or orca-companion.json
- **WHEN** a reader compares a directive in `NOTES.md` against the corresponding content of `README.md` and `orca-companion.json` at the baseline commit
- **THEN** the directive in `NOTES.md` is consistent with, and does not contradict, those source files

#### Scenario: NOTES.md contains no executable override scripts
- **WHEN** `NOTES.md` is read as plain text
- **THEN** it contains no fenced code block tagged as a shell, build, or CI script that asserts a behavior, command, or configuration not already documented in `README.md` or `orca-companion.json`
