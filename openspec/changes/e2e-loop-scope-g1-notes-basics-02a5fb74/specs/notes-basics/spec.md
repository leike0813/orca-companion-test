# Spec Delta: notes-basics

## Purpose

The `notes-basics` capability provides a stable `NOTES.md` landing page at the
repository root that documents the project's basic purpose, contribution
conventions, scope, and pointers to other documentation so downstream work
packages and human readers share a single reference point.

## ADDED Requirements

### Requirement: NOTES.md exists at the repository root

A file named `NOTES.md` SHALL exist at the repository root (the same
directory that contains `README.md`).

#### Scenario: NOTES.md is present after the change

- **WHEN** a reader lists the contents of the repository root after the
  change is applied
- **THEN** a file named `NOTES.md` is present
- **AND** it is a regular file, not a symbolic link to a directory

### Requirement: NOTES.md is encoded as UTF-8 Markdown

`NOTES.md` SHALL be encoded as UTF-8 and use Markdown syntax (`.md`
extension) so it renders correctly in standard Markdown viewers.

#### Scenario: File has UTF-8 Markdown content

- **WHEN** a reader opens `NOTES.md`
- **THEN** the file's contents are valid UTF-8 text
- **AND** the file's contents parse as Markdown without errors in a standard
  Markdown parser

### Requirement: NOTES.md has a Purpose section

`NOTES.md` SHALL contain a clearly labeled section that states the project's
purpose in one short paragraph or bullet list.

#### Scenario: Purpose section is present and labeled

- **WHEN** a reader scans `NOTES.md`
- **THEN** a Markdown section heading with the case-insensitive word
  `Purpose` is present at any heading level
- **AND** the section contains at least one sentence describing what the
  project is for

### Requirement: NOTES.md has a Conventions section

`NOTES.md` SHALL contain a clearly labeled section that summarizes the
project's basic contribution conventions (such as how to propose a change,
how to format commit messages, or where to find related specifications).

#### Scenario: Conventions section is present and labeled

- **WHEN** a reader scans `NOTES.md`
- **THEN** a Markdown section heading with the case-insensitive word
  `Conventions` is present at any heading level
- **AND** the section contains at least one bullet item describing a
  convention

### Requirement: NOTES.md has a Scope section

`NOTES.md` SHALL contain a clearly labeled section that describes what is in
scope and what is out of scope for the current change graph, including a
pointer to `README.md` for installation, usage, and other deferred sections.

#### Scenario: Scope section is present and labeled

- **WHEN** a reader scans `NOTES.md`
- **THEN** a Markdown section heading with the case-insensitive word `Scope`
  is present at any heading level
- **AND** the section mentions both what this change graph covers and that
  installation, usage, and other sections live in `README.md`
