# Design

## Context

The repository ships only `README.md` today, which explicitly defers the next sections ("Installation, Usage, etc.") to future changes. There is no existing engineering-notes surface (release notes, design decisions, follow-ups), so every future change would otherwise have to invent its own shape. This change introduces `NOTES.md` as the single canonical place for those notes and locks in a minimal contract (location, required sections, entry shape) so downstream changes can extend it.

The proposal establishes the why and what; this design captures only the design-level decisions that shape the artifact: which sections are required, in which order, and how entries are formatted.

## Goals / Non-Goals

**Goals:**
- Define a stable, observable layout for `NOTES.md` so downstream changes do not have to re-negotiate structure.
- Keep the contract small enough that it can be implemented by committing a single text file in this change.
- Seed the file with at least one entry per required section so the file is never shipped empty.

**Non-Goals:**
- Adding tooling, linting, or generators around `NOTES.md`. This change introduces the file only; automation is a future concern.
- Migrating or restructuring any existing documentation. There is no pre-existing `NOTES.md` and no other notes surface to consolidate.
- Defining the full taxonomy of release notes or follow-ups. The contract specifies the shape of an entry, not its content.

## Decisions

- **Three required sections, fixed order.** `## Release Notes`, `## Design Decisions`, `## Follow-ups`, in that order. Rationale: matches the common engineering-notes pattern (what shipped / why we chose it / what's next) and gives downstream changes predictable anchor points. Alternatives considered: a single free-form notes section — rejected because it forces every consumer to re-discover the structure.
- **Dated entries.** Every entry starts with an ISO-8601 date (`YYYY-MM-DD`) so chronology is preserved without relying on git blame or commit timestamps. Alternatives considered: relying on commit timestamps — rejected because `NOTES.md` may be reorganized after the fact.
- **Bulleted entries for Release Notes and Follow-ups; third-level headings for Design Decisions.** Rationale: release notes and follow-ups are short and benefit from a flat bullet list; design decisions often need a paragraph of rationale and read better as `### ` headings with body text. Alternatives considered: uniform bullets for all three — rejected because it would either crowd design-decision rationale into a single line or force every section into headings.
- **Single canonical file at the repository root.** Rationale: keeps `NOTES.md` discoverable alongside `README.md` and avoids inventing a new documentation directory for a single file. Alternatives considered: a `docs/notes.md` location — rejected because the repository has no `docs/` directory yet and adding one is out of scope for "notes-basics".
- **No tooling in this change.** Rationale: a single hand-authored text file is sufficient to satisfy the spec; introducing a generator now would expand scope without changing observable behavior.

## Risks / Trade-offs

- [Risk] Future changes may want different entry shapes (e.g. semantic-versioning tags on Release Notes) — [Mitigation] the spec locks only the date prefix and the heading/bullet form, so future deltas can extend without invalidating prior entries.
- [Risk] Manual edits could drift away from the spec — [Mitigation] the verification task invokes `openspec validate`, which reports structural findings; deeper linting is explicitly out of scope and can be addressed in a later change.
- [Trade-off] The fixed section ordering forecloses alternative layouts (e.g. swapping Design Decisions before Release Notes) — accepted because predictability for downstream consumers outweighs flexibility here.
