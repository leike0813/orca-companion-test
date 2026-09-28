# Spec Delta

## Purpose

Define the minimum structural requirements for the repository's `NOTES.md`
so that subsequent work packages and human readers can rely on a stable,
discoverable home for lightweight project notes, release pointers, and
follow-up callouts.

## ADDED Requirements

### Requirement: NOTES.md exists at repository root

The repository MUST contain a Markdown file named `NOTES.md` located at the
top-level working tree root, alongside `README.md` and `orca-companion.json`.

#### Scenario: NOTES.md present at root

- **WHEN** a reader lists the files in the repository root after this change
  ships
- **THEN** `NOTES.md` is present alongside `README.md` and
  `orca-companion.json`

#### Scenario: NOTES.md is a Markdown file

- **WHEN** the contents of `NOTES.md` are inspected
- **THEN** the file is plain UTF-8 text with a non-empty body

### Requirement: NOTES.md starts with a Project Notes heading

`NOTES.md` MUST begin with a top-level heading whose text is exactly
`Project Notes`, followed by a short introductory paragraph that names the
`orca-companion` project and points the reader back to `README.md` for
high-level project information.

#### Scenario: Heading is exactly "Project Notes"

- **WHEN** the first non-empty line of `NOTES.md` is examined
- **THEN** it is a single `#` heading whose text is exactly `Project Notes`

#### Scenario: Intro paragraph references orca-companion and README.md

- **WHEN** the paragraph directly beneath the `# Project Notes` heading is
  read
- **THEN** it mentions `orca-companion` and explicitly references
  `README.md`

### Requirement: NOTES.md carries an Upcoming section

`NOTES.md` MUST contain a top-level section titled `## Upcoming` whose body
lists at least one bullet point that names a category of follow-up work
intended for a later change (for example, expanded installation or usage
documentation).

#### Scenario: Upcoming section exists

- **WHEN** the Markdown headings of `NOTES.md` are enumerated
- **THEN** a level-2 heading named `Upcoming` is present

#### Scenario: Upcoming section lists at least one follow-up item

- **WHEN** the body under `## Upcoming` is read
- **THEN** it contains at least one bullet item describing a planned
  follow-up that does not duplicate this change's scope
