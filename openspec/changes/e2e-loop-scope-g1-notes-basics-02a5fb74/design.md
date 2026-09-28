# Design

## Context

The repository has three tracked files and no `openspec/` root yet. This change introduces both the `NOTES.md` document and the OpenSpec root that hosts the planning loop the document will describe. See proposal.md for the motivation.

## Goals / Non-Goals

**Goals:**

- Produce a `NOTES.md` whose sections map one-to-one onto the requirements in `specs/notes-basics/spec.md`, so a reader can navigate by heading.
- Keep every command listed in `NOTES.md` runnable as written from the repository root.

**Non-Goals:**

- Reworking, merging into, or deleting `README.md`. The README keeps its current one-line role; `NOTES.md` points at it rather than absorbing it.
- Building tooling that checks or generates `NOTES.md`. The verification for this change is a human/command review described in tasks.md, not new automation.
- Extending the planning loop itself. The document describes the loop as it already behaves; it does not redefine it.

## Decisions

**Section-per-requirement structure instead of a freeform notes layout.** Each requirement in the spec delta becomes its own top-level heading in `NOTES.md`. Alternative considered: a single prose document with inline subheadings, which reads more naturally but makes it hard to confirm that every required topic is present and would fail the navigability requirement.

**Describe commands, do not wrap them in scripts or aliases.** The spec requires commands to be runnable as written, so `NOTES.md` lists the literal commands. Alternative considered: adding npm scripts or a Makefile to shorten them, rejected because it adds files outside this change's scope envelope and makes the listed commands depend on a wrapper the reader must trust.

**Document the OpenSpec layout from what exists on disk, not from the tool's defaults.** The planning-loop section names the directories the reader will actually see after this change. Alternative considered: paraphrasing the OpenSpec product documentation, rejected because the reader needs this repository's layout, not the tool's general one.

## Risks / Trade-offs

- [Risk] The documented planning loop drifts out of date as the harness evolves → Mitigation: the constraints section states that `NOTES.md` is maintained alongside the loop and flags review of that section as an open follow-up.
- [Risk] A contributor treats `NOTES.md` as authoritative over the README → Mitigation: the purpose section links to the README for the one-line description and reserves `NOTES.md` for orientation detail, so the two do not compete.
