# Spec Delta

## Purpose

Defines the shape and required contents of the banner block that opens
`README.md`, so contributors can rely on a predictable hero area at the top of
the repository's landing page.

## ADDED Requirements

### Requirement: README.md opens with a blockquote-framed banner
The system SHALL ensure `README.md` begins with a Markdown blockquote banner
block whose first line is `# orca-companion` and whose content is followed by
a horizontal rule (`---`) that separates the banner from the rest of the
document.

#### Scenario: Banner is the first content in README.md
- **WHEN** a reader opens `README.md`
- **THEN** the first non-blank line of the file begins with a `>` blockquote
  marker and is followed by additional `>`-prefixed lines that together form
  the banner block

#### Scenario: Banner ends with a horizontal rule separator
- **WHEN** the reader scrolls past the banner
- **THEN** a `---` line terminates the banner before the introductory
  paragraph that follows it

### Requirement: Banner carries the project name as its level-1 heading
The system SHALL ensure the banner block contains a single level-1 heading
with the text `orca-companion` so the project's name remains the first heading
in the file.

#### Scenario: Project name appears as the banner's heading
- **WHEN** a renderer parses the banner
- **THEN** the banner contains a `# orca-companion` heading and no other
  level-1 heading appears in the file

### Requirement: Banner includes a one-sentence tagline and a fact strip
The system SHALL ensure the banner block contains, in order, a one-sentence
tagline describing the project's purpose, followed by a single-line fact
strip that lists the project's identifying marks (for example: `Spec-driven ·
E2E loop · Codex worker`).

#### Scenario: Tagline appears directly under the project heading
- **WHEN** a reader reads the banner from top to bottom
- **THEN** the first sentence under `# orca-companion` is a plain-language
  tagline that states the project's purpose in one sentence

#### Scenario: Fact strip follows the tagline on its own line
- **WHEN** a renderer parses the banner
- **THEN** a single line listing the project's identifying marks appears
  after the tagline and before the closing horizontal rule

### Requirement: Banner uses GitHub-flavored Markdown only
The system SHALL ensure the banner is composed exclusively of
GitHub-flavored Markdown primitives (blockquotes, headings, paragraphs,
horizontal rules, and inline text) and SHALL NOT introduce HTML elements,
embedded images, templating, or generated artifacts.

#### Scenario: Banner contains no HTML or image markup
- **WHEN** a reviewer greps the banner for HTML tags or image syntax
- **THEN** no `<...>` tags or `![]()` / `![](...)` image references appear
  inside the blockquote block
