# Spec Delta

## Purpose

Define the structure and writing conventions for the project's `NOTES.md` working-notes file so that anyone opening the repository can find dated, categorized notes in a predictable layout.

## ADDED Requirements

### Requirement: NOTES.md Exists At Repository Root
The project SHALL provide a `NOTES.md` file at the repository root that is checked into version control.

#### Scenario: Contributor opens the repository
- **WHEN** a contributor lists the repository root
- **THEN** a file named `NOTES.md` is present and readable

### Requirement: Required Top-Level Sections
`NOTES.md` SHALL contain a top-level `# Notes` heading followed by the level-two sections `## Overview`, `## Decisions`, and `## Open Questions`, appearing in that order.

#### Scenario: Sections are present and ordered
- **WHEN** `NOTES.md` is read from top to bottom
- **THEN** it starts with `# Notes` and then lists `## Overview`, `## Decisions`, and `## Open Questions` in that order

#### Scenario: A required section is missing
- **WHEN** any of `## Overview`, `## Decisions`, or `## Open Questions` is absent from `NOTES.md`
- **THEN** the file does not satisfy this requirement

### Requirement: Dated Entries
Every entry under `## Decisions` and `## Open Questions` SHALL be introduced by a level-three heading of the form `### YYYY-MM-DD — <short title>`, where the date is an ISO-8601 calendar date.

#### Scenario: Entry heading follows the convention
- **WHEN** an entry appears under `## Decisions` or `## Open Questions`
- **THEN** its heading starts with a `YYYY-MM-DD` date, a spaced em dash separator, and a non-empty short title

#### Scenario: Undated entry is added
- **WHEN** an entry heading omits the `YYYY-MM-DD` prefix
- **THEN** the entry does not satisfy this requirement

### Requirement: Entries Are Scannable And Concise
Entries under `## Decisions` and `## Open Questions` SHALL be written as a single short paragraph of at most three sentences, and SHALL NOT contain nested level-four headings.

#### Scenario: Concise entry
- **WHEN** an entry is reviewed
- **THEN** it is a plain paragraph of at most three sentences with no nested headings

### Requirement: Overview States Purpose And How To Add Notes
The `## Overview` section SHALL state the purpose of the file in one sentence and SHALL state, in one sentence, that new notes are appended by editing the file directly and committing the result.

#### Scenario: Overview is self-explanatory
- **WHEN** a first-time contributor reads only `## Overview`
- **THEN** they learn what the file is for and how to add an entry without further instructions

