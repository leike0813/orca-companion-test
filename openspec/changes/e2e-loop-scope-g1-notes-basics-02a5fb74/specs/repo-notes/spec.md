# Spec Delta

## Purpose

Defines the repository's root-level notes document: what it must contain so a reader can orient themselves, and the accuracy rule that keeps its description of the repository trustworthy over time.

## ADDED Requirements

### Requirement: Root notes file
The repository SHALL provide a notes document at the repository root named `NOTES.md`, and that document SHALL contain non-empty prose content.

#### Scenario: Notes file is present at the repository root
- **WHEN** a reader looks for `NOTES.md` at the root of the repository
- **THEN** the file exists at that path and is not empty

#### Scenario: Notes file is discoverable at the root only
- **WHEN** the repository root is listed
- **THEN** exactly one notes document named `NOTES.md` appears at the root level, with no duplicate notes files at the root

### Requirement: Documented project basics
`NOTES.md` SHALL contain sections covering the project overview, the repository layout, and the commands used for everyday development work, each as a clearly delimited section within the document.

#### Scenario: Reader finds the project overview
- **WHEN** a reader opens `NOTES.md` and looks for a description of what the project is
- **THEN** a section states the project's purpose in prose rather than only naming the directory

#### Scenario: Reader finds the repository layout
- **WHEN** a reader opens `NOTES.md` and looks for an explanation of the directory structure
- **THEN** a section describes the top-level directories and what each one holds

#### Scenario: Reader finds the development commands
- **WHEN** a reader opens `NOTES.md` and looks for commands to run
- **THEN** a section lists the concrete commands for validating and listing OpenSpec items, each written so it can be copied and run as written

### Requirement: Referenced paths stay accurate
Every repository path that `NOTES.md` references SHALL exist in the repository at the time the notes are read.

#### Scenario: All referenced paths resolve
- **WHEN** each repository path named in `NOTES.md` is checked for existence
- **THEN** every named path exists, and no referenced path is missing

#### Scenario: Documented directories are described, not invented
- **WHEN** `NOTES.md` describes a top-level directory
- **THEN** that directory exists in the repository and the description matches the contents actually stored there
