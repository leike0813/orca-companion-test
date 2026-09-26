# NOTES

## Overview

The orca-companion repository is an end-to-end demonstration project for the orca-companion agent harness, showcasing how planning, implementation, validation, and finalization work together under a single coordinator model. It currently exposes a placeholder `README.md` and the `orca-companion.json` harness configuration, with new capabilities introduced through OpenSpec changes tracked under `openspec/changes/`. This file is the canonical place for day-to-day observations, handoff context, and scratchpad items that should survive between work packages, so contributors do not need to read the full README to understand the project.

## Conventions

Every entry in this file follows a small set of rules that keep the notes consistent and easy to scan:

- **Dated headings**: each new entry is a level-3 (`###`) heading prefixed with an ISO-8601 date (`YYYY-MM-DD`) and a short slug, for example `### 2026-09-27 — example entry`.
- **Markdown only**: content is plain GitHub-flavored Markdown; no HTML tags, inline scripts, or raw markup are permitted, and confidential material (third-party credentials, private URLs, internal hostnames, customer identifiers) must never be quoted verbatim.
- **Append at the end**: new entries are added to the bottom of the relevant section rather than inserted into older entries, so the file reads chronologically and older notes are preserved verbatim.
- **Stable size**: the file stays under 200 lines until a follow-up change explicitly expands it, so reviewers can rely on `wc -l NOTES.md` as a quick sanity check.

## Open Items

- _No open items logged yet — append new bullets below as they come up. Each item should describe the question or follow-up in one or two sentences and link to the relevant work package, spec delta, or commit when one exists._
