# Design — `e2e-loop-scope-g1-notes-basics-02a5fb74`

## Context

See `proposal.md` — Why. The current state is a 2-commit repository
(`e951e88` baseline) with only `README.md`, an empty `.gitignore`,
and `orca-companion.json`. There is no developer-notes surface in
the repo.

The artifact introduced by this Work Package is a single,
top-level, hand-authored Markdown file (`NOTES.md`). The
deliverable is a static document; there is nothing to compile,
bundle, deploy, migrate, or wire to a runtime.

## Goals / Non-Goals

- **Goals**: produce a conformant `NOTES.md` that satisfies every
  `### Requirement` declared in `specs/notes-basics/spec.md`
  (`ADDED Requirements` block).
- **Non-Goals**: no tooling, no generation pipeline, no editor
  plugin, no CI check, no restructuring of existing tracked files.
  Future Work Packages may add those — they are explicitly outside
  this Scope Envelope (`["NOTES.md"]`).

## Decisions

- **Decision: hand-author `NOTES.md`; do not generate it.**
  - _Rationale_: the file is small (low hundreds of lines at
    most), changes infrequently, and has no machine-readable
    consumers at baseline. A generator would be a new dependency
    surface that is out of this Scope Envelope.
  - _Alternatives considered_:
    - Template from `openspec show notes-basics --type spec` —
      rejected, no such helper exists in OpenSpec today.
    - Generated from `orca-companion.json` and `git ls-tree` —
      rejected, adds a script and execution surface that exceed
      the Scope Envelope.
- **Decision: keep `NOTES.md` in plain CommonMark.**
  - _Rationale_: human readability and broad tooling support; no
    site generator is present at baseline, so there is no benefit
    to a Markdown dialect.
  - _Alternatives considered_: MDX, AsciiDoc — both rejected
    because there is no toolchain to render them in this repo.
- **Decision: do not commit a `design.md` template variant; mirror
  this same schema at archive time.**
  - The capability description in `specs/notes-basics/spec.md`
    (`## Purpose` plus `## ADDED Requirements`) is what gets
    promoted into `openspec/specs/notes-basics/spec.md` on
    archive. Nothing in this design is supposed to leak into the
    archived spec; we keep design.md inside the change bundle and
    do not propagate it.

## Risks / Trade-offs

- **Risk: the baseline SHA and `orca-companion.json` keys
  described in `NOTES.md` go stale as the project evolves.**
  → Mitigation: the `notes-basics` spec requires a new OpenSpec
  change whenever either surface moves (see `## ADDED Requirements`
  in `specs/notes-basics/spec.md`).
- **Risk: a future Work Package widens the Scope Envelope to
  add tooling around notes.**
  → Mitigation: that is the right answer for tooling — open a new
  change rather than mutating this one. The Scope Envelope is fixed
  for this Work Package (`["NOTES.md"]`).
- **Risk: humans forget to update `NOTES.md` when adding a new
  durable file at the repository root.**
  → Mitigation: a verifier task in `tasks.md` cross-checks
  `Repository Layout` against
  `git ls-tree -r HEAD --name-only | awk -F/ '{print $1}' | sort -u`,
  so a stale note is caught at apply time.

## Migration Plan

- _None._ This is the first notes surface in the repo. The only
  "migration" is the act of writing `NOTES.md` for the first time;
  there is no prior format to migrate from.

## Open Questions

None. Every durable surface this Work Package needs to reference
already exists at baseline (`README.md`, `.gitignore`,
`orca-companion.json`, the `e951e88` commit), so no design-level
ambiguity needs to be resolved before implementation.
