# Spec Delta

## Purpose

Defines the placement, content, and accuracy rules for the project status
banner in the repository's `README.md`, so the repository's front page states
its current stage truthfully instead of deferring to future changes.

## ADDED Requirements

### Requirement: README carries a project status banner

`README.md` MUST contain a project status banner: a single contiguous block
directly beneath the top-level title, before any other body content, that
tells a reader the project's current stage and what kind of project it is.
The banner MUST be visually distinguishable from ordinary prose — rendered as
a Markdown blockquote block, meaning every one of its lines starts with `>`.

#### Scenario: Banner sits directly under the title
- **WHEN** a reader reads `README.md` from the top
- **THEN** the first content after the single `#` title is the banner block, and
  no other body content precedes it

#### Scenario: Banner is visually distinct
- **WHEN** `README.md` is rendered by a Markdown viewer
- **THEN** the banner appears as a blockquote set apart from the surrounding
  paragraphs, not as another body paragraph

#### Scenario: Banner states stage and project kind
- **WHEN** a reader reads only the banner
- **THEN** the banner says what development stage the project is in and what
  the project is, in at least one sentence each

### Requirement: Banner replaces the deferral placeholder

`README.md` MUST NOT retain the placeholder line that defers content to future
changes. The placeholder text `will be added in later changes` MUST NOT appear
anywhere in the file, and it MUST NOT be rephrased into an equivalent promise
that the README has no such content yet.

#### Scenario: No placeholder survives
- **WHEN** a search is run over `README.md` for `will be added in later changes`
- **THEN** the search finds no match

#### Scenario: No equivalent deferral is introduced
- **WHEN** a reviewer reads the whole of `README.md`
- **THEN** no line promises that sections are forthcoming, since the banner
  replaces the deferral rather than restating it

### Requirement: Banner stays scoped and accurate

Every path the banner names MUST resolve to a real file or directory at the
revision the banner is written against, and every claim it makes MUST be true
of the repository at that revision. The banner MUST NOT name capabilities,
commands, or entry points the repository does not contain.

#### Scenario: Referenced paths exist
- **WHEN** each path named in the banner is resolved against the repository root
- **THEN** each path corresponds to a file or directory that exists

#### Scenario: Claims match reality
- **WHEN** a reviewer compares each statement in the banner against the
  repository contents
- **THEN** every statement is accurate at the revision being documented

### Requirement: README document structure stays intact

`README.md` MUST remain a plain Markdown document with exactly one top-level
title and no additional headings introduced by the banner; the banner replaces
one line of prose and does not restructure the document.

#### Scenario: Single title preserved
- **WHEN** the top-level titles in `README.md` are counted
- **THEN** exactly one line starts with `# `

#### Scenario: No new headings
- **WHEN** headings of any level are listed in `README.md`
- **THEN** the only heading is the original project title
