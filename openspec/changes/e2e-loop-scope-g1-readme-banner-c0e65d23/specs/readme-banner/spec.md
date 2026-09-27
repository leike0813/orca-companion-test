# Spec Delta

## Purpose

Defines the structure and baseline content of the introductory banner block at the top of the project README so the project's identity, tagline, and status are described consistently across changes.

## ADDED Requirements

### Requirement: README banner block exists at the top of the file

`README.md` MUST contain a banner block at the top of the file consisting of exactly three Markdown constructs, in this order: an H1 title, a non-empty prose paragraph acting as the tagline, and a single italic status banner line. The banner block MUST appear before any `## H2` heading or other Markdown section.

#### Scenario: Banner is the first content in the file
- **WHEN** a reader opens `README.md` from the repository root
- **THEN** the first non-blank construct in the file is the H1 title, immediately followed by the tagline paragraph and the status banner line, with no `## H2` heading appearing before any of them

### Requirement: Banner H1 title identifies the project

The banner's H1 title MUST be the literal string `orca-companion` so that the project name is unambiguous across renderers and downstream tools.

#### Scenario: H1 title is the project name
- **WHEN** a reader inspects the first non-blank line of `README.md`
- **THEN** the line is a level-1 Markdown heading whose text is exactly `orca-companion`

### Requirement: Banner tagline is a single non-empty prose paragraph

The banner MUST include, immediately after the H1 title, exactly one non-empty Markdown paragraph that describes the project in prose. The paragraph MUST begin with the sentence `An e2e-loop demonstration project for the orca-companion agent harness.` and MAY include additional sentences afterwards.

#### Scenario: Tagline paragraph is present and non-empty
- **WHEN** a reader reads the paragraph directly under the H1 title in `README.md`
- **THEN** the paragraph is non-empty and its first sentence is the canonical tagline sentence

### Requirement: Banner includes an italic status banner line

The banner MUST include, after the tagline paragraph, exactly one line that announces the project's status. The status banner line MUST be rendered as italic Markdown (using `_..._` syntax) and MUST declare, in prose, that the project is an end-to-end loop demonstration under active development and that further sections will be added in later changes.

#### Scenario: Status banner is italic and announces forward-looking additions
- **WHEN** a reader reads the line that follows the tagline paragraph in `README.md`
- **THEN** that line is rendered in italic Markdown and states, in prose, that additional sections will be added in later changes

### Requirement: Banner is plain Markdown

The banner block MUST be encoded as plain CommonMark Markdown (UTF-8 text only). It MUST NOT contain HTML scripts, executable payloads, image embeds, badge URLs, or other non-text constructs.

#### Scenario: Banner contains no non-Markdown constructs
- **WHEN** a tooling step reads the banner bytes from `README.md`
- **THEN** the bytes decode as UTF-8 and contain no `<script>` tags, no executable payloads, no image embeds (`![...](...)`), and no link-only badge constructs that depend on external trackers
