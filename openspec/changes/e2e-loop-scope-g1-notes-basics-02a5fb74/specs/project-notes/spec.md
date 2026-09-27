# Spec Delta

## Purpose

Captures the structure and baseline content of the top-level `NOTES.md` file so the orca-companion harness has a stable, machine-checkable home for project-wide notes.

## ADDED Requirements

### Requirement: Project notes file exists

A file named `NOTES.md` MUST exist at the repository root and MUST be tracked in version control.

#### Scenario: Notes file is present at the repository root
- **WHEN** a contributor lists the repository root at the default branch HEAD
- **THEN** the listing includes a regular file named `NOTES.md`

### Requirement: Notes file contains baseline sections

The `NOTES.md` file MUST contain top-level Markdown headings (level 2 or deeper) for each of the following baseline sections, in this order: `Overview`, `Conventions`, `Open Questions`. Each baseline section MUST contain at least one non-empty line of prose.

#### Scenario: All baseline sections are present and populated
- **WHEN** a contributor reads `NOTES.md` from the repository root
- **THEN** the file contains the headings `## Overview`, `## Conventions`, and `## Open Questions` in that order, and each section contains at least one prose line

### Requirement: Overview section summarizes the project

The `Overview` section MUST state, in prose, what the orca-companion harness is and that it is the subject of the notes captured in this file.

#### Scenario: Overview explains the harness
- **WHEN** a contributor reads the `Overview` section of `NOTES.md`
- **THEN** the prose identifies the project as the orca-companion e2e-loop harness and frames the rest of the file as project notes

### Requirement: Conventions section documents current rules

The `Conventions` section MUST list, as a Markdown bullet list with at least one entry, the rules that contributors are expected to follow when authoring or updating `NOTES.md` itself or any other project note captured under this capability.

#### Scenario: Conventions lists enforceable rules
- **WHEN** a contributor reads the `Conventions` section of `NOTES.md`
- **THEN** the section contains a Markdown bullet list with one or more entries describing rules for how project notes are written and maintained

### Requirement: Open Questions section records unresolved items

The `Open Questions` section MUST contain a Markdown bullet list. Each bullet MUST start with a one-line summary of a question or unresolved item and MAY include inline Markdown linking back to any tracking artifact.

#### Scenario: Open Questions tracks at least one item
- **WHEN** a contributor reads the `Open Questions` section of `NOTES.md`
- **THEN** the section contains a Markdown bullet list describing at least one open question or unresolved item relevant to the orca-companion harness

### Requirement: Notes file is plain Markdown

The `NOTES.md` file MUST be encoded as UTF-8 text containing only CommonMark Markdown (no embedded binary, HTML scripts, or executable content).

#### Scenario: File is portable Markdown
- **WHEN** a tooling step reads `NOTES.md` as bytes from the repository root
- **THEN** the bytes decode as UTF-8 and contain no script tags, executable payloads, or other non-Markdown binary content
