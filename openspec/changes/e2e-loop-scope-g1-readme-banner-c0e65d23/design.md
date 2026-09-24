# Design

## Context

The repository is an isolated baseline with no prior README. The work-package scope restricts in-scope changes to `README.md` only, so this design touches exactly one file. Markdown is the conventional README format and renders natively on every platform used to review the repository.

See `proposal.md` for motivation; this design covers only the implementation shape.

## Goals / Non-Goals

**Goals:**
- Introduce the project identity at the very top of `README.md`.
- Use only portable Markdown features that render on every standard renderer.

**Non-Goals:**
- Adding installation, usage, configuration, API, or contribution sections.
- Adding images, badges, or external assets (kept out of scope for a minimal banner).
- Introducing tooling or scripts to generate the README.

## Decisions

- Use a level-1 Markdown heading (`#`) for the project name to maximize visual prominence and avoid competing with later section headings.
- Use a single short tagline sentence directly below the heading to keep the banner compact and immediately readable.
- Place the banner as the first content of the file, with no blank lines preceding the heading, so the "first non-blank content" requirement holds reliably across renderers.

## Risks / Trade-offs

- A short banner may not capture every nuance of the project. → Mitigation: this change intentionally adds only the banner; richer sections can be added by subsequent changes.
- The chosen heading level affects later sections. → Mitigation: the banner uses a single H1, so subsequent sections naturally start at H2 and below.

## Migration Plan

None. This change only adds a documentation file.

## Open Questions

None.
