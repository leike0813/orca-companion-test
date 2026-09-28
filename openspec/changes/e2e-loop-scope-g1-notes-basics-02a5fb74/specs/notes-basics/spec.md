# Spec Delta

## Purpose

Documents the developer-facing project notes that `NOTES.md` MUST carry so
the repository has a single, machine-discoverable place for scope, intent,
and working conventions that complements (but does not duplicate) the
user-facing `README.md`.

## ADDED Requirements

### Requirement: NOTES.md presence

`NOTES.md` MUST exist at the repository root (the same directory that
contains `README.md`) and MUST be a non-empty UTF-8 Markdown file of at
least 64 bytes.

#### Scenario: NOTES.md is present at the repository root
- **WHEN** a contributor lists the files in the repository root directory
- **THEN** `NOTES.md` is present alongside `README.md` and reports a size
  greater than zero bytes.

#### Scenario: NOTES.md parses as Markdown
- **WHEN** a reader opens `NOTES.md` directly with `cat`, a Markdown
  viewer, or any common Markdown parser
- **THEN** the file opens without parser error and displays visible prose
  to the reader.

### Requirement: NOTES.md mandatory sections

`NOTES.md` MUST contain the level-2 Markdown headings `## Scope`,
`## Intent`, and `## Conventions` in that exact relative order. Each
heading MUST be followed by at least one paragraph of real prose (no
placeholder fragments such as `TBD`, `TODO`, `lorem ipsum`, or an
empty section).

#### Scenario: Scope section describes in-scope work
- **WHEN** a reader reads the `## Scope` heading and the prose directly
  beneath it
- **THEN** the prose names what is currently in scope for the
  orca-companion project and names nothing that is explicitly out of
  scope.

#### Scenario: Intent section explains the project's reason to exist
- **WHEN** a reader reads the `## Intent` heading and the prose directly
  beneath it
- **THEN** the prose explains, in declarative form, why the
  orca-companion project exists and what it aims to demonstrate, so a
  new contributor can understand its purpose from `NOTES.md` alone.

#### Scenario: Conventions section lists developer-facing rules
- **WHEN** a reader reads the `## Conventions` heading and the prose
  directly beneath it
- **THEN** the prose declares at least one developer-facing convention
  that contributors MUST observe when working in this repository,
  phrased as a rule rather than as a suggestion.

### Requirement: NOTES.md cross-link to README.md

`NOTES.md` MUST contain a Markdown link whose link label is non-empty
and whose link target is the relative string `README.md`.

#### Scenario: Reader can jump from NOTES.md to README.md
- **WHEN** a reader renders `NOTES.md` in a Markdown viewer such as a
  code-hosting platform or `grip`
- **THEN** the rendered output contains a clickable link whose target
  resolves to `README.md` at the repository root.

#### Scenario: NOTES.md does not duplicate README.md prose
- **WHEN** the prose blocks of `NOTES.md` are compared against the prose
  blocks of `README.md`
- **THEN** no prose block in `NOTES.md` is an exact byte-for-byte copy
  of any prose block in `README.md`; `NOTES.md` complements rather than
  mirrors the user-facing overview.
