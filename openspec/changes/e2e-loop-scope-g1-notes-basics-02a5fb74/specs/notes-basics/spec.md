# Spec Delta

## Purpose

Establishes the baseline structure of `NOTES.md` so the project has a canonical place to record layout, conventions, and follow-up items that downstream changes can rely on.

## ADDED Requirements

### Requirement: NOTES.md exists at the repository root

The repository SHALL contain a `NOTES.md` file at the top level, alongside `README.md`, `orca-companion.json`, and `.gitignore`.

#### Scenario: NOTES.md is present in the working tree

- **WHEN** a developer lists the top-level entries of the repository
- **THEN** `NOTES.md` appears among the listed files

### Requirement: NOTES.md documents the project layout

`NOTES.md` MUST contain a section titled "Project Layout" that names every top-level file (`README.md`, `NOTES.md`, `orca-companion.json`, `.gitignore`) and gives a one-sentence role for each.

#### Scenario: Project Layout section is rendered with all four entries

- **WHEN** a developer opens `NOTES.md`
- **THEN** a heading titled "Project Layout" is followed by entries that mention each of `README.md`, `NOTES.md`, `orca-companion.json`, and `.gitignore`

### Requirement: NOTES.md records baseline conventions

`NOTES.md` MUST contain a section titled "Conventions" that states the baseline expectations for future changes: every change proposes a spec before implementation, scope envelopes constrain file edits, and `README.md` remains the only public-facing overview.

#### Scenario: Conventions section lists the three baseline expectations

- **WHEN** a developer opens `NOTES.md`
- **THEN** a heading titled "Conventions" is followed by content that mentions spec-first changes, scope envelopes, and the public role of `README.md`
