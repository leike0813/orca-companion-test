# Spec Delta

## Purpose

Defines the banner that opens the project landing page, so a first-time reader immediately
learns the project name, its purpose, and its lifecycle status, and so the banner's presence
and shape can be checked mechanically.

## ADDED Requirements

### Requirement: README opens with a banner
The project landing page SHALL render a banner as the first content of the file, before any
project title, and the banner SHALL be separated from the following content by a blank line.

#### Scenario: First non-blank line belongs to the banner
- **WHEN** a reader or checker inspects the opening of the landing page
- **THEN** the first non-blank line is the banner's opening line and no project title precedes it

#### Scenario: Banner is followed by a blank line
- **WHEN** the banner block ends
- **THEN** exactly one blank line separates it from the following project title

### Requirement: Banner identifies the project
The banner SHALL name the project explicitly and SHALL state its purpose in a single line of
plain text that does not rely on images, badges, or HTML.

#### Scenario: Project name is stated as text
- **WHEN** a reader views the landing page as plain text
- **THEN** the banner contains the project name and a one-line purpose statement

### Requirement: Banner declares lifecycle status
The banner SHALL contain exactly one status line that labels the project's lifecycle state,
and that status line SHALL use a fixed, greppable `**Status:**` label prefix.

#### Scenario: Status line is present and greppable
- **WHEN** a checker searches the landing page for the `**Status:**` label
- **THEN** exactly one status line is found and it appears inside the banner block

#### Scenario: Status is a declared value, not free prose
- **WHEN** the status line is read
- **THEN** it names one lifecycle state from the project's declared set of values

### Requirement: Banner stays a banner
The banner SHALL remain a short introductory block and SHALL NOT displace the project title or
any existing content below it.

#### Scenario: Existing project title survives
- **WHEN** the banner is present
- **THEN** the original top-level project title is still present below the banner

#### Scenario: Banner stays bounded in size
- **WHEN** the banner block is measured
- **THEN** it occupies no more than ten non-blank lines
