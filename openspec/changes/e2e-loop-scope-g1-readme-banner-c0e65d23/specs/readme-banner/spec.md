# Spec Delta

## Purpose

Define the status banner in the project's `README.md` so that a reader learns the project's maturity before reading any other content, and so the statement stays consistent across future edits.

## ADDED Requirements

### Requirement: Status Banner Directly Below The Title
`README.md` SHALL begin with the `# orca-companion` level-one heading, and the status banner SHALL be the first content that follows it, separated only by blank lines and before any other prose.

#### Scenario: Banner position in the file
- **WHEN** `README.md` is read from the top
- **THEN** the first line is the `# orca-companion` heading, and only blank lines separate it from the banner, which precedes every other line of prose in the file

#### Scenario: Banner is missing or misplaced
- **WHEN** the banner is absent, or appears after the descriptive paragraph
- **THEN** `README.md` does not satisfy this requirement

#### Scenario: Banner renders as part of the title
- **WHEN** the banner line is written with no blank line separating it from the `# orca-companion` heading
- **THEN** a Markdown renderer does not treat the banner as a separate block, and `README.md` does not satisfy this requirement

### Requirement: Banner Is A Single Blockquote Line
The banner SHALL be written as one line prefixed with `> `, and SHALL NOT contain a second blockquote line or a bullet list.

#### Scenario: Banner form
- **WHEN** the banner line is inspected
- **THEN** it is a single `>`-prefixed line of plain prose

### Requirement: Banner States Demonstration Status
The banner SHALL state that the project is a demonstration or e2e exercise and SHALL state that it is not ready for production use.

#### Scenario: Reader learns the maturity
- **WHEN** a reader looks only at the banner
- **THEN** they can tell the project is a demonstration and that production use is not supported

#### Scenario: Status wording is dropped
- **WHEN** the banner no longer mentions demonstration status or production readiness
- **THEN** the banner does not satisfy this requirement
