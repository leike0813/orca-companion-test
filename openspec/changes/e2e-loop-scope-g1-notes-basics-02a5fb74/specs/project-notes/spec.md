# Spec Delta

## Purpose

Establishes the shape and minimum content of the root-level `NOTES.md` so every contributor records project observations, handoff context, and open questions in a consistent place.

## ADDED Requirements

### Requirement: NOTES.md location and existence

The repository SHALL contain a tracked Markdown file named `NOTES.md` at the repository root, alongside `README.md` and `orca-companion.json`. The file SHALL be plain UTF-8 Markdown with a `.md` extension and SHALL be present after this change is applied.

#### Scenario: NOTES.md is present at the repository root

- **WHEN** a contributor lists tracked files at the repository root
- **THEN** `NOTES.md` is included in the listing

#### Scenario: NOTES.md is not nested under a directory

- **WHEN** a contributor searches for any `NOTES.md` outside the repository root
- **THEN** no other `NOTES.md` files exist anywhere else in the repository tree

### Requirement: NOTES.md required top-level sections

`NOTES.md` SHALL contain exactly three top-level sections in this order: `## Overview`, `## Conventions`, and `## Open Items`. Each section SHALL contain at least one non-empty line of content so the file is never a bare heading list.

#### Scenario: Overview section describes the project

- **WHEN** a reader opens `NOTES.md` and reads the `## Overview` section
- **THEN** the section states, in two or three sentences, what the orca-companion project is for so a new reader does not have to re-read `README.md`

#### Scenario: Conventions section states the note-taking rules

- **WHEN** a reader opens `NOTES.md` and reads the `## Conventions` section
- **THEN** the section names, at minimum, the entry format (dated headings), the allowed content type (Markdown only), and the rule that new entries are appended at the end

#### Scenario: Open Items section explains how to add new items

- **WHEN** a reader opens `NOTES.md` and reads the `## Open Items` section
- **THEN** the section contains at least one bullet explaining how future contributors should append new open items, even when no real items have been logged yet

### Requirement: NOTES.md content stability

The first commit that introduces `NOTES.md` SHALL NOT include any personal data, secrets, credentials, or absolute filesystem paths. Subsequent edits SHALL keep the file under 200 lines until a follow-up change explicitly expands it.

#### Scenario: Initial NOTES.md stays under the size limit

- **WHEN** a contributor counts the lines in the initial `NOTES.md`
- **THEN** the total line count is at most 200

#### Scenario: Initial NOTES.md contains no secrets

- **WHEN** a reviewer greps `NOTES.md` for typical secret markers (API keys, bearer tokens, password literals)
- **THEN** no matches are found

### Requirement: NOTES.md formatting rules

All content inside `NOTES.md` SHALL be valid GitHub-flavored Markdown. Top-level section markers SHALL use exactly two `#` characters (`##`). Subsection markers, when used, SHALL use three `#` characters (`###`). No HTML tags or inline scripts SHALL appear in the file.

#### Scenario: Section headings use the two-hash marker

- **WHEN** a parser scans `NOTES.md` for headings
- **THEN** every level-2 heading begins with exactly `## ` followed by a non-empty title

#### Scenario: No HTML tags appear in NOTES.md

- **WHEN** a reviewer greps `NOTES.md` for `<script`, `<iframe`, or raw HTML tags
- **THEN** no matches are found

