# Spec Delta

## Purpose

Define the banner section that the repository-level `README.md` carries at the
top of the document, so a reader immediately learns what kind of project this
is and how complete the rest of the file is.

## ADDED Requirements

### Requirement: README carries a banner section

`README.md` MUST contain a banner section positioned directly below the document
title and above the project description prose, and the banner MUST contain a
status statement and at least one sentence stating what the repository is for.

#### Scenario: Reader opens the repository landing page

- **WHEN** a reader opens `README.md` at the repository root
- **THEN** the text below the title shows a banner carrying a status statement
  and a sentence describing what the repository is for, before any other prose

#### Scenario: Banner is added to an existing README

- **WHEN** a README that has no banner exists and this change is implemented
- **THEN** the banner is inserted below the title and above the existing
  description paragraph, and the existing paragraph is left in place below it

### Requirement: Banner states the project is a demonstration

The banner MUST identify the repository as a demonstration or harness project
in plain text, and MUST NOT depend on a remote image, badge service, or any other
network resource to convey that status.

#### Scenario: Banner is read without network access

- **WHEN** a reader views `README.md` with no network access
- **THEN** the status statement is still readable as text in the document, and
  no part of the banner is missing because a remote resource failed to load

### Requirement: Banner sets expectations about the rest of the document

The banner MUST make clear that the remaining sections of `README.md` are not
yet complete, so a reader does not treat the absence of Installation or Usage
guidance as an oversight.

#### Scenario: Reader looks for installation guidance

- **WHEN** a reader scans the banner for installation or usage instructions
- **THEN** the banner tells the reader that those sections are still to be added

### Requirement: Banner appears exactly once

`README.md` MUST contain exactly one banner section, so a reader does not
encounter two competing statements of the project's purpose.

#### Scenario: Whole document is scanned for banners

- **WHEN** a reader reads `README.md` from top to bottom
- **THEN** exactly one section presents itself as the banner below the title
