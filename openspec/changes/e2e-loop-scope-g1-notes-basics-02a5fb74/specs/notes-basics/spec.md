# Spec Delta: notes-basics

## Purpose

Establishes the minimum structure and content of the repository-root
`NOTES.md` so the e2e-loop demonstration always ships a stable,
discoverable baseline notes document that downstream graph nodes can
layer on top of.

## ADDED Requirements

### Requirement: Project MUST ship a repository-root NOTES.md

The project MUST provide a `NOTES.md` file at the repository root, and
that file MUST be tracked in version control so it is present in every
clone and every worktree.

#### Scenario: NOTES.md is present at the repository root
- **WHEN** a contributor clones or checks out the repository at any
  commit that claims to include the `notes-basics` capability
- **THEN** the repository root contains a regular file whose name is
  exactly `NOTES.md` (case-sensitive)
- **AND** that file is readable as plain UTF-8 text

#### Scenario: NOTES.md is tracked in version control
- **WHEN** the working tree is in a clean state on a commit that claims
  to include the `notes-basics` capability
- **THEN** `git ls-files NOTES.md` (or an equivalent Git query) lists
  `NOTES.md` as tracked
- **AND** `NOTES.md` is not excluded by any `.gitignore` rule in the
  repository

### Requirement: NOTES.md MUST contain the required top-level sections

`NOTES.md` MUST contain exactly the following level-2 (`##`) sections,
in this order: `Overview`, `Conventions`, and `Pointers`. Each of
those sections MUST contain at least one non-blank line of body text.

#### Scenario: Required sections are present and ordered
- **WHEN** a reader opens `NOTES.md` in any standard Markdown viewer
- **THEN** the first level-2 heading in the document is `## Overview`
- **AND** the next level-2 heading after `## Overview` is
  `## Conventions`
- **AND** the next level-2 heading after `## Conventions` is
  `## Pointers`
- **AND** each of those three sections contains at least one
  non-whitespace character of body content

#### Scenario: No additional top-level sections are introduced
- **WHEN** `NOTES.md` is parsed for level-2 headings
- **THEN** the set of level-2 headings equals exactly
  `{Overview, Conventions, Pointers}` with no duplicates and no
  missing entries
- **AND** no other level-2 headings (e.g., `## FAQ`, `## License`,
  `## Changelog`) appear in `notes-basics`

### Requirement: NOTES.md MUST be valid standalone Markdown

`NOTES.md` MUST be valid GitHub-flavored Markdown, MUST be UTF-8
encoded without a byte order mark, and MUST NOT depend on external
resources (images, scripts, stylesheets, or other network-hosted
links) for any information that the document is supposed to convey.

#### Scenario: Document parses without Markdown errors
- **WHEN** `NOTES.md` is fed into a GitHub-flavored Markdown parser
  such as `markdownlint-cli2` or `remark`
- **THEN** the parser reports no fatal syntax errors
- **AND** the three required sections render as level-2 headings

#### Scenario: Document is self-contained
- **WHEN** a reader opens `NOTES.md` with no network access and with
  no other files in the repository available
- **THEN** the document still conveys the full intended content of
  the `Overview`, `Conventions`, and `Pointers` sections
- **AND** no required information is gated behind a missing external
  resource (image, script, or off-repository link)

### Requirement: NOTES.md MUST describe the project's e2e-loop context

The `## Overview` section MUST explicitly identify `orca-companion`
as an end-to-end loop demonstration project for the orca-companion
agent harness, and the `## Pointers` section MUST reference, by
their exact repository-relative paths, both `README.md` and
`orca-companion.json`.

#### Scenario: Overview states the project purpose
- **WHEN** a reader reads the `## Overview` section of `NOTES.md`
- **THEN** the section explicitly identifies the project as an
  end-to-end loop demonstration for the orca-companion agent harness
- **AND** the section is written as prose (not as an empty placeholder
  or a single stray character)

#### Scenario: Pointers reference the canonical configuration files
- **WHEN** a reader reads the `## Pointers` section of `NOTES.md`
- **THEN** the section mentions both `README.md` and
  `orca-companion.json` using their exact repository-relative paths
- **AND** each of those two file mentions is unambiguous (e.g., not
  written as "the README" or "the config" with no path)
