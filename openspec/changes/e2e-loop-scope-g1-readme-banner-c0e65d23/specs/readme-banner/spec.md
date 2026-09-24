# Spec Delta

## Purpose

Establishes the top-of-README banner section that introduces the project by name and a one-line tagline, giving readers immediate framing before any other content appears in the file.

## ADDED Requirements

### Requirement: README Banner Section
The project README SHALL contain a banner section as its first content that names the project and states a one-line tagline.

#### Scenario: Banner is the first content
- **WHEN** a reader opens README.md
- **THEN** the first non-blank content is a banner section that includes the project name and a one-line tagline

### Requirement: Banner Uses Markdown Headings
The banner section SHALL use Markdown headings so the project name and tagline are visually prominent in rendered Markdown.

#### Scenario: Project name appears as H1
- **WHEN** the README is rendered as Markdown
- **THEN** the project name in the banner appears as a level-1 heading (`#`)

#### Scenario: Tagline is a separate paragraph
- **WHEN** the README is rendered as Markdown
- **THEN** the one-line tagline appears directly below the project name heading as a plain paragraph (no heading)
