# Design

## Context

See proposal.md - Why for motivation. The constraint that shapes this design is the Work
Package Scope Envelope: only `README.md` may change, and acceptance evidence is a command
that covers `README.md`. There is no build, no test runner, and no documentation pipeline in
the repository, so verification has to work against the raw file with tools that already
exist on a developer machine.

## Goals / Non-Goals

**Goals:**

- Make the banner's shape checkable by a single shell command that exits non-zero on
  regression.
- Keep the edit small enough that a reviewer sees the whole change in one diff hunk.

**Non-Goals:**

- No generator, template, or lint tool for documentation. The banner is maintained by hand.
- No badges, images, or HTML; the banner must render as plain text everywhere.
- No restructuring of the page below the banner.

## Decisions

**Plain Markdown with a fixed label, not a badge.** The status line uses a literal
`**Status:**` prefix instead of a shields.io badge or an HTML block. Rationale: badges render
as empty boxes in plain-text terminals and in diff views, and they cannot be asserted with a
text match. Alternative considered: shields.io badge for visual polish — rejected because it
makes the status unobservable to the command-based acceptance check.

**Verify with `grep` in the acceptance command rather than adding a test.** `grep -q` over the
file covers the ordering, label, and uniqueness requirements with no new dependency. A unit
test would require introducing a test framework, which is outside the scope envelope.
Alternative considered: a markdown linter rule for heading structure — rejected as a new
dependency for a four-line block.

**One heading level above the title only.** The banner is a bolded line plus a short status
line and purpose line, not a new `#` heading, so the document keeps exactly one top-level
title. This keeps the existing title as the only H1 and avoids two competing headings at the
top of the page.

## Risks / Trade-offs

- [Banner drifts from reality as the project changes] → the status value comes from a small
  declared set, so a future edit is a conscious choice rather than free prose.
- [The grep-based check is weaker than a real test] → acceptable for a static document; the
  failure mode is a missed regression in wording, not in structure.

## Migration Plan

Single-commit, single-file edit. Rollback is reverting the commit; there is no state to
migrate and no consumer that depends on the banner's content.

