# Spec Delta

## Purpose

The project shall maintain a top-level `NOTES.md` file that serves as a
concise orientation document for first-time readers, sitting alongside
`README.md` and `orca-companion.json` rather than replacing either of
them.

## ADDED Requirements

### Requirement: Top-level NOTES.md file
The project MUST provide a `NOTES.md` file at the repository root that
documents the project's baseline orientation for new readers.

#### Scenario: NOTES.md is present at the repository root
- **WHEN** a user lists the top-level files of the repository
- **THEN** a `NOTES.md` file is present at the same level as
  `README.md`

#### Scenario: NOTES.md renders as structured markdown
- **WHEN** a user opens `NOTES.md` in a markdown viewer
- **THEN** the file is rendered as structured text with a top-level
  `#` heading and one or more `##` body sections

### Requirement: NOTES.md orientation content
The `NOTES.md` file MUST contain, at a minimum, the following four
sections, in this order: a "Project" section, a "Status" section, a
"Next Steps" section, and a "References" section.

#### Scenario: All four required sections are present in order
- **WHEN** a user reads `NOTES.md`
- **THEN** the file contains the section headers `## Project`,
  `## Status`, `## Next Steps`, and `## References` in that order

#### Scenario: References section points to authoritative files
- **WHEN** a user reads the References section of `NOTES.md`
- **THEN** at least one of `README.md`, `orca-companion.json`, or the
  `openspec/` directory is named as a source of further information

### Requirement: NOTES.md stays in sync with active OpenSpec changes
The Next Steps section of `NOTES.md` MUST list the currently active
OpenSpec changes so that readers can discover the next planned work
without leaving the file.

#### Scenario: Active change is reflected in Next Steps
- **WHEN** an OpenSpec change is added under `openspec/changes/`
- **THEN** the change's short identifier appears in the Next Steps
  section of `NOTES.md`
