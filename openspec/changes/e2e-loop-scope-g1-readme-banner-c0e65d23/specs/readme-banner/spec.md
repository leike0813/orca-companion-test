# Spec Delta

## Purpose

Establishes the introductory surface of `README.md` as a stable, pinned banner
that downstream changes, automation, and consumers can rely on as a fixed
anchor. The banner sits directly under the project's H1 and is the first
content a reader encounters; it is the only content in `README.md` whose
wording, position, and formatting are pinned by this spec. Downstream changes
extend `README.md` strictly by appending new sections after the banner, never
by renaming, relocating, or removing it.

## ADDED Requirements

### Requirement: README.md begins with the canonical H1

The first non-blank line of `README.md` MUST be exactly `# orca-companion`,
with no leading whitespace, no trailing spaces, and no preceding blank lines.
That H1 MUST be the only level-1 Markdown heading in the file.

#### Scenario: First non-blank line is the canonical H1

- **WHEN** a reader inspects the first non-blank line of `README.md`
- **THEN** it is exactly `# orca-companion`

#### Scenario: Exactly one level-1 heading exists

- **WHEN** a reader counts the Markdown lines beginning with a single `#`
  followed by a space
- **THEN** the count in `README.md` is exactly one

### Requirement: A pinned banner blockquote follows the H1

A single Markdown blockquote banner MUST appear in `README.md` directly under
the H1. The banner line MUST begin with the following pinned leading sentence and
MUST NOT contain any further content on the same line:

    > **Note:** this repository is an end-to-end loop demonstration project for the orca-companion agent harness.

The banner line MUST be positioned exactly on line `3` of `README.md`: line `1`
is the H1, line `2` is a single blank Markdown separator, and line `3` is the
banner blockquote. No paragraph, list item, fenced code block, image, table,
or heading (of any level) MAY appear on line `2` or between the H1 and the
banner. The banner MUST be a single line; multi-line or stacked blockquotes
MUST NOT be used as the banner. Line endings MUST be a single `\n` (LF) so
that downstream consumers can compute byte-exact positions.

#### Scenario: Banner line is present with the pinned leading sentence

- **WHEN** a reader greps `README.md` for the literal leading sentence of the
  banner
- **THEN** exactly one matched line is reported and the matched line begins
  with `> **Note:** this repository is an end-to-end loop demonstration
  project for the orca-companion agent harness.`

#### Scenario: Banner is positioned on line 3 exactly

- **WHEN** a reader enumerates lines of `README.md` starting at line 1
- **THEN** line 1 is `# orca-companion`, line 2 is empty, and line 3 begins
  with the pinned banner leading sentence

#### Scenario: No interposing content sits between the H1 and the banner

- **WHEN** a reader scans lines 2 of `README.md`
- **THEN** line 2 is empty and the banner blockquote is the first
  non-blank line after the H1

#### Scenario: Banner is exactly one line

- **WHEN** a reader counts consecutive `>`-prefixed Markdown lines that form
  the banner
- **THEN** the banner consists of exactly one line

### Requirement: README banner is the only contractually pinned content

The banner blockquote is the only content in `README.md` whose wording,
position, and formatting are pinned by this spec. Any prose that appears
after the banner is documentation-only and MUST NOT be relied upon by
automation; downstream changes MAY modify, replace, or remove such prose
without amending this capability, provided the H1 and the banner blockquote
remain byte-identical to their pinned forms on lines 1 and 3 of the file.

#### Scenario: Post-banner prose is documentation-only

- **WHEN** a reader reads content that appears after the banner blockquote
- **THEN** that content is treated as plain documentation and is not pinned
  by the `readme-banner` capability

#### Scenario: Downstream changes preserve the H1 and banner verbatim

- **WHEN** a downstream change edits `README.md` to add a new section or to
  revise non-pinned content
- **THEN** the `# orca-companion` H1 line and the banner blockquote line
  remain byte-identical to their pinned forms

### Requirement: Banner is a documentation-only surface

The banner blockquote MUST be plain Markdown prose. It MUST NOT contain any
fenced code block, inline HTML, version pin, semantic-version string,
machine-readable identifier, or assertion about behavior, configuration, or
commands that is not already declared as a declaration elsewhere in the
repository. The banner MUST remain a single line of plain Markdown text so
that automation can safely treat it as a documentation blurb rather than as
executable or machine-actionable content.

#### Scenario: Banner contains no fenced code or inline HTML

- **WHEN** a reader scans the banner line for fenced code fences or
  angle-bracketed HTML tags
- **THEN** neither a triple-backtick fence nor `<` HTML markers appear on
  that line

#### Scenario: Banner asserts no version pin or behavior contract

- **WHEN** a reader inspects the banner line for version strings, machine
  identifiers, or imperative commands
- **THEN** the banner is plain prose and declares no version, identifier, or
  runtime behavior

#### Scenario: Banner line is exactly the pinned leading sentence

- **WHEN** a reader compares the banner line against the pinned leading
  sentence
- **THEN** the banner line is the pinned leading sentence with no trailing
  or preceding extra characters on the same line
