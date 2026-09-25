# Spec Delta

## Purpose
The `readme-banner` capability describes the banner block that sits at the top of `README.md` to signal that this repository is a demo harness for orca-companion, that it is driven through the orca-companion agent harness, and that the README is being built incrementally across multiple work packages.

## ADDED Requirements

### Requirement: README MUST open with a banner block under the H1 title
The file `README.md` MUST contain a banner block positioned immediately after its single H1 title (`# orca-companion`) and before any other prose. The banner MUST be rendered as a Markdown blockquote (`>` prefix) so it is visually distinct from the rest of the document.

#### Scenario: Reader opens README.md and scans the top
- **WHEN** a visitor opens `README.md`
- **THEN** the first lines after the H1 title form a blockquote banner
- **AND** no heading, paragraph, list, fenced code block, or HTML element precedes that banner

### Requirement: README banner MUST communicate project purpose, harness context, and incremental scope
The banner MUST convey three pieces of information in plain text: (a) the project is a demonstration / demo artifact and not the production orca-companion harness, (b) the orca-companion agent harness is what drives the project, and (c) additional README sections (Installation, Usage, etc.) will be added in later changes. Each of the three pieces MUST be present somewhere in the banner block.

#### Scenario: Visitor reads the banner block end to end
- **WHEN** the visitor reads the banner in full
- **THEN** they can identify the project as a demo
- **AND** they can identify the orca-companion agent harness as the driver
- **AND** they can identify that more sections are expected in subsequent changes

### Requirement: README banner MUST stay self-contained and visually consistent
The banner MUST NOT introduce external links, images, badges, fenced code blocks, inline HTML, or any other element that requires network access or rendering support beyond plain Markdown. The banner MUST be written as blockquote lines of plain prose. The banner MUST NOT duplicate or contradict the existing one-line project description paragraph that follows it.

#### Scenario: README.md is rendered offline or in a minimal Markdown viewer
- **WHEN** the file is rendered without network access or extended Markdown features
- **THEN** the banner appears in full and conveys all three required pieces of information
- **AND** no element of the banner requires fetching a remote resource

### Requirement: README banner MUST leave exactly one H1 and exactly one description paragraph
After the banner is added, `README.md` MUST contain exactly one H1 heading (`# orca-companion`), one banner blockquote, and one body paragraph beginning with the words `An e2e-loop demonstration project`. No additional H1, H2, list, image, or fenced code block may be introduced by the banner change.

#### Scenario: Inspector counts the structural elements of README.md
- **WHEN** a reviewer reads the file from top to bottom
- **THEN** they see exactly one `#` heading
- **AND** they see one blockquote banner directly under that heading
- **AND** they see one body paragraph starting with `An e2e-loop demonstration project` below the banner
