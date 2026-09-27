# Spec Delta

## Purpose

The `notes-basics` capability delivers a top-level `NOTES.md` that orients
readers to the orca-companion repository: what the project is for, what the
harness configuration file controls, and where the existing `README.md` and
`openspec/` workflow live.

## ADDED Requirements

### Requirement: Top-Level NOTES.md Orientation File

The orca-companion repository SHALL provide a `NOTES.md` file at the
repository root. The file SHALL be plain Markdown and SHALL exist as a
non-empty file readable from the repository root.

#### Scenario: NOTES.md exists at the repository root

- **WHEN** a reader lists the contents of the repository root
- **THEN** `NOTES.md` is present alongside `README.md` and
  `orca-companion.json`

### Requirement: NOTES.md Content Describes Repository Purpose

The top-level `NOTES.md` SHALL describe what the orca-companion repository
is for, identify `orca-companion.json` as the harness configuration file,
and point to the existing `README.md` and the `openspec/` workflow directory
as places to learn more. The descriptions SHALL be written in plain
prose that any reader can understand without prior project context.

#### Scenario: NOTES.md explains the repository's purpose

- **WHEN** a reader opens `NOTES.md`
- **THEN** the document contains a short statement describing the purpose
  of the orca-companion repository

#### Scenario: NOTES.md describes the harness configuration

- **WHEN** a reader opens `NOTES.md`
- **THEN** the document names `orca-companion.json` and explains at a
  high level that it configures the orca-companion harness

#### Scenario: NOTES.md points at the README and openspec workflow

- **WHEN** a reader opens `NOTES.md`
- **THEN** the document references both `README.md` and the `openspec/`
  directory so the reader knows where additional documentation and
  specifications live

### Requirement: NOTES.md Contains No Code or Tooling Changes

The top-level `NOTES.md` SHALL be a documentation-only addition. It SHALL
NOT introduce executable code, modify configuration files, alter schemas,
or change the behavior of any existing tooling. The change SHALL NOT
modify, rename, or remove `README.md`, `orca-companion.json`, or any
file inside `openspec/`.

#### Scenario: NOTES.md leaves other repository files untouched

- **WHEN** the change that produces `NOTES.md` is applied
- **THEN** `README.md` and `orca-companion.json` retain their prior
  contents and the `openspec/` directory is unchanged apart from the
  specification describing this capability
