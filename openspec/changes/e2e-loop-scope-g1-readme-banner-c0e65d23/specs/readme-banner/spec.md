# Spec Delta

## Purpose

Documents the Markdown blockquote banner that opens `README.md` so the
repository has a stable, machine-discoverable orientation block at the
top of its user-facing overview, with a guaranteed cross-link to the
developer-facing record in `NOTES.md`.

## ADDED Requirements

### Requirement: README.md banner blockquote presence

`README.md` MUST contain at least one Markdown blockquote line whose
first non-whitespace character is `>`. The blockquote MUST be placed
above the existing `# orca-companion` title, and the `# orca-companion`
title MUST remain the first level-1 heading of the file.

#### Scenario: Banner is the first non-empty content of README.md
- **WHEN** a reader opens `README.md` directly with `cat`, a Markdown
  viewer, or any common Markdown parser
- **THEN** the first non-empty line(s) of the file form a Markdown
  blockquote (lines whose first non-whitespace character is `>`), and
  the `# orca-companion` level-1 heading appears after that blockquote.

#### Scenario: Blockquote parses as a single Markdown quote element
- **WHEN** a Markdown parser such as `grip` or a code-hosting platform
  renders `README.md`
- **THEN** the lines beginning with `>` render as a single contiguous
  blockquote element rather than as separate paragraphs.

### Requirement: README.md banner content

The banner blockquote MUST contain non-empty prose that (a) names the
demo nature of the orca-companion project and (b) directs the reader
toward `NOTES.md` for the developer-facing scope, intent, and
conventions. Each of those two signals MUST appear at least once inside
the blockquote.

#### Scenario: Banner names the demo nature of the project
- **WHEN** a reader reads only the banner blockquote of `README.md`
- **THEN** the prose makes clear, in declarative form, that the project
  exists to demonstrate the orca-companion dispatch loop rather than
  to ship a production-ready tool.

#### Scenario: Banner points the reader to NOTES.md
- **WHEN** a reader reads only the banner blockquote of `README.md`
- **THEN** the prose explicitly directs the reader to `NOTES.md` for
  additional developer-facing context such as scope, intent, or
  conventions.

### Requirement: README.md banner cross-link to NOTES.md

The banner blockquote MUST contain a Markdown link whose link label is
non-empty and whose link target is the relative string `NOTES.md`. The
link MUST be present inside the blockquote itself, not after it.

#### Scenario: Reader can jump from the banner to NOTES.md
- **WHEN** a reader renders `README.md` in a Markdown viewer such as a
  code-hosting platform or `grip`
- **THEN** the rendered banner contains a clickable link whose target
  resolves to `NOTES.md` at the repository root, so the user can move
  from the user-facing overview to the developer-facing record without
  guessing the path.

#### Scenario: Banner link target is the literal relative path
- **WHEN** the banner blockquote of `README.md` is searched for the
  Markdown link syntax `](NOTES.md)`
- **THEN** at least one match is found and the match is contained on a
  line whose first non-whitespace character is `>`.

### Requirement: README.md banner does not duplicate NOTES.md

The prose inside the banner blockquote MUST NOT be a byte-for-byte copy
of any prose block already present in `NOTES.md`. The banner
complements `NOTES.md` rather than mirroring it.

#### Scenario: Banner prose differs from NOTES.md prose
- **WHEN** the prose inside the banner blockquote of `README.md` is
  compared against the prose blocks of `NOTES.md`
- **THEN** no block of prose inside the banner is an exact
  byte-for-byte copy of any block of prose inside `NOTES.md`; the two
  files remain complementary documents.
