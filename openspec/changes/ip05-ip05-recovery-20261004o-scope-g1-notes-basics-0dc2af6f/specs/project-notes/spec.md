# Spec Delta

## Purpose

Gives the repository one durable, human- and agent-readable record of its own basics — purpose, file layout, companion configuration, working agreements, and open items — so a recovered or freshly cloned worktree can be understood without reverse-engineering its configuration by hand.

## ADDED Requirements

### Requirement: Repository notes file

The repository MUST contain a Markdown notes file at `NOTES.md` in the repository root, and that file MUST open with a single top-level heading so it is recognizable as the project's notes document.

#### Scenario: Fresh checkout of the worktree

- **WHEN** a user or agent lists the repository root of a fresh checkout
- **THEN** a file named `NOTES.md` is present alongside `README.md`
- **AND** the first line of that file is a top-level Markdown heading

#### Scenario: Notes file is read as plain text

- **WHEN** `NOTES.md` is opened with any plain-text or Markdown viewer
- **THEN** it renders as structured Markdown with no tool-specific syntax or embedded binary payload

### Requirement: Notes cover the project basics

`NOTES.md` MUST contain sections covering, in this order: an overview of what the project is, the repository layout with the purpose of each tracked file, how the Orca companion configuration is wired (provider connections, models, coordinator model, harness and sandbox, git integration target, limits, and accepted risks), the working agreements those settings impose, and the open items.

#### Scenario: An agent needs to know the harness before acting

- **WHEN** an agent reads only `NOTES.md` to decide how work is executed in this repository
- **THEN** it finds the configured execution harness, sandbox mode, and git integration branch without having to parse `orca-companion.json`

#### Scenario: An agent needs to know the concurrency budget

- **WHEN** an agent reads only `NOTES.md` to decide how many work packages may run at once
- **THEN** it finds the configured work-package concurrency limit and the per-attempt limits for implementation, validation, and recovery

#### Scenario: A reader needs to know what is not built yet

- **WHEN** a reader looks for outstanding recovery work
- **THEN** `NOTES.md` lists the open items, including that the repository has no product code and that `NOTES.md` is the only file this work package covers

### Requirement: Notes stay free of duplicated and drifting content

`NOTES.md` MUST NOT restate the contents of `README.md`, and MUST NOT embed the full text of `orca-companion.json`. It MUST describe configuration by reference, so that a change to the configuration file does not leave contradictory copies behind in the notes.

#### Scenario: Companion configuration changes

- **WHEN** a value in `orca-companion.json` is changed
- **THEN** updating the corresponding description in `NOTES.md` is a one-line edit rather than a rewrite of an embedded copy
- **AND** no duplicate of the configuration document remains in `NOTES.md`

#### Scenario: README identity line

- **WHEN** a reader compares `README.md` and `NOTES.md`
- **THEN** the project title is the only content they share

### Requirement: Notes are verifiable with a read-only command

Acceptance of the notes file MUST be decidable by a read-only shell command that checks the file exists and begins with a top-level heading, so that verification requires no build, dependency install, or test runner.

#### Scenario: Acceptance check runs in a clean worktree

- **WHEN** a shell command asserts that `NOTES.md` exists and that its first line is a top-level heading
- **THEN** the command exits zero on the delivered file and non-zero when the file is missing or lacks the heading

### Requirement: Notes change is confined to the notes file

This capability governs `NOTES.md` only. Satisfying it MUST NOT require creating, editing, renaming, or deleting any other tracked repository file, and MUST NOT add dependencies, build configuration, or runtime behavior.

#### Scenario: Reviewing the change's file impact

- **WHEN** the change is reviewed for the set of repository files it touches
- **THEN** `NOTES.md` is the only product file in that set, and the specification lives under `openspec/changes/` rather than in the product tree
