# Spec Delta

## Purpose

Defines the baseline project notes file `NOTES.md` so the repository has a
single, discoverable place for stating what the project is for and what is
intentionally deferred to later changes.

## ADDED Requirements

### Requirement: Project notes file exists at repository root

The repository MUST contain a tracked `NOTES.md` file at the worktree root.

#### Scenario: NOTES.md is present at the worktree root
- **WHEN** a contributor inspects the repository root
- **THEN** a `NOTES.md` file is present and tracked in version control

### Requirement: NOTES.md states project purpose and scope

`NOTES.md` MUST state the project's purpose in a short opening section and
MUST list at least one explicitly deferred follow-on item so contributors
can see what is intentionally out of the current baseline.

#### Scenario: NOTES.md opens with a Purpose section
- **WHEN** a contributor reads `NOTES.md`
- **THEN** the file begins with a section that describes the project's
  purpose

#### Scenario: NOTES.md lists deferred follow-on items
- **WHEN** a contributor reads `NOTES.md`
- **THEN** the file includes a section that lists at least one item
  deferred to a later change

### Requirement: NOTES.md uses Markdown headings and stays plain

`NOTES.md` MUST be valid Markdown using `ATX` headings (lines starting
with `#`) and MUST NOT embed HTML, scripts, or remote resources so the
file remains safely renderable on common Markdown viewers.

#### Scenario: NOTES.md contains only Markdown headings and plain text
- **WHEN** `NOTES.md` is opened in any Markdown viewer
- **THEN** the content renders as headings and paragraphs without
  attempting to load external resources or execute embedded scripts
