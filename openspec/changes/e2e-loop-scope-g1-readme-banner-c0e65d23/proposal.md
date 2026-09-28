# Proposal

## Why

The repository ships with a `README.md` stub whose only contents are a
project title, a one-sentence tagline, and an italic note that defers
every other section to "later changes." Subsequent work packages in this
graph generation will add installation, usage, and other documentation
to `README.md`, but they have no explicit contract for the banner region
they will append below. We need a foundational `readme-banner`
capability that locks in the structure and content of the README's
banner so the project always opens with a stable title, tagline, and
forward-pointer note that hands readers off to NOTES.md for the wider
project notes.

## What Changes

- Establish the `readme-banner` capability, which governs the
  introductory banner at the top of `README.md` (the content above any
  future sections such as Installation or Usage).
- The banner SHALL carry the project title `orca-companion` as a
  level-1 Markdown heading on the very first non-empty line of the
  file.
- The banner SHALL carry a one-paragraph tagline that names the project
  as both an end-to-end demonstration project and the orca-companion
  agent harness.
- The banner SHALL carry an italic forward-pointer note that defers
  installation, usage, and other sections to later changes.
- No source code, configuration, or other files are added, renamed, or
  removed by this change; the only file under specification is
  `README.md`.

## Design Intent

The banner is intentionally the smallest viable landing surface: one
heading, one paragraph, one italic note. Every later change in this
graph appends after the italic note, so the banner itself is the only
contract this change owns. Anything that would expand the banner
(adding badges, links, or sub-sections) belongs to a future change so
that diffs stay reviewable.

## Capabilities

### New Capabilities

- `readme-banner`: A `README.md` banner at the repository root that
  introduces the project with a level-1 title, a one-paragraph tagline
  naming the project as an end-to-end demonstration of the
  orca-companion agent harness, and an italic forward-pointer note
  deferring installation, usage, and other sections to later changes.

### Modified Capabilities

- `n/a`

## Impact

- File under specification: `README.md`
