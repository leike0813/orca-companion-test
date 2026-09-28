# Design: NOTES Basics

## Context

The repository is a fixture worktree whose only meaningful user-facing
artefacts today are a single-line `README.md`, an empty `.gitignore`,
and an `orca-companion.json`. There is no source code, no test suite,
and no documentation directory. This change introduces a single Markdown
file — `NOTES.md` — so that anyone opening the project can find a small,
well-formed page of basic notes without us inventing extra artefacts.

The change has no architectural, dependency, or runtime surface. The
design choices below are therefore limited to the wording, layout, and
topic coverage of `NOTES.md` itself. See `proposal.md` for the
motivation behind introducing the file.

## Goals / Non-Goals

**Goals:**

- Add a `NOTES.md` at the repository root that satisfies every
  requirement in `specs/notes-basics/spec.md`.
- Keep the file short and scannable: one H1, one or more H2 sections,
  and plain prose beneath each heading.
- Cover only basic, durable facts about the project that the implementer
  can state factually from the existing worktree contents.

**Non-Goals:**

- Adding installation, build, or run instructions (there is no runtime
  to document, and `README.md` already carries the project title).
- Adding badges, links to external sites, or any auto-generated
  content.
- Creating any file outside `NOTES.md`.
- Modifying `README.md`, `.gitignore`, `.git`, or `orca-companion.json`.
- Tracking history or versioning inside `NOTES.md`; that belongs in a
  future changelog-style change if one is ever introduced.

## Decisions

- **Layout: H1 + one or more H2 sections of plain prose.** Rationale:
  the spec requires exactly one H1 (`Notes`) and at least one H2;
  keeping the layout flat avoids inventing extra structure that the
  spec does not require. Alternatives considered: a table-of-contents
  H2 followed by deeper H3 sections. Rejected because the spec
  mandates no H3 content and the file should stay minimal.
- **Section topics: project stage and repo layout.** Rationale: those
  are the only basic facts the implementer can state factually from the
  existing worktree (it is a fixture worktree whose tracked files are
  `README.md`, `.gitignore`, `orca-companion.json`, and the OpenSpec
  change tree). Alternatives considered: longer topic lists (tooling,
  dependencies, glossary). Rejected because the worktree contains no
  additional facts to ground those topics in.
- **No placeholder markers.** Rationale: the spec requires their
  absence, and copy decisions therefore must avoid leaving
  `TODO`/`TBD`/`<placeholder>`/`lorem ipsum` strings in the file even
  briefly during drafting.

## Risks / Trade-offs

- Wording risk → the topic sections could overstate the project's
  maturity (e.g., promising a quickstart that does not exist).
  Mitigation: keep the body sentences factual about the fixture
  worktree rather than promising future functionality.
- Creep risk → future contributors could grow `NOTES.md` beyond the
  basics scope. Mitigation: the spec caps topics at plain-English H2
  headings with body sentences; any addition of new structural
  artefacts (tables, glossaries, changelog entries) requires its own
  OpenSpec change.

## Migration Plan

None. `NOTES.md` is added as a new file; no existing artefact
references its absence or its content.

## Open Questions

None.
