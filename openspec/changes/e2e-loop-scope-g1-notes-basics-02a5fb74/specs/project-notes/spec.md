# Spec Delta: project-notes

## Purpose

The `project-notes` capability establishes the existence and minimal, stable
structure of a project-root `NOTES.md` file for the orca-companion project.
It defines only the baseline outline so that later Work Packages in the
e2e-loop-scope graph can fill in concrete sections (Installation, Usage,
Conventions, etc.) without having to re-introduce the file or renegotiate its
top-level shape.

## ADDED Requirements

### Requirement: Repository Root Contains NOTES.md

The orca-companion repository MUST contain a tracked file named
`NOTES.md` at the repository root (the same directory that holds
`README.md` and `orca-companion.json`).

#### Scenario: NOTES.md present at the project root
- **WHEN** a contributor lists the tracked files at the project root
- **THEN** an entry for `NOTES.md` is present alongside `README.md`
  and `orca-companion.json`

#### Scenario: NOTES.md is a tracked file
- **WHEN** the repository's tracked-file listing is inspected
- **THEN** `NOTES.md` is reported as tracked (it is not ignored, not
  untracked, and not a symlink to an untracked path)

### Requirement: NOTES.md Top-Level Heading

`NOTES.md` MUST begin with a single top-level Markdown heading that
identifies the file as the orca-companion project's notes file. The
heading text MUST contain the word "Notes" (case-insensitive) and MUST
appear before any other content in the file.

#### Scenario: First line of NOTES.md is a level-1 heading
- **WHEN** the file `NOTES.md` is opened
- **THEN** the first non-blank line begins with a single `#` followed by
  a space and heading text containing the word "Notes"

#### Scenario: No preamble precedes the heading
- **WHEN** the bytes preceding the first level-1 heading in `NOTES.md`
  are inspected
- **THEN** they contain only optional leading blank lines and an optional
  UTF-8 BOM; no other content (frontmatter, prose, code fences) appears
  before that heading

### Requirement: NOTES.md Purpose Section

`NOTES.md` MUST contain a `## Purpose` section whose body explains, in
at least one full sentence, what role `NOTES.md` plays for the
orca-companion project and how it relates to `README.md`.

#### Scenario: Purpose section exists
- **WHEN** the level-2 headings of `NOTES.md` are listed
- **THEN** a heading named exactly `Purpose` (case-insensitive) is
  present

#### Scenario: Purpose body references README.md's deferral
- **WHEN** the body of the `## Purpose` section is read
- **THEN** it states that `README.md` defers detailed documentation and
  that `NOTES.md` is where that context lives instead

### Requirement: NOTES.md Stub Sections For Later Generations

`NOTES.md` MUST reserve at least one additional level-2 heading beyond
`## Purpose` whose body is empty or contains only placeholder text
indicating that a later generation of the e2e-loop-scope graph will fill
it in. The reserved heading MUST be one of: `Conventions`, `Status`,
or `Open Questions`.

#### Scenario: At least one reserved heading exists
- **WHEN** the level-2 headings of `NOTES.md` beyond `## Purpose` are
  listed
- **THEN** at least one heading matches one of `Conventions`,
  `Status`, or `Open Questions` (case-insensitive)

#### Scenario: Reserved heading body is a stub
- **WHEN** the body under a reserved heading is read
- **THEN** it is either empty or contains a single placeholder sentence
  that explicitly says the section will be populated by a later Work
  Package

