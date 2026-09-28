# Spec Delta

## Purpose

Define the contract for the status banner at the top of `README.md`, so that every
reader learns the repository is an e2e-loop demonstration of the `orca-companion` agent
harness and carries no stability guarantees, without having to read past the title.

## ADDED Requirements

### Requirement: Banner is the first content after the title
`README.md` SHALL place its status banner immediately after the single level-1 Markdown
title, ahead of the project's prose description, so that it is visible without
scrolling or reading further into the document.

#### Scenario: Reader sees the status on the first screen
- **WHEN** a reader opens `README.md` at its beginning
- **THEN** the banner appears directly below the level-1 title and before any other prose

### Requirement: Banner states the demonstration status
The banner SHALL state, in its own words, that the repository exists to demonstrate the
`orca-companion` agent harness rather than to serve as a usable product.

#### Scenario: Status is unambiguous without outside context
- **WHEN** a reader reads only the banner text
- **THEN** it identifies the repository as an e2e-loop demonstration of the agent harness

### Requirement: Banner disclaims stability and support
The banner SHALL state that the repository offers no stability, compatibility, or
support guarantees, so a reader does not infer a maintenance commitment from the file's
existence.

#### Scenario: Reader does not mistake the project for supported
- **WHEN** a reader reads only the banner text
- **THEN** it says that the repository carries no such guarantees

### Requirement: Banner uses plain Markdown that renders consistently
The banner SHALL be expressed with Markdown constructs that render the same on a GitHub
web view and in a plain-text read of the file, and SHALL NOT rely on colour, badges,
images, or HTML to carry its meaning.

#### Scenario: Meaning survives a plain-text read
- **WHEN** the file is read as plain text with all markup visible
- **THEN** the banner's statement is still legible without interpreting rendered HTML,
  images, or badge services

### Requirement: Exactly one banner
`README.md` SHALL contain exactly one status banner, and the banner SHALL NOT be repeated
as a comment or duplicated later in the document.

#### Scenario: No duplicated warnings
- **WHEN** the whole of `README.md` is searched for the banner statement
- **THEN** it is found exactly once

### Requirement: No deferred-sections placeholder
`README.md` SHALL NOT carry the trailing sentence that defers sections such as
Installation and Usage to later changes, because the banner supersedes it as the
statement of scope.

#### Scenario: Contradicting scope statements removed
- **WHEN** the whole of `README.md` is read
- **THEN** it no longer states that further sections will be added in later changes
