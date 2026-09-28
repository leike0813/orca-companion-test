# Spec Delta

## Purpose

Defines the structure and content rules for the repository's top-level
`NOTES.md` document so it stays a short, complete, and reviewable reference
for contributors.

## ADDED Requirements

### Requirement: Repository provides a NOTES.md reference

The repository MUST contain a Markdown file named `NOTES.md` at its root, so
that contributors and reviewers have a single discoverable place for the
project's basics.

#### Scenario: NOTES.md exists at the repository root
- **WHEN** a contributor lists the files in the repository root
- **THEN** a file named `NOTES.md` is present alongside `README.md`

#### Scenario: NOTES.md is readable as plain Markdown
- **WHEN** a contributor opens `NOTES.md` in any Markdown viewer
- **THEN** the file renders as formatted Markdown with a single top-level title

### Requirement: NOTES.md documents the project basics

`NOTES.md` MUST contain a non-empty statement of what the project is, and MUST
contain at least one section describing how the repository is laid out or how
its contents may be verified. Placeholder or empty sections do NOT satisfy
this requirement.

#### Scenario: Purpose is stated
- **WHEN** a reviewer reads `NOTES.md`
- **THEN** the document states what this project is in at least one sentence

#### Scenario: Structure or verification guidance is present
- **WHEN** a reviewer looks for how to navigate or verify the repository
- **THEN** `NOTES.md` contains at least one heading covering layout or
  verification with non-empty content beneath it

### Requirement: NOTES.md stays scoped and consistent

`NOTES.md` MUST agree with the repository it documents: any path, command, or
entry point it names MUST exist at the referenced revision, and it MUST NOT
claim features or files that the repository does not contain.

#### Scenario: Referenced paths exist
- **WHEN** every file path named in `NOTES.md` is resolved against the
  repository root
- **THEN** each resolved path corresponds to a file or directory that exists

#### Scenario: Claims match reality
- **WHEN** a reviewer compares the statements in `NOTES.md` against the
  repository contents
- **THEN** every stated fact is accurate at the revision being documented
