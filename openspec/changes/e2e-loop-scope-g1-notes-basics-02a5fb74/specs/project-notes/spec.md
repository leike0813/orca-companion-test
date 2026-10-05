# Spec Delta

## Purpose

Define the single root-level notes document that records what this project is, how it is laid out, which conventions it follows, and how work is normally done, so that anyone joining the project can get oriented without reconstructing the context by hand.

## ADDED Requirements

### Requirement: Root-level notes document exists
The repository SHALL contain a file named `NOTES.md` at its root, the file SHALL be non-empty, and its content SHALL be valid UTF-8 text.

#### Scenario: Reader looks for the notes at the repository root
- **WHEN** a reader checks for `NOTES.md` in the repository root directory
- **THEN** the file exists, contains at least one non-whitespace character, and is readable as UTF-8 text

#### Scenario: Notes are the only documentation file this change introduces
- **WHEN** the change is inspected after implementation
- **THEN** `NOTES.md` is present at the repository root and no other file outside this change's specification unit was created, modified, or deleted

### Requirement: Notes document has a fixed section structure
`NOTES.md` SHALL begin with exactly one level-one heading that names the project, and SHALL contain a level-two section for each of the headings `Purpose`, `Project Layout`, `Conventions`, and `Workflow`, in that order. Each level-two section SHALL contain at least one line of body text that is not itself a heading.

#### Scenario: Reader scans the section headings
- **WHEN** a reader lists the level-one and level-two headings of `NOTES.md`
- **THEN** there is exactly one level-one heading, and the level-two headings are `Purpose`, `Project Layout`, `Conventions`, and `Workflow` appearing once each in that order

#### Scenario: Reader opens a section and expects content
- **WHEN** a reader reads any one of the four level-two sections
- **THEN** that section contains at least one line of non-heading body text, so no section is an empty placeholder

#### Scenario: A required section is missing
- **WHEN** `NOTES.md` omits any one of the four required level-two sections, or repeats one of them
- **THEN** a structural check of the document fails and the document is not accepted as complete

### Requirement: Notes describe the repository accurately
Every repository-relative path that `NOTES.md` presents as an existing file or directory SHALL exist in the repository working tree, and the `Project Layout` section SHALL mention at least one existing entry. Path references SHALL be written relative to the repository root, without a leading `./` or `/`.

#### Scenario: Reader follows a path from the layout section
- **WHEN** a reader resolves a repository-relative path taken from the `Project Layout` section against the working tree
- **THEN** the resolved path exists

#### Scenario: Notes claim a path that no longer exists
- **WHEN** a path referenced by `NOTES.md` is absent from the working tree
- **THEN** a path-reference check of the document fails and the document is not accepted as complete

#### Scenario: Notes contain no path references at all
- **WHEN** the `Project Layout` section names no existing repository entry
- **THEN** a path-reference check of the document fails, because the layout section would be describing nothing
