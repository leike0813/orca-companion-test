# Spec Delta

## Purpose

Defines the at-a-glance contract for the repository's `README.md` so
that any visitor — human or agent — immediately sees an internal-use
banner identifying the project as the `orca-companion` agent-harness
e2e-loop demonstration target before reading any other content.

## ADDED Requirements

### Requirement: README.md MUST open with an internal-use banner
The repository's `README.md` MUST contain, as the very first content
block after the project title, a clearly delimited banner that
identifies the repository as the `orca-companion` agent-harness
e2e-loop demonstration target and signals that the repository is _not_
a real product.

#### Scenario: A visitor opens README.md and reads the first content
- **WHEN** a visitor opens `README.md` at the repository root
- **THEN** the first content block under the `# orca-companion` title
      is a banner, not the existing one-line description or any other
      prose
- **AND** that banner names the project as the `orca-companion`
      agent-harness e2e-loop demonstration target

#### Scenario: A visitor scans the banner for out-of-scope signals
- **WHEN** a visitor reads the banner to confirm the repository is _not_
      a real product
- **THEN** the banner states that the repository has no install path,
      no production code, and no end-user surface
- **AND** the banner is phrased as a notice (for example with an
      explicit "not", "demo", or "internal" cue) rather than a neutral
      description

### Requirement: README banner MUST stay plain GitHub-flavored Markdown
The internal-use banner at the top of `README.md` MUST render as plain
GitHub-flavored Markdown with no HTML, no images, no fenced
build-step directives, and no YAML / TOML front-matter.

#### Scenario: A visitor renders README.md on GitHub
- **WHEN** `README.md` is rendered on GitHub (or any standard CommonMark
      renderer)
- **THEN** the banner appears as plain text and headings only
- **AND** the banner contains no HTML tags, no image syntax
      (`![](...)` or `<img>`), and no fenced code blocks longer than
      a short illustrative snippet

#### Scenario: A maintainer inspects README.md on the file system
- **WHEN** a maintainer opens `README.md` in a plain text editor
- **THEN** the file contains no YAML or TOML front-matter at the top
- **AND** the banner is delimited by a Markdown heading or blockquote,
      not by HTML or image syntax

### Requirement: README banner MUST be the only added README content
The change that introduces the banner MUST add or modify only
`README.md` at the repository root; every other repository file MUST
remain byte-identical to the pre-change state.

#### Scenario: A validator diffs the worktree against the baseline
- **WHEN** the change's working tree is diffed against the baseline
      commit declared in the Work Package
- **THEN** the only modified file is `README.md`
- **AND** no new files have been added outside `README.md` and the
      `openspec/changes/...` artefacts created by this change
