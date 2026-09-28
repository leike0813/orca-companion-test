# Spec Delta: readme-banner

## Purpose

The `readme-banner` capability locks in the introductory banner at the top of
`README.md`: a level-1 project title, a one-paragraph tagline that names the
project as an end-to-end demonstration of the orca-companion agent harness,
and an italic forward-pointer note that defers every further section to
later changes. The banner is the region of `README.md` that downstream work
packages append to rather than rewrite, so its shape and wording must stay
stable across the change graph.

## ADDED Requirements

### Requirement: README.md exists as a regular file at the repository root

A file named `README.md` SHALL exist at the repository root — the same
directory that holds `NOTES.md` and the `openspec/` tree — and SHALL be a
regular file (not a symbolic link to a directory or another special file).

#### Scenario: README.md is present after the change

- **WHEN** a reader lists the contents of the repository root after the
  change is applied
- **THEN** a file named `README.md` is present at the repository root
- **AND** it is a regular file, not a symbolic link or directory entry

### Requirement: README.md is encoded as UTF-8 Markdown text

`README.md` SHALL be encoded as UTF-8 (no BOM, no other encoding) and SHALL
use Markdown syntax with the `.md` extension so it renders in standard
Markdown viewers without extra tooling.

#### Scenario: File has clean UTF-8 Markdown content

- **WHEN** a reader opens `README.md` in a UTF-8 aware Markdown viewer
- **THEN** the file starts with no byte-order mark (no `\xef\xbb\xbf` prefix)
- **AND** every byte sequence in the file decodes as valid UTF-8 text
- **AND** the file's contents parse as Markdown without parser errors

### Requirement: README.md opens with the level-1 project title

`README.md` SHALL open with a level-1 Markdown heading whose literal text
is exactly the project name `orca-companion`, and that heading SHALL occupy
the very first non-empty line of the file.

#### Scenario: First non-empty line is the `orca-companion` heading

- **WHEN** a reader opens `README.md`
- **THEN** the first non-empty line of the file is `# orca-companion`
- **AND** no Markdown content precedes that line (other than an optional
  UTF-8 byte-order mark, which is forbidden by the encoding requirement)

### Requirement: README.md carries a tagline that names the orca-companion agent harness

`README.md` SHALL contain, immediately after the level-1 title and before
any other top-level section, a plain paragraph that names the project as
both an end-to-end demonstration project and the orca-companion agent
harness. The paragraph SHALL be rendered as ordinary Markdown text — not
as a heading and not as italic-only emphasis.

#### Scenario: Tagline paragraph names the project and the harness

- **WHEN** a reader scans the top of `README.md` after the title
- **THEN** a Markdown paragraph is present between the level-1 title and
  any other top-level section heading
- **AND** the paragraph contains the literal phrase
  `end-to-end demonstration project`
- **AND** the paragraph contains the literal phrase
  `orca-companion agent harness`
- **AND** the paragraph is rendered as a plain Markdown block (no leading
  `#`, no surrounding `*…*` emphasis only)

### Requirement: README.md defers further sections via an italic forward-pointer note

`README.md` SHALL contain, immediately after the tagline paragraph and
before any other top-level section, a Markdown emphasis span whose visible
text defers installation, usage, and other sections to later changes. The
emphasis SHALL use single-asterisk italic syntax (`*…*`) rather than
double-asterisk bold or underscore emphasis.

#### Scenario: Italic forward-pointer note is present and explicit

- **WHEN** a reader scans the top of `README.md` after the tagline
- **THEN** a Markdown emphasis span is present that mentions more
  sections being added in later changes
- **AND** the emphasis explicitly names at least one deferred section
  (for example `Installation` or `Usage`)
- **AND** the emphasis is delimited by single asterisks
  (`*…*`) rather than double asterisks (`**…**`) or underscores (`_…_`)

### Requirement: README.md banner precedes every other top-level section

The banner region — title, tagline, and italic forward-pointer note —
SHALL appear as the first three top-level constructs of `README.md` and
SHALL precede any later level-1 or level-2 heading such as `Installation`,
`Usage`, or any other section added by future changes.

#### Scenario: Banner is the topmost region of the file

- **WHEN** a reader reads `README.md` from the top
- **THEN** the level-1 title, the tagline paragraph, and the italic
  forward-pointer note appear in that order
- **AND** no other level-1 or level-2 heading appears above the
  forward-pointer note

### Requirement: README.md ends with exactly one trailing newline

`README.md` SHALL terminate with exactly one newline character (`\n`) as
its final byte. It SHALL NOT end with a bare EOF or with two or more
trailing newlines, so that standard text tooling treats the file as a
well-formed text document.

#### Scenario: File ends with a single newline

- **WHEN** a reader inspects the final byte of `README.md`
- **THEN** the file's last byte is the ASCII newline character `\n`
- **AND** the second-to-last byte is not another newline (so exactly one
  trailing newline is present)
