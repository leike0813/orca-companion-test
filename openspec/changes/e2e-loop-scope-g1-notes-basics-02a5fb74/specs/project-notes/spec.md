# Spec Delta

## Purpose

Define the existence, location, format, and minimum structural sections of a repository-rooted Markdown notes document so contributors and downstream tooling have a single canonical place to read project orientation, conventions, and pointers.

## ADDED Requirements

### Requirement: NOTES.md existence and location

The repository SHALL contain a file named `NOTES.md` at the repository root (the same directory that contains `README.md`). The file SHALL be tracked by Git and SHALL NOT be excluded by `.gitignore`. No other path SHALL be accepted as a substitute for `NOTES.md` for this capability.

#### Scenario: NOTES.md exists at the repository root
- WHEN a contributor or tool lists the contents of the repository root
- THEN `NOTES.md` SHALL be present as a tracked file alongside `README.md`

#### Scenario: NOTES.md is not excluded by .gitignore
- WHEN the repository is cloned with a fresh working tree
- THEN `NOTES.md` SHALL appear in the working tree (it is not gitignored)

### Requirement: NOTES.md format

`NOTES.md` SHALL be a plain UTF-8 Markdown file using GitHub-flavored Markdown syntax. It SHALL be readable as Markdown without preprocessing and SHALL NOT depend on build steps, templates, or generators to render. The file SHALL begin with a single top-level Markdown title (`# Title`) as its first non-blank content line.

#### Scenario: NOTES.md opens with a top-level title
- WHEN `NOTES.md` is opened
- THEN its first non-blank line SHALL be a Markdown H1 heading (`# ...`)

#### Scenario: NOTES.md is plain Markdown
- WHEN `NOTES.md` is rendered by any standard Markdown parser
- THEN it SHALL render as a Markdown document without requiring preprocessing

### Requirement: NOTES.md required sections

`NOTES.md` SHALL contain exactly four top-level sections, in this order: `Overview`, `Conventions`, `Pointers`, and `Open Questions`. Each section SHALL be introduced by a level-2 Markdown heading (`## Section Name`). The `Open Questions` section MAY contain a single paragraph stating that there are no open questions at this time.

#### Scenario: NOTES.md lists all required sections in order
- WHEN a reader scans the level-2 headings of `NOTES.md`
- THEN the headings SHALL appear in this order: `Overview`, `Conventions`, `Pointers`, `Open Questions`

#### Scenario: Each required section is non-empty
- WHEN a reader opens `NOTES.md`
- THEN each of `Overview`, `Conventions`, `Pointers`, and `Open Questions` SHALL contain at least one paragraph of content

### Requirement: NOTES.md scope boundary

`NOTES.md` SHALL describe only the project's orientation, conventions, and pointers. It SHALL NOT duplicate the content of `README.md`, SHALL NOT introduce installation or usage instructions, and SHALL NOT introduce CI, build, or release-process content. Later changes MAY extend `NOTES.md` with additional subsections under the existing top-level sections.

#### Scenario: NOTES.md does not duplicate README.md
- WHEN a reader compares `README.md` and `NOTES.md`
- THEN `NOTES.md` SHALL contain no sentence that is also present verbatim in `README.md`

#### Scenario: NOTES.md defers installation and usage to later changes
- WHEN a reader searches `NOTES.md` for installation or usage steps
- THEN the document SHALL NOT contain step-by-step installation or usage instructions in this change
