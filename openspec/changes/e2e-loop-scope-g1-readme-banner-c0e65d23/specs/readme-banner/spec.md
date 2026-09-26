## Purpose

The `readme-banner` capability defines the Markdown banner that appears at
the top of `README.md` and identifies the `orca-companion` project as an
Orca e2e-loop demonstration target. It locks in where the banner lives
(immediately after the H1 title), what it must say, and how it must be
formatted, so future changes can extend or replace the banner without
re-litigating the contract.

## ADDED Requirements

### Requirement: `README.md` has a banner directly under the title
`README.md` MUST begin with a single H1 title (`# orca-companion`) followed
immediately by a banner block, followed by the rest of the document body.
There SHALL be no content between the H1 title and the banner, and the
banner SHALL appear exactly once in the file. The H1 title, the banner,
and the remainder of the document SHALL be separated from each other by
exactly one blank line.

#### Scenario: Banner is the first body element after the H1 title
- **WHEN** a reader parses `README.md` line by line
- **THEN** line 1 SHALL be the H1 title `# orca-companion`
- **AND** line 2 SHALL be blank
- **AND** the banner SHALL begin on line 3
- **AND** no other content SHALL appear between the H1 title and the
  banner

#### Scenario: Banner appears more than once
- **WHEN** `README.md` contains the banner wording defined in this
  capability in two or more places
- **THEN** the file SHALL be considered out of conformance
- **AND** the remediation message SHALL name both locations

### Requirement: Banner identifies the Orca e2e-loop demonstration role
The banner SHALL name both the project (`orca-companion`) and its role
as an Orca e2e-loop demonstration target. At minimum, the banner body
MUST contain the substring `orca-companion` and the substring
`Orca e2e-loop` (case-insensitive). The banner MAY add additional
wording beyond that minimum; it SHALL NOT contradict it.

#### Scenario: Banner contains the required identifiers
- **WHEN** a reader greps `README.md` for the substrings `orca-companion`
  and `Orca e2e-loop`
- **THEN** both substrings SHALL be present inside the banner block
- **AND** at least one match for each substring SHALL be inside the
  banner's lines (not in later document body)

#### Scenario: Banner contradicts its role
- **WHEN** the banner's wording claims the project is something other
  than an Orca e2e-loop demonstration target (for example, by
  describing it as a production library, a CLI tool, or a different
  agent harness)
- **THEN** the file SHALL be considered out of conformance
- **AND** the contradicting wording SHALL be quoted in the remediation
  message

### Requirement: Banner uses a Markdown blockquote with an emoji prefix
The banner SHALL be formatted as a GitHub-flavored Markdown blockquote:
its lines MUST start with `>` followed by a space. The first
non-whitespace character of the banner body MUST be a single emoji
character (any Unicode emoji codepoint). The banner MAY span multiple
blockquote lines and MUST be terminated by the first non-blockquote
line in the document.

#### Scenario: Banner is a Markdown blockquote
- **WHEN** a reader inspects the banner lines
- **THEN** every banner line SHALL begin with `>` followed by a single
  space character
- **AND** the banner SHALL contain at least one such `> `-prefixed
  line

#### Scenario: Banner begins with an emoji
- **WHEN** a reader reads the first non-whitespace character of the
  banner body
- **THEN** that character SHALL be a single Unicode emoji codepoint
- **AND** it SHALL be followed by a space before the rest of the
  banner wording begins

#### Scenario: Banner uses an unsupported format
- **WHEN** the banner is rendered as plain prose, an HTML `<div>`,
  an image, or any construct other than a `> `-prefixed Markdown
  blockquote
- **THEN** the file SHALL be considered out of conformance
- **AND** the offending construct SHALL be cited in the remediation
  message

### Requirement: Banner does not displace the rest of `README.md`
The banner SHALL be additive: every line of `README.md` that exists at
the baseline commit `e951e8877b1ed12eebf4eb992ea91623b986b05c` outside
of the banner MUST remain in `README.md` after the banner is added,
in its original order. In particular, the one-sentence description
(`An e2e-loop demonstration project for the orca-companion agent
harness.`) and the italic deferral note (`_More sections
(Installation, Usage, etc.) will be added in later changes._`) MUST
both still be present, in that order, after the banner.

#### Scenario: Baseline description and deferral note are preserved
- **WHEN** a reader compares the body of `README.md` after this change
  to the body of `README.md` at baseline commit `e951e88`
- **THEN** the baseline description line SHALL still be present
- **AND** the baseline italic deferral note SHALL still be present
- **AND** the baseline deferral note SHALL still appear after the
  baseline description

#### Scenario: Baseline content is removed or reordered
- **WHEN** a baseline line is missing from `README.md` after the change
  is applied, or the baseline lines appear in a different order than
  they did at `e951e88`
- **THEN** the file SHALL be considered out of conformance
- **AND** the missing or reordered line SHALL be cited in the
  remediation message

### Requirement: Banner change is reflected in the spec on update
Whenever the banner's wording, placement, emoji, or supporting Markdown
construct is introduced, altered, or removed, the change MUST be
expressed through OpenSpec: the `readme-banner` spec SHALL be updated
via an `ADDED` or `MODIFIED Requirements` block in a change under
`openspec/changes/` before the on-disk `README.md` is admitted.

#### Scenario: README changes without a spec update
- **WHEN** a future Work Package modifies the banner in `README.md`
  but the `readme-banner` capability is not updated through OpenSpec
- **THEN** the future Work Package SHALL be considered out of
  conformance
- **AND** the missing capability update SHALL be cited in the
  remediation message

#### Scenario: Capability update precedes README change
- **WHEN** a future Work Package that touches the banner opens an
  OpenSpec change whose `MODIFIED Requirements` block updates
  `readme-banner` before any on-disk `README.md` change is admitted
- **THEN** the Work Package SHALL be considered conformant with this
  requirement

