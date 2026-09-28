# Design

## Context

`NOTES.md` is a documentation-only artifact. It has no runtime consumers, no build integration, and no automated readers, so the design goal is a durable text convention rather than a format or tool decision.

## Goals / Non-Goals

Goals:

- Fix the section layout so notes remain easy to scan as entries accumulate.
- Require a date per entry so freshness and ordering are visible without a tool.
- Keep every entry short enough to be read inline during code review.

Non-Goals:

- No schema, front-matter, or machine-readable metadata; `NOTES.md` stays plain Markdown.
- No tooling, linting, or CI check that enforces the structure.
- No migration of content out of `README.md`; the README is left untouched.

## Decisions

### Plain Markdown with fixed level-two sections

The file uses a fixed skeleton (`# Notes`, then `## Overview`, `## Decisions`, `## Open Questions`). A closed set of sections is chosen over a free-form outline because it lets a reader jump to a known place, and because the spec can state requirements that are objectively checkable by reading the text.

### Dates live in level-three entry headings

Each decision and open question is a `### YYYY-MM-DD — <title>` heading followed by a paragraph. Putting the date in the heading rather than a bullet prefix keeps entries at a uniform depth, makes new entries appendable at the end of a section, and avoids introducing a nested structure that would drift across notes.

An em dash with surrounding spaces is used as the separator because it renders unambiguously next to an ISO date, unlike a bare hyphen or a colon.

### Entries are capped at three sentences

A short cap keeps notes useful as pointers to a decision rather than as a second home for its rationale, which discourages content that will drift from the actual change it describes. The cap is stated in the spec as a scenario so it can be applied during review without tooling.

## Risks / Trade-offs

- The structure is unenforced, so a future edit could add or drop a section silently. Mitigation: the requirements describe the sections explicitly, so a reviewer can check the file by reading it.
- Capping entries at three sentences may push longer reasoning into the change proposal or an issue tracker. That is the intended destination; the cap is a routing rule, not a claim that reasoning is unimportant.

## Migration Plan

None. `NOTES.md` is introduced empty apart from the required skeleton; no existing content is moved.

## Open Questions

- Should the `## Overview` section eventually link to a per-topic index once the number of entries makes a single list unwieldy? Deferred; the current entry volume does not justify it.

