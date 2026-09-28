# Proposal: Notes basics

## Why

The `orca-companion` repository currently has no structured notes surface.
As the e2e-loop demonstration grows across multiple work packages,
contributors and downstream agents need a single, stable place to find
cross-cutting context that does not fit the short README and that cannot
live inside any single module. Without that surface, notes end up
scattered across specs, READMEs, and ephemeral chat threads, which makes
handoffs harder to verify and contradicts the e2e-loop goal of giving
each graph node a discoverable baseline.

This change introduces that surface as a minimal, scope-bounded first
version (`notes-basics`). Future graph nodes (e.g., contributor guides,
release notes, change-log summaries) will layer on top of this baseline
in their own changes rather than extending it implicitly.

## What Changes

- Add a new top-level `NOTES.md` file at the repository root.
- `NOTES.md` MUST contain a fixed set of level-2 sections, in order:
  `Overview`, `Conventions`, and `Pointers`.
- `NOTES.md` MUST be valid GitHub-flavored Markdown, UTF-8 encoded, and
  fully self-contained (no required images, scripts, or external links).
- No file outside the Scope Envelope of this Work Package is created
  or modified by this change.

## Capabilities

### New Capabilities
- `notes-basics`: Defines the minimum structure and content of the
  repository-root `NOTES.md` so the e2e-loop demo always ships a
  discoverable, stable baseline notes document.

### Modified Capabilities
- _None._ This change introduces the first notes-related capability
  in the project and does not modify any existing capability.

## Impact

- `NOTES.md` (new file at the repository root; the only file created
  by this change and the only path declared in this Work Package's
  Scope Envelope).
