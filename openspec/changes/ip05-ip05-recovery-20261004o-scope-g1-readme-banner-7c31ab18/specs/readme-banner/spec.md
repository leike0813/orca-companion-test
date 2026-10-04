# Spec Delta

## Purpose

Gives the repository's `README.md` a short, durable status banner, so that a reader or agent opening the first file in a recovered worktree immediately learns that the project is under recovery, that the absence of product code is deliberate rather than a loss, and which files hold the detail — without turning the README into a second copy of the project's documentation.

## ADDED Requirements

### Requirement: README opens with the project title

`README.md` MUST exist at the repository root and MUST begin, on its first line, with a single top-level Markdown heading naming the project. The banner defined by the requirements below MUST appear after that heading, and the heading itself MUST NOT be reordered, reworded, or relocated below the banner.

#### Scenario: Reader opens the repository root

- **WHEN** a user or agent opens `README.md` in a fresh checkout of the worktree
- **THEN** the first line is a top-level Markdown heading naming the project
- **AND** the recovery banner appears immediately beneath it, not before it

### Requirement: Banner declares the project's recovery state

`README.md` MUST contain a banner, rendered as a blockquote block, directly beneath the project title, that states in greppable prose: that the project is a recovered Orca worktree still under recovery, that the repository contains no product code yet by design rather than by loss, and that the outstanding recovery work is specified as OpenSpec changes.

#### Scenario: Cold reader asks whether the repository was lost

- **WHEN** a reader opens `README.md` with no other context
- **THEN** the banner states that the repository is a recovered worktree whose recovery is in progress
- **AND** the banner states that no product code exists yet, so the empty state is not mistaken for missing content

#### Scenario: Agent looks for a codebase to modify

- **WHEN** an agent reads `README.md` to decide what it can build on
- **THEN** it learns from the banner that there is no product code to extend
- **AND** it learns that remaining work is specified under the in-flight change directory rather than left untracked

#### Scenario: Banner is rendered as a distinct block

- **WHEN** the banner is viewed in a Markdown renderer
- **THEN** it renders as a visually distinct block adjacent to the title, clearly separated from ordinary body prose

### Requirement: Banner points to the detail without duplicating it

`README.md` MUST name `NOTES.md` as the place where the project basics, the Orca companion configuration, the working agreements, and the open recovery items are recorded, and MUST name `openspec/changes/` as the place where the outstanding specified work is tracked. The banner MUST be short — no more than five substantive lines — and MUST NOT restate the contents of `NOTES.md`, MUST NOT embed the contents of the Orca companion configuration, and MUST NOT introduce its own section-structured documentation.

#### Scenario: Reader needs configuration detail

- **WHEN** a reader needs to know how the Orca companion is configured or what remains to be done
- **THEN** the banner directs that reader to `NOTES.md` as the single record of those facts
- **AND** the banner itself does not repeat the configuration, the working agreements, or the open items

#### Scenario: Configuration changes later

- **WHEN** a value in the Orca companion configuration is changed by a later work package
- **THEN** no edit to `README.md` is required, because the banner describes the configuration only by reference
- **AND** no contradictory second copy of the configuration exists in the README

#### Scenario: Banner stays short

- **WHEN** the banner is counted
- **THEN** it is at most five substantive lines, so it remains scannable and does not grow into a documentation section

### Requirement: Banner is verifiable with a read-only command

Acceptance of the banner MUST be decidable by a read-only shell command that checks that `README.md` exists, that its first line is a top-level heading, and that a `NOTES.md` pointer is present near the top of the file, so that verification requires no build, dependency install, or test runner.

#### Scenario: Acceptance check runs in a clean worktree

- **WHEN** a read-only shell command asserts that `README.md` exists, that its first line is a top-level heading, and that it references `NOTES.md`
- **THEN** the command exits zero on the delivered file
- **AND** it exits non-zero when the file is missing, when the heading is absent, or when the pointer is missing

### Requirement: Banner change is confined to the README

This capability governs `README.md` only. Satisfying it MUST NOT require creating, editing, renaming, or deleting any other tracked repository file, and MUST NOT add dependencies, build configuration, or runtime behavior.

#### Scenario: Reviewing the change's file impact

- **WHEN** the change is reviewed for the set of repository files it touches
- **THEN** `README.md` is the only product file in that set, and the specification lives under `openspec/changes/` rather than in the product tree

#### Scenario: Reverting the change

- **WHEN** the banner block is removed from `README.md`
- **THEN** the file is a single top-level project heading again, and no other repository file required a corresponding change
