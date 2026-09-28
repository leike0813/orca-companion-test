# Proposal

## Why

`README.md` is the first thing anyone opening this repository sees, and it
currently ends with an italic placeholder — "_More sections (Installation,
Usage, etc.) will be added in later changes._" — that tells the reader nothing
about the project's current state. A visitor who stops after the title and
one-line description learns neither that the project is spec-driven nor where
the work is tracked, and the placeholder invites them to assume content that
does not exist yet.

Replacing that placeholder with a short status banner closes the gap between
what the repository is and what its README promises: the banner states the
project's stage, what kind of project it is, and where to look next.

## What Changes

- Replace the `_More sections ... will be added in later changes._` placeholder
  line in `README.md` with a short, self-contained status banner.
- Require the banner to be visually distinct (a blockquote block directly after
  the title) so it reads as a status line rather than body prose.
- Require every claim and every path the banner names to be true and resolvable
  at the revision being written, so the banner cannot drift into fiction.

No existing capability changes, and nothing is removed or made incompatible.

## Capabilities

### New Capabilities

- `readme-banner`: Specifies the content, placement, and accuracy rules for the
  project status banner at the top of the repository's `README.md`.

### Modified Capabilities

None.

## Impact

- `README.md`: modified at the repository root; the placeholder line is replaced
  by a status banner. This is the only path this Work Package is permitted to
  touch.

No runtime code, public API, dependency, or build configuration is affected.
