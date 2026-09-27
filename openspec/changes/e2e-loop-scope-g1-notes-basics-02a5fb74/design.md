# Design

## Context

The orca-companion repository currently exposes project identity through `README.md` and runtime configuration through `orca-companion.json`, but has no dedicated Markdown file for narrative project notes. The `README.md` already anticipates future additions of Installation and Usage sections, while the `e2e-loop-scope` graph generation `g1` needs a stable anchor that future notes changes can extend without redesigning the layout. This change introduces that anchor as a fresh `NOTES.md` at the repository root.

Constraints from the Scope Envelope:
- Only `NOTES.md` may be added or modified by this change; every other file is out of scope.
- The change must be a valid OpenSpec change proposal, so it ships a delta spec for a new `notes-basics` capability alongside proposal, design, and tasks artifacts.

## Goals / Non-Goals

**Goals:**
- Provide a tracked `NOTES.md` at the repository root that captures introductory notes for the orca-companion e2e-loop demonstration project.
- Record the current `e2e-loop-scope` graph generation (`g1`) and identify the `notes-basics` work package as the source of the file.
- Reserve the `## Installation` and `## Usage` headings so later changes have stable anchor points.

**Non-Goals:**
- Populating the Installation or Usage sections with installation or usage instructions (those belong to later changes).
- Modifying `README.md`, `orca-companion.json`, `.gitignore`, or any other file outside the Scope Envelope.
- Introducing tooling, scripts, or automation for notes generation.

## Decisions

### Decision 1: Author `NOTES.md` as plain hand-written Markdown
Write `NOTES.md` by hand instead of generating it from a template or build step. The file is small, has no machine consumers in this generation, and hand-written Markdown is the simplest artifact that satisfies the spec.

**Rationale:** A generator would introduce build-time coupling and additional files outside the Scope Envelope.

### Decision 2: Use only `#` and `##` headings in `NOTES.md`
Restrict the heading hierarchy to one top-level title and second-level section headings, and skip no levels.

**Rationale:** The `notes-basics` spec requires heading continuity and bans `TBD`/`TODO` markers; a flat hierarchy makes that trivially auditable and leaves room for later changes to deepen sections without rewriting earlier structure.

### Decision 3: Place future-change anchors inline rather than as TODOs
Inside the reserved `## Installation` and `## Usage` sections, write a short prose sentence noting that a later change will populate the section.

**Rationale:** Inline prose preserves the "no TBD/TODO markers" requirement while still signalling that the section is intentionally reserved.

### Decision 4: Keep the change proposal as a single new capability with no modifications
Declare one new capability (`notes-basics`) under `## Capabilities` and leave `### Modified Capabilities` empty, since no existing capability's requirements are affected by this change.

**Rationale:** The change introduces behavior only for a new file and does not modify any existing spec; an empty Modified Capabilities list accurately reflects the scope.

## Risks / Trade-offs

- **Heading proliferation in later generations** — Future changes may need to introduce third-level (`###`) headings inside `## Installation` or `## Usage`. → Mitigation: The `notes-basics` spec only constrains the first generation's structure; later capability specs may deepen the hierarchy under those anchors.
- **Drift between `README.md` and `NOTES.md`** — Both files describe the project, and they could diverge over time. → Mitigation: `NOTES.md` deliberately focuses on current scope and forward-looking anchors, leaving the high-level project pitch to `README.md`.
