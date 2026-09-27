# Spec Delta

## Purpose

Provide a baseline `NOTES.md` file at the repository root that records introductory notes for the orca-companion e2e-loop demonstration project and establishes the heading structure that future notes changes will extend.

## ADDED Requirements

### Requirement: Repository includes NOTES.md

The repository SHALL contain a tracked Markdown file named `NOTES.md` located at the repository root, alongside `README.md` and `orca-companion.json`.

#### Scenario: NOTES.md exists at the repository root
- **WHEN** a contributor lists the files in the repository root
- **THEN** `NOTES.md` is present and is recognized as a Markdown file by its `.md` extension

### Requirement: NOTES.md documents the e2e-loop demonstration purpose

`NOTES.md` SHALL include a section that records the project's identity as the orca-companion e2e-loop demonstration and explains its role inside the orca-companion agent harness.

#### Scenario: Reader can identify the project purpose
- **WHEN** a contributor reads the introductory section of `NOTES.md`
- **THEN** the section names the project as orca-companion and describes it as an e2e-loop demonstration for the orca-companion agent harness

### Requirement: NOTES.md records the current e2e-loop-scope status

`NOTES.md` SHALL include a section that captures the current scope of the `e2e-loop-scope` graph generation and lists the work package that introduces the file.

#### Scenario: Reader can see the current work-package status
- **WHEN** a contributor reads the current-scope section of `NOTES.md`
- **THEN** the section identifies graph generation `g1` and names `notes-basics` as the work package that introduces this `NOTES.md` file

### Requirement: NOTES.md uses canonical Markdown structure

`NOTES.md` SHALL be organized as well-formed Markdown that uses only top-level (`#`) and second-level (`##`) headings, never skips heading levels, and contains no placeholder markers such as `TBD` or `TODO` in the published prose.

#### Scenario: Validator confirms heading hierarchy
- **WHEN** the headings in `NOTES.md` are walked in document order
- **THEN** every heading level increases by at most one level relative to the previous heading and the file contains no `TBD` or `TODO` markers in its prose

### Requirement: NOTES.md reserves headings for future changes

`NOTES.md` SHALL include second-level headings named `## Installation` and `## Usage` whose bodies state that the section will be filled in by later changes, so that future work packages have a stable anchor point.

#### Scenario: Future-change anchors are present
- **WHEN** a contributor searches `NOTES.md` for the `## Installation` and `## Usage` headings
- **THEN** both headings are present and each body indicates the section is reserved for a later change
