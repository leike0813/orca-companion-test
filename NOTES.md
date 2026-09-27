# Project Notes

This document collects orientation, conventions, and pointers for contributors working on the `orca-companion` repository. It complements `README.md` rather than replacing it: `README.md` remains the public entry point, while this file records lower-churn guidance that the top-level readme does not cover.

## Overview

The repository is an end-to-end demonstration harness for the Orca companion agent workflow. It currently ships a stub `README.md`, the harness configuration file `orca-companion.json`, and this notes file. Future changes are expected to extend the documentation layout incrementally as additional capabilities land.

The scope of this document is intentionally narrow. It records project orientation, contributor conventions, and pointers to related surfaces; it does not duplicate the public readme and it does not describe how to install or run anything.

## Conventions

Contributors should follow the conventions below when extending the repository. These conventions apply to every change, including documentation-only changes such as this one.

- Changes are organized as OpenSpec change proposals under `openspec/changes/` and progress through proposal, design, spec, and tasks artifacts before any implementation lands.
- Repository-root Markdown documents (`README.md`, `NOTES.md`) stay plain GitHub-flavored Markdown with no front matter, no templating, and no build-time preprocessing.
- The first non-blank line of any new root-level Markdown file is a level-1 title; subsequent top-level structure uses level-2 headings.
- Each OpenSpec change is constrained by a Work Package Scope Envelope that lists exactly which paths the change may add, modify, or remove; no path outside that envelope may be touched in the same change.
- The harness configuration in `orca-companion.json` is treated as data: changes to it follow the same OpenSpec workflow as code changes and never happen as a side effect of another change.

## Pointers

The following surfaces are useful starting points for contributors who want to understand or extend this repository.

- `README.md` — public entry point and high-level project description.
- `orca-companion.json` — harness configuration, including the coordinator model, planner settings, and execution limits.
- `openspec/config.yaml` — OpenSpec schema declaration for the repository (`spec-driven`).
- `openspec/specs/` — archived and approved capability specifications that are part of the main branch.
- `openspec/changes/` — active and archived change proposals, each in its own directory.
- `.gitignore` — list of paths intentionally excluded from version control.

## Open Questions

There are no open questions at this time. Any question that arises while extending this document or any other part of the repository should be filed as a new OpenSpec change proposal rather than answered implicitly here.
