# Spec — readme-banner

## ADDED Requirements

### Requirement: README banner section

`README.md` SHALL exist at the repository root and SHALL begin with a banner section that identifies the project. The banner MUST be the first content in the file (no leading blank lines or front-matter) and MUST use a top-level Markdown heading (`#`) followed by a short descriptive subtitle.

#### Scenario: Project root contains README.md

- **WHEN** a reader opens the repository root
- **THEN** a file named `README.md` is present
- **AND** the file's first non-empty line is a top-level Markdown heading (`# ...`)

#### Scenario: Banner uses project identity and subtitle

- **WHEN** a reader reads the banner section
- **THEN** the heading names the project
- **AND** a subtitle (one short paragraph or a tagline line) appears directly under the heading

### Requirement: Banner is the only content for this change

For this change, `README.md` MUST contain only the banner section plus, at most, a single placeholder line indicating that further content will be added in later changes. No additional sections (Features, Installation, Usage, Contributing, License, etc.) SHALL be introduced by this change.

#### Scenario: Minimal content scope

- **WHEN** the change is applied
- **THEN** `README.md` contains the banner section
- **AND** `README.md` does not introduce any new top-level sections beyond the banner

#### Scenario: Future extensions are deferred

- **WHEN** a reader looks for follow-up sections such as "Installation" or "Usage"
- **THEN** they do not appear in this change
- **AND** the only indication of future content is a single placeholder line, if any

### Requirement: Banner content is plain Markdown

The banner MUST consist of plain Markdown (ATX headings, paragraphs, and optional emphasis). It MUST NOT embed HTML, raw images, badges, or third-party widgets in this change.

#### Scenario: No embedded HTML or assets

- **WHEN** the banner is rendered
- **THEN** the rendered output is plain Markdown text
- **AND** it contains no `<` HTML tags, no `![...]()` images, and no badge/shield snippets
