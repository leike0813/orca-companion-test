## ADDED Requirements

### Requirement: Repository MUST ship a NOTES.md maintainer note
The `orca-companion` repository MUST ship a `NOTES.md` file at the
repository root that gives a maintainer a quick, accurate summary of why
the repository exists and what it deliberately leaves to other layers.

#### Scenario: Maintainer opens NOTES.md to learn the project's purpose
- **WHEN** a maintainer opens `NOTES.md` from the repository root
- **THEN** the file renders as GitHub-flavored Markdown
- **AND** the first section is a clearly labelled "Purpose" section
- **AND** that section states that the repository exists as an
      end-to-end demonstration target for the `orca-companion` agent
      harness

#### Scenario: Maintainer looks for an out-of-scope statement
- **WHEN** a maintainer reads `NOTES.md` to confirm what the repository
      is _not_
- **THEN** the file contains a section labelled "What this repo is not"
      (or equivalent heading)
- **AND** that section enumerates at least the following explicitly
      out-of-scope items: production code, real install instructions,
      multi-component configurations, and credentials / secrets

#### Scenario: Maintainer looks for where follow-up work is tracked
- **WHEN** a maintainer reads `NOTES.md` to find where future iterations
      are tracked
- **THEN** the file contains a section labelled "Where follow-up work
      lives" (or equivalent heading)
- **AND** that section points at the GitHub issues and follow-up
      OpenSpec changes that drive future iterations of the demo

#### Scenario: NOTES.md stays a single root-level plain Markdown file
- **WHEN** the repository is inspected at any commit that includes this
      change
- **THEN** there is exactly one `NOTES.md` file at the repository root
- **AND** the file contains no YAML or TOML front-matter
- **AND** the file contains no embedded HTML or build-step directives
