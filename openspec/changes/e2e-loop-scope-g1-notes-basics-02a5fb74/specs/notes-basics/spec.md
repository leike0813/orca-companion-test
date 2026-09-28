# Spec Delta

## Purpose

Defines the content and maintenance expectations for the repository's root-level `NOTES.md`, the entry point that orients contributors to the project, its harness configuration, its planning loop, and its working constraints.

## ADDED Requirements

### Requirement: Notes file exists at repository root

The repository SHALL contain a file named `NOTES.md` at its root, so that a contributor opening the project can locate it without knowing the layout in advance.

#### Scenario: Contributor opens the repository

- **WHEN** a contributor lists the repository root
- **THEN** a file named `NOTES.md` is present at the root

### Requirement: Notes state the project purpose

`NOTES.md` SHALL contain a section that states what the project is and what it is used for, in prose a non-author can understand without prior context.

#### Scenario: Reader asks what this project is

- **WHEN** a reader looks to `NOTES.md` to determine the purpose of the project
- **THEN** a clearly identifiable section answers what the project is and what it is for

### Requirement: Notes describe the harness configuration

`NOTES.md` SHALL contain a section explaining the role of `orca-companion.json`, including what it configures for this project (for example the coordinator model, tracker, and execution harness).

#### Scenario: Reader asks how the harness is configured

- **WHEN** a reader looks to `NOTES.md` to learn how the orca-companion harness is configured for this project
- **THEN** a clearly identifiable section explains what `orca-companion.json` configures and highlights its key settings

### Requirement: Notes explain the planning loop

`NOTES.md` SHALL contain a section describing how the OpenSpec planning loop works for this repository: that changes are proposed under `openspec/changes/<change-name>/` with a proposal, spec deltas, and tasks, and that a change is only complete once its tasks are checked and it is archived.

#### Scenario: Reader asks how to make a change here

- **WHEN** a reader looks to `NOTES.md` to learn how changes are planned and landed in this repository
- **THEN** a clearly identifiable section describes the OpenSpec change directory layout and the proposal/specs/tasks/archive lifecycle

### Requirement: Notes list working commands

`NOTES.md` SHALL contain a section listing the commands a contributor needs for normal work, with each command stated so it can be run as written.

#### Scenario: Contributor needs to validate a change

- **WHEN** a contributor looks to `NOTES.md` for the command that validates an OpenSpec change
- **THEN** the listed command is one that can be executed as written from the repository root

### Requirement: Notes record constraints and open work

`NOTES.md` SHALL contain a section recording the constraints contributors must respect and any open follow-up work that is not yet done.

#### Scenario: Contributor looks for boundaries

- **WHEN** a contributor looks to `NOTES.md` for the rules that bound changes to this repository and for outstanding work
- **THEN** a clearly identifiable section lists the constraints and the open follow-ups

### Requirement: Notes are concise and navigable

`NOTES.md` SHALL use Markdown headings for each required section so a reader can jump to a section directly, and SHALL NOT duplicate the README's project blurb as its own content.

#### Scenario: Reader scans for a section

- **WHEN** a reader scans the headings of `NOTES.md` looking for commands or constraints
- **THEN** each required section is reachable as a distinct Markdown heading

