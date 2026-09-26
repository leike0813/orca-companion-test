# Engineering Notes

This file tracks release notes, design decisions, and follow-ups for the
`orca-companion` project. Entries are dated in ISO-8601 (`YYYY-MM-DD`) form and
appended to the appropriate section.

## Release Notes

- 2026-09-27 Introduce `NOTES.md` as the canonical engineering notes surface alongside `README.md`.

## Design Decisions

### 2026-09-27 Adopt a fixed three-section layout for `NOTES.md`
`NOTES.md` uses three required top-level sections — `## Release Notes`,
`## Design Decisions`, and `## Follow-ups` — in that fixed order. Release notes
and follow-ups are short and read well as bullets, while design decisions often
need a paragraph of rationale and are therefore rendered as third-level
headings. Every entry begins with an ISO-8601 date so chronology is preserved
without relying on git history.

## Follow-ups

- 2026-09-27 Extend `README.md` with Installation and Usage sections that defer here in future changes.
