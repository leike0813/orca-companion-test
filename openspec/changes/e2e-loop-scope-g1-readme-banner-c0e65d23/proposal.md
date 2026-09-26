# Proposal: Promote README.md to a banner-style project front page

## Why

The repository's `README.md` currently contains only a project title, a one-line tagline, and a placeholder sentence stating that more sections will be added later. New visitors landing on the repository therefore see no immediate signal about what the project is, what status it is in, or where to look next. Because `README.md` is the canonical first impression of the orca-companion harness demonstration, the file needs a banner-style front page that conveys the project's purpose, scope, and status at a glance, before any of the deeper sections (Installation, Usage, etc.) are introduced by follow-up changes.

This change upgrades `README.md` from a placeholder into a proper banner page that documents the project's status, key entry points, and the explicit expectation that deeper sections will be added later. It is intentionally narrow: it touches `README.md` only and does not introduce any other tracked file, configuration change, or tooling.

## What Changes

- Rewrite `README.md` so it opens with a status banner that signals the project is an end-to-end demonstration of the orca-companion agent harness and is not yet a production-ready release.
- Add a "Quick Links" subsection under the banner that lists the canonical entry points so readers know where to look for related context.
- Add a "Project Status" subsection that states, in plain language, that this change is the first of a sequenced series and that deeper sections will follow in later changes.
- Keep the existing tagline sentence as the lead description so the project name and one-line description continue to appear immediately under the title.
- Remove the placeholder italic sentence ("_More sections (Installation, Usage, etc.) will be added in later changes._") only after the new "Project Status" subsection carries the same information explicitly, so no guidance is lost.
- No other files are created, modified, or removed. No tooling, CI, or configuration is added.
- No breaking changes for downstream consumers, because the file was a placeholder and the new content is additive.

## Capabilities

### New Capabilities

- `readme-banner`: Defines the structure and required content of the banner-style front page rendered in `README.md`, including the status banner, quick links, and project status subsections, so every visitor sees a consistent project overview before deeper sections are added.

### Modified Capabilities

None. This change introduces a brand-new capability; no existing spec requirements change.

## Impact

- Adds and modifies a tracked file: `README.md` at the repository root.
- No other tracked files in the work-package scope envelope are created, modified, or removed.
- No public APIs, dependencies, configuration files, build steps, or external systems are affected.
- This change is scoped exclusively to the `README.md` path declared in the work-package scope envelope.
