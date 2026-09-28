# Design

## Context

The baseline repository contains only `README.md`, `orca-companion.json`, and `.gitignore` at the root. `README.md` is intentionally minimal and promises that additional sections (Installation, Usage, etc.) will be added by later changes. `orca-companion.json` is the harness configuration: it pins the planner/worker model, the integration branch, and the orchestration limits. There is no file that aggregates cross-cutting human-authored notes. This change introduces the first such file under a single fixed name so future changes and downstream tools can refer to it without ad-hoc naming.

## Goals / Non-Goals

**Goals:**
- Establish a single, well-known anchor file for project-level notes.
- Ship an initial, minimal structure that downstream changes can extend without renames or migrations.
- Keep `NOTES.md` a pure documentation surface so it never conflicts with the harness configuration.

**Non-Goals:**
- Filling `NOTES.md` with rich content (history, contributor lists, roadmap) beyond the three baseline sections.
- Modifying `README.md`, `orca-companion.json`, or any other baseline file.
- Introducing tooling, scripts, or CI checks that read or write `NOTES.md`.

## Decisions

- **File location: repository root.** `NOTES.md` lives alongside `README.md` so it is visible in a default clone listing and matches the convention used by widely-deployed documentation surfaces.
- **Filename: exactly `NOTES.md`.** A canonical uppercase `NOTES.md` avoids drift between this directory and downstream references; lowercase `notes.md` is explicitly rejected by the spec.
- **Capability path: `notes-basics`.** This mirrors the work-package slug `e2e-loop-scope#g1:notes-basics` and signals the minimal first version. Future richer note capabilities (`notes-status`, `notes-roadmap`, etc.) can extend without renaming this one.
- **Three fixed baseline sections in a fixed order.** `Project Status`, `Open Questions`, `Change Index` are ordered from "now" to "tracking". The fixed order lets downstream automation locate sections deterministically without parsing prose.
- **No execution semantics.** `NOTES.md` is plain Markdown. The spec requires that it contains no fenced shell/build/CI blocks that contradict `README.md` or `orca-companion.json`, so the file cannot accidentally act as a shadow config.

## Risks / Trade-offs

- **Section names may feel redundant with `README.md` sections added later.** Future changes may add an Installation or Usage section to `README.md` that overlaps semantically with `Project Status`. The "documentation-only" requirement mitigates this by forbidding behavioral conflicts; semantic overlap is acceptable as long as declarations stay consistent.
- **Fixed heading order may constrain future authors.** Authors who want a different order would have to amend this spec. The trade-off favors deterministic section discovery over free-form authoring, which matches the documentation-only nature of the file.
- **Filename capitalization could surprise tools on case-insensitive filesystems.** On macOS or Windows default clones, `NOTES.md` and `notes.md` would collide. The spec deliberately requires the uppercase form so a single canonical name is enforced regardless of platform.
