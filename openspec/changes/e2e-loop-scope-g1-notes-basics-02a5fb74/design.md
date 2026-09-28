# Design

## Context

`NOTES.md` is a new, human-readable document at the repository root. It has no
runtime consumer: nothing in the build, CI, or the harness reads it. The only
consumers are people, which means the design questions are about authoring
rules and verification rather than architecture.

Constraints carried from the work package scope envelope:

- `NOTES.md` is the only file this change may create or modify.
- The document must stay accurate for the revision it is written against.

## Goals / Non-Goals

**Goals**

- Produce a `NOTES.md` that satisfies every requirement in
  `specs/notes-basics/spec.md`.
- Make each requirement checkable by a command a reviewer can run directly.

**Non-Goals**

- Redesigning or expanding `README.md`.
- Automating NOTES.md generation, linting, or publishing it anywhere.
- Documenting harness internals that are not present in this repository.

## Decisions

### Decision: author NOTES.md by hand, against the current tree

Every fact in `NOTES.md` is written from the repository state at the change's
baseline commit rather than copied from another checkout or templated.

**Rationale**: the "claims match reality" requirement is only meaningful if the
author resolved each path against the tree being documented. Generation would
add machinery for a document nobody consumes.

### Decision: keep the section set small and fixed

The document uses a single H1, a short purpose paragraph, and a small set of H2
sections covering repository layout and verification.

**Rationale**: the requirement demands a purpose statement and at least one
layout-or-verification section. A fixed, minimal set satisfies it without
creating a second README that competes with the existing one.

### Decision: verify with plain `test` / `grep` over the committed file

Verification is a set of shell checks: the file exists and is non-empty, the
H1 is present, the required sections carry non-empty bodies, and every path
named in the document resolves to a real file or directory.

**Rationale**: the acceptance evidence for this work package is a command, and
the repository has no test runner. Standard POSIX tools are available and keep
the check reproducible for any reviewer without extra dependencies.

## Risks / Trade-offs

- *Drift*: NOTES.md can go stale as the repository changes. Accepted for this
  change; the accuracy requirement binds each revision, and future changes are
  the natural place to add a maintenance note if staleness becomes a problem.
- *Overlap with README.md*: duplicating content invites contradictions. Mitigated
  by keeping NOTES.md focused on basics and cross-referencing rather than
  restating the README.

## Migration Plan

None. The change only adds a new file; nothing existing is renamed, removed, or
reconfigured.

## Open Questions

None. No open question changes what gets built.
