# Spec Delta

## Purpose
Defines the canonical `NOTES.md` baseline notes file for the orca-companion project. The capability locks down which sections must be present, how the notes file relates to OpenSpec changes and the orca harness descriptor, and how subsequent changes may amend the file.

## ADDED Requirements

### Requirement: NOTES.md Exists At Repository Root

The repository SHALL publish a notes file at `NOTES.md` (relative to the worktree root) so the canonical operating notes for orca-companion have a single, stable location.

#### Scenario: NOTES.md Is Committed
- **WHEN** a reviewer inspects the worktree at the change's baseline commit
- **THEN** `NOTES.md` exists at the repository root and is tracked in git

#### Scenario: NOTES.md Path Is Stable
- **WHEN** a downstream change references the notes file
- **THEN** the path `NOTES.md` resolves to the same file in every worktree of the project

### Requirement: NOTES.md Has Canonical Sections

`NOTES.md` SHALL contain the following top-level sections, in this order: `## Project Overview`, `## Repository Layout`, `## Running the e2e Loop`, `## Conventions`, `## Troubleshooting`, `## Future Work`. Each section SHALL be non-empty.

#### Scenario: All Canonical Sections Are Present
- **WHEN** a reader scans `NOTES.md` from top to bottom
- **THEN** the six canonical headings appear in the declared order and each section contains at least one paragraph or list

#### Scenario: Section Order Is Stable
- **WHEN** tooling or downstream changes parse `NOTES.md`
- **THEN** the section order matches the canonical order so that anchors and references remain valid across revisions

### Requirement: NOTES.md Documents the e2e Loop

The `## Running the e2e Loop` section SHALL describe how the orca harness consumes `orca-companion.json`, how work packages are dispatched against the OpenSpec change under `openspec/changes/`, and how each dispatch reports completion through `orca orchestration send --type worker_done`.

#### Scenario: Loop Narrative Is Traceable
- **WHEN** a contributor reads `## Running the e2e Loop`
- **THEN** they can name the harness descriptor, the OpenSpec change layout, and the worker-done report path without consulting external documentation

### Requirement: NOTES.md Lists Cross-References

`NOTES.md` SHALL cross-reference the OpenSpec directory (`openspec/`), the harness descriptor (`orca-companion.json`), and the existing `README.md` so readers can navigate between narrative, configuration, and specification artifacts.

#### Scenario: Cross-References Are Resolvable
- **WHEN** a reader follows a relative path mentioned in `NOTES.md`
- **THEN** the referenced file or directory exists in the same worktree

### Requirement: NOTES.md Edits Respect Scope Envelopes

Edits to `NOTES.md` SHALL only be applied by a change whose scope envelope explicitly includes `NOTES.md`. Any change that lists `NOTES.md` outside its declared scope envelope SHALL be rejected by Admission with `scope_envelope_exceeded`.

#### Scenario: In-Scope Edit Is Admitted
- **WHEN** a change proposal lists `NOTES.md` in `scopeEnvelope.include`
- **THEN** Admission accepts the change and the validator may amend `NOTES.md`

#### Scenario: Out-of-Scope Edit Is Rejected
- **WHEN** a change proposal modifies `NOTES.md` without listing it in `scopeEnvelope.include`
- **THEN** Admission rejects the change with `scope_envelope_exceeded` and the validator does not touch `NOTES.md`

### Requirement: NOTES.md Survives Later Changes

`NOTES.md` SHALL remain parseable Markdown after any subsequent change that legitimately amends it: headings remain well-formed, code fences balance, and no canonical section is removed or reordered.

#### Scenario: Markdown Stays Well-Formed
- **WHEN** the validator checks `NOTES.md` after an in-scope amendment
- **THEN** the file contains six balanced `##` headings in the canonical order with no stray unclosed fences
