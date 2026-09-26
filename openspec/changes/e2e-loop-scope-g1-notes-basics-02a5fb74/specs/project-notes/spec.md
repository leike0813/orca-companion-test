# Spec Delta: project-notes

## Purpose

Captures the canonical, human-authored project notes that document what the `orca-companion` e2e-loop demonstration is for, what its baseline scope covers, and which follow-ups are already planned. The capability defines the presence and required sections of `NOTES.md` so downstream Work Packages have a stable, in-repo anchor to extend.

## ADDED Requirements

### Requirement: Repository includes NOTES.md

The repository SHALL include a top-level `NOTES.md` file at the repository root, alongside `README.md`.

#### Scenario: NOTES.md exists at the repository root
- **WHEN** a contributor lists the files at the repository root
- **THEN** `NOTES.md` is present
- **AND** `NOTES.md` is a non-empty UTF-8 Markdown file

### Requirement: NOTES.md has a Purpose section

`NOTES.md` SHALL contain a top-level Markdown section titled `Purpose` that describes what the `orca-companion` project is for and why it exists.

#### Scenario: Purpose section documents the demonstration
- **WHEN** a reader opens `NOTES.md` and reads the `Purpose` section
- **THEN** the section names the project as an e2e-loop demonstration for the orca-companion agent harness
- **AND** the section explains why the demonstration is needed now

### Requirement: NOTES.md has a Baseline Scope section

`NOTES.md` SHALL contain a top-level Markdown section titled `Baseline Scope` that lists the files, capabilities, and surfaces included in the project's baseline commit.

#### Scenario: Baseline Scope references the in-scope files
- **WHEN** a reader opens `NOTES.md` and reads the `Baseline Scope` section
- **THEN** the section names `README.md`, `NOTES.md` (this file), and `orca-companion.json` as part of the baseline
- **AND** the section does not claim any path that is not present at the baseline commit

### Requirement: NOTES.md has a Follow-ups section

`NOTES.md` SHALL contain a top-level Markdown section titled `Follow-ups` that enumerates the next planned Work Packages or notes-driven changes in priority order.

#### Scenario: Follow-ups section lists planned Work Packages
- **WHEN** a reader opens `NOTES.md` and reads the `Follow-ups` section
- **THEN** the section lists at least one planned follow-up Work Package
- **AND** each listed follow-up is a single bullet item whose text begins with a verb

### Requirement: NOTES.md uses Markdown headings consistently

`NOTES.md` SHALL use exactly three top-level Markdown sections, in the order `Purpose`, `Baseline Scope`, `Follow-ups`, each introduced by a level-1 heading (`#`).

#### Scenario: Section order and heading level
- **WHEN** a reader scans the headings in `NOTES.md`
- **THEN** the first heading is `# Purpose`
- **AND** the second heading is `# Baseline Scope`
- **AND** the third heading is `# Follow-ups`
- **AND** no other level-1 headings appear in the file
