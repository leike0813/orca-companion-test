# Design

## Context

`README.md` is the repository's front page and currently reads:

    # orca-companion

    An e2e-loop demonstration project for the orca-companion agent harness.

    _More sections (Installation, Usage, etc.) will be added in later changes._

It has no runtime consumer — nothing in the build, CI, or the harness reads
it — so the design questions are about tone, placement, and how a reviewer can
check the result, not architecture.

Constraints carried from the work package scope envelope:

- `README.md` is the only file this change may modify.
- The banner must be true at the revision it is written against.

## Goals / Non-Goals

**Goals**

- Replace the deferral placeholder with a status banner that states the
  project's stage and what kind of project it is.
- Make each requirement checkable with a shell command a reviewer can run
  directly, since the acceptance evidence for this work package is a command.

**Non-Goals**

- Writing the Installation, Usage, or Contributing sections the placeholder
  alludes to.
- Reworking `NOTES.md`, which already holds the layout and verification detail
  that the banner points at.
- Introducing a status badge, generated header, or any build-time templating.

## Decisions

### Decision: render the banner as a blockquote block under the title

The banner is a run of `>`-prefixed lines placed immediately after the `#`
title. Blockquote is used because Markdown has no other inline convention that
visually separates a status line from prose, and it keeps the document to a
single heading level.

**Rationale**: placement under the title is what makes it a banner rather than
a paragraph that a reader can scroll past; blockquote rendering makes it
obvious in both a rendered view and a raw read of the file.

### Decision: state stage and project kind, and point at what already exists

The banner says the project is under active, spec-driven development, says it
is a demonstration project for the agent harness rather than a shipped library
or service, and points at `openspec/` for tracked work and `NOTES.md` for
layout and verification. It deliberately does not restate those documents.

**Rationale**: the placeholder's real failure was that it said nothing about
current state. Two factual sentences plus a pointer fix that; restating the
layout would duplicate `NOTES.md` and create a second thing to keep in sync.

### Decision: verify with plain `grep` / `awk` / `test` over the committed file

Verification is a set of shell checks: the placeholder text is gone, the
title count is still one, the first non-blank content after the title is a
blockquote block with a non-empty body, no headings other than the title exist,
and every path the banner names resolves.

**Rationale**: the repository has no test runner, and the acceptance evidence
for this work package is a command. Standard POSIX tools keep the check
reproducible for any reviewer without extra dependencies.

## Risks / Trade-offs

- *Drift*: the banner can go stale as the repository changes. Accepted for this
  change; the accuracy requirement binds each revision, and future changes are
  the natural place to relax it if staleness becomes a recurring problem.
- *Blockquote is a styling choice, not a semantic one*: a reader viewing raw
  Markdown sees `>` prefixes. Accepted — the banner stays legible either way,
  and the alternative (an H2) would add a heading the requirements forbid.

## Migration Plan

None. The change replaces one line of prose in an existing document; nothing is
renamed, removed, or reconfigured, and no consumer reads the file.

## Open Questions

None. No open question changes what gets built.
