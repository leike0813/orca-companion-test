# Proposal

## Why

`README.md` currently opens with the project title, a single short
description, and a one-line placeholder note that "more sections will be
added in later changes." That placeholder is honest but does not give a
first-time reader any signal that the repository is a demonstration of
the orca-companion dispatch loop, nor any pointer to the canonical
developer-facing record in `NOTES.md`. A reader landing on `README.md`
from a clone has no obvious next step and may not realise that
`NOTES.md` already exists and holds the project's scope, intent, and
conventions. Introducing a banner at the top of `README.md` now — while
the surface is still small — gives every visitor an immediate,
machine-discoverable orientation block, mirrors the cross-link that
`NOTES.md` already carries back to `README.md`, and locks in a stable
top-of-file anchor that downstream tooling (linters, link auditors,
status badges) can rely on.

## What Changes

- Add a Markdown blockquote banner to `README.md`, placed as the first
  non-empty content of the file, above the existing `# orca-companion`
  title.
- The banner MUST name the project's demo nature and MUST contain a
  Markdown link whose target resolves to `NOTES.md` at the repository
  root, so a reader has a one-click path from the user-facing overview
  to the developer-facing record.
- The banner prose MUST NOT be a byte-for-byte copy of any prose block
  already present in `NOTES.md`; the two files stay complementary.
- No other file in the repository is added, removed, renamed, or
  modified by this change.

## Capabilities

### New Capabilities

- `readme-banner`: Defines the required presence, position, content,
  and cross-link conventions of the Markdown blockquote banner that
  opens `README.md`.

### Modified Capabilities

None.

## Impact

This change modifies exactly one existing path: `README.md` at the
repository root. Per the Work Package Scope Envelope, `README.md` is
the only file touched by this proposal; every additional piece of
context referenced by the banner lives inside the file content itself
and does not extend the surface of the change. No configuration files,
manifests, harness settings, or companion documents are introduced,
altered, or removed by this proposal.
