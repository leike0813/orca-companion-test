# Spec Delta

## Purpose

Establishes the structure and required content of the banner-style front page rendered in `README.md`, so every visitor sees a consistent project overview that names the project, signals its demonstration status, points at the canonical entry points, and acknowledges that deeper sections will be added in later changes.

## ADDED Requirements

### Requirement: README.md project title and lead description

`README.md` SHALL contain a level-1 heading (`#`) whose text is the project name `orca-companion`. Immediately after that heading, the file SHALL contain the existing lead description sentence "An e2e-loop demonstration project for the orca-companion agent harness." as the first non-heading paragraph.

#### Scenario: Title heading names the project

- **WHEN** a visitor opens `README.md`
- **THEN** the first heading is `# orca-companion`

#### Scenario: Lead description appears directly after the title

- **WHEN** a visitor reads the lines immediately following the title heading
- **THEN** the first non-empty paragraph is the existing tagline sentence "An e2e-loop demonstration project for the orca-companion agent harness."

### Requirement: README.md status banner

After the lead description, `README.md` SHALL contain a level-2 heading (`##`) titled `Status` followed by at least one paragraph that explicitly states the project is an end-to-end demonstration of the orca-companion agent harness and is not yet a production-ready release. The status paragraph SHALL be the only content under the `## Status` heading before the next level-2 heading.

#### Scenario: Status banner heading is present

- **WHEN** a visitor scans `README.md` for top-level sections
- **THEN** a level-2 heading titled `Status` appears before any other level-2 section

#### Scenario: Status banner explains the demonstration scope

- **WHEN** a visitor reads the `## Status` section
- **THEN** the section contains a sentence that explicitly says the project is an end-to-end demonstration of the orca-companion agent harness and is not a production-ready release

### Requirement: README.md quick links subsection

After the `## Status` section, `README.md` SHALL contain a level-2 heading titled `Quick Links`. Under that heading the file SHALL contain a Markdown bullet list with exactly three bullets, each one a relative link to one of the canonical entry points: `NOTES.md`, `openspec/`, and `orca-companion.json`. Each bullet SHALL contain both the link target and a short label describing what the reader will find there.

#### Scenario: Quick Links heading is present and follows Status

- **WHEN** a visitor scans the top-level sections of `README.md` in order
- **THEN** the `## Quick Links` heading appears immediately after the `## Status` heading

#### Scenario: Quick Links lists the three canonical entry points

- **WHEN** a visitor reads the `## Quick Links` section
- **THEN** the section contains exactly three bullets
- **AND** the three bullets link, in order, to `NOTES.md`, `openspec/`, and `orca-companion.json`
- **AND** each bullet includes a short label naming what the reader will find at that path

### Requirement: README.md project status subsection

After the `## Quick Links` section, `README.md` SHALL contain a level-2 heading titled `Project Status`. Under that heading the file SHALL contain a paragraph that explicitly states that deeper sections (such as Installation, Usage, and Configuration) will be added in later changes, so that no information carried by the previous placeholder italic sentence is lost.

#### Scenario: Project Status heading is present and follows Quick Links

- **WHEN** a visitor scans the top-level sections of `README.md` in order
- **THEN** the `## Project Status` heading appears immediately after the `## Quick Links` heading

#### Scenario: Project Status explains follow-up sections

- **WHEN** a visitor reads the `## Project Status` section
- **THEN** the section states that deeper sections such as Installation, Usage, and Configuration will be added in later changes
- **AND** the previous placeholder italic sentence ("_More sections (Installation, Usage, etc.) will be added in later changes._") no longer appears anywhere in the file

### Requirement: README.md formatting and content rules

`README.md` SHALL be valid GitHub-flavored Markdown. Section headings SHALL use the documented level markers (`#` for the title, `##` for top-level sections). The file SHALL contain no raw HTML tags or inline scripts. The file SHALL stay under 200 lines until a follow-up change explicitly expands it.

#### Scenario: Section markers follow the documented hierarchy

- **WHEN** a parser scans `README.md` for headings
- **THEN** the level-1 heading uses exactly one `#` character
- **AND** every level-2 heading uses exactly two `#` characters

#### Scenario: No raw HTML or scripts appear in README.md

- **WHEN** a reviewer greps `README.md` for `<script`, `<iframe`, or other raw HTML tags
- **THEN** no matches are found

#### Scenario: README.md stays under the size limit

- **WHEN** a contributor counts the lines in `README.md`
- **THEN** the total line count is at most 200

### Requirement: README.md scope discipline

This change SHALL modify `README.md` only. No other tracked file in the repository SHALL be created, modified, or removed by this change. References to `NOTES.md`, `openspec/`, and `orca-companion.json` SHALL be descriptive text inside `README.md` and SHALL NOT alter those referenced files.

#### Scenario: Only README.md is touched by the change

- **WHEN** a reviewer runs `git status --porcelain` after applying this change
- **THEN** the only entry is `README.md`
- **AND** no other file appears as added, modified, or deleted

#### Scenario: Referenced files are described, not modified

- **WHEN** a reviewer reads `README.md`
- **THEN** the references to `NOTES.md`, `openspec/`, and `orca-companion.json` appear only as descriptive text inside the `## Quick Links` bullets
- **AND** `git diff NOTES.md openspec/config.yaml orca-companion.json` reports no changes
