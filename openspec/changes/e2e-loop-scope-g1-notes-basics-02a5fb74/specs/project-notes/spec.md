# Spec Delta

## Purpose

Defines the contract for the repository's `NOTES.md` engineering notes file, which serves as the foundation for release notes, design decisions, and follow-ups that downstream changes can extend.

## ADDED Requirements

### Requirement: NOTES.md location

A file named `NOTES.md` SHALL exist at the repository root (the same directory that contains `README.md`).

#### Scenario: NOTES.md is present at the repository root
- **WHEN** a reader inspects the repository root
- **THEN** a file named `NOTES.md` is present

### Requirement: NOTES.md required sections

`NOTES.md` SHALL contain the following top-level sections, in this order: `## Release Notes`, `## Design Decisions`, `## Follow-ups`. Each section SHALL contain at least one entry that conforms to the entry-shape requirement below.

#### Scenario: All required top-level sections are present
- **WHEN** a reader scans `NOTES.md` from top to bottom
- **THEN** the headings `## Release Notes`, `## Design Decisions`, and `## Follow-ups` all appear in that order

#### Scenario: Each required section is non-empty
- **WHEN** a reader opens any of the required sections
- **THEN** at least one entry (heading or bullet) is present under that section

### Requirement: NOTES.md entry shape

Each non-empty entry under `## Release Notes`, `## Design Decisions`, or `## Follow-ups` SHALL start with a date in ISO-8601 form (`YYYY-MM-DD`), followed by a short title on the same line. Entries under `## Release Notes` and `## Follow-ups` SHALL be presented as bulleted items (`-`). Entries under `## Design Decisions` SHALL be presented as third-level headings (`### `) so that long-form rationale can follow the title line.

#### Scenario: Release Notes entries use bullet form with a dated title
- **WHEN** a reader inspects any entry under `## Release Notes`
- **THEN** the entry begins with `- YYYY-MM-DD ` and is followed by a short title

#### Scenario: Design Decisions entries use a third-level heading with a dated title
- **WHEN** a reader inspects any entry under `## Design Decisions`
- **THEN** the entry is a third-level heading of the form `### YYYY-MM-DD <short title>` and may be followed by additional rationale lines

#### Scenario: Follow-ups entries use bullet form with a dated title
- **WHEN** a reader inspects any entry under `## Follow-ups`
- **THEN** the entry begins with `- YYYY-MM-DD ` and is followed by a short title

### Requirement: NOTES.md non-empty

`NOTES.md` SHALL contain at least one entry across the required sections so that the file is never shipped empty once this capability is active.

#### Scenario: NOTES.md ships with content
- **WHEN** a reader opens `NOTES.md` for the first time after this capability is active
- **THEN** at least one entry conforming to the entry-shape requirement is present
