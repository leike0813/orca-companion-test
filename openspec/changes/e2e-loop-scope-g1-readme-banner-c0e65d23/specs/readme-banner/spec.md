# Spec Delta

## Purpose

Define the status banner in the project's `README.md` so that a reader learns the project's maturity before reading any other content, and so the statement stays consistent across future edits.

## ADDED Requirements

### Requirement: Status Banner Directly Below The Title
`README.md` SHALL contain a status banner on the line immediately after the `# orca-companion` level-one heading, and before any other content.

#### Scenario: Banner position in the file
- **WHEN** `README.md` is read from the top
- **THEN** the first line is the `# orca-companion` heading and the banner follows it directly, with no other prose in between

#### Scenario: Banner is missing or misplaced
- **WHEN** the banner is absent, or appears after the descriptive paragraph
- **THEN** `README.md` does not satisfy this requirement

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
