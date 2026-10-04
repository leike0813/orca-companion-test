# Design

## Context

See `proposal.md` for the motivation. The concrete constraints shaping the approach:

- The work package's scope envelope admits exactly one product path, `NOTES.md`, so the design cannot introduce a `docs/` directory, a notes index, or a second document.
- The only machine-readable source of truth in the repository is `orca-companion.json` (schemaVersion 2). It is nested and long — the execution, planning, and limits blocks alone run past two hundred lines — so it is impractical to read casually.
- There is no test runner, package manifest, or build step, so acceptance cannot rely on infrastructure that does not exist.
- `README.md` already carries the project title. Duplicating it would create two places to update.

## Goals / Non-Goals

**Goals:**

- Make the repository self-describing from `NOTES.md` alone for the three questions a worker actually asks first: what is this, what runs me, what is left.
- Keep the notes cheap to keep true: each configuration fact appears once, in prose form, with a pointer back to `orca-companion.json` as the authority.
- Make acceptance decidable by a single read-only shell command that works in a bare worktree.

**Non-Goals:**

- Generating `NOTES.md` from `orca-companion.json` at build time. That would add tooling and a second file outside the envelope.
- Exhaustively transcribing every configuration key. A reference-by-description file drifts less than a transcription, and the full document is one `cat` away.
- Establishing a general documentation standard for the project; the repository has no other documents to standardize against.

## Decisions

**A single root-level `NOTES.md` with fixed, ordered sections.** The sections are fixed — Overview, Repository Layout, Companion Configuration, Working Agreements, Open Items — rather than free-form, because the spec requires a reader to be able to locate a specific fact without scanning. Fixed order also makes drift visible in review: a moved heading is a diff.

Alternative considered: a bulleted quick-reference with no headings. Rejected — it scales badly, and a reader would have to read the whole file to answer one question.

**Describe the configuration; never copy it.** The Companion Configuration section paraphrases each block in a sentence or two and names the JSON path (`execution.harness`, `execution.limits.concurrencyLimit`, and so on) so the reader can jump to the authority. The alternative — pasting the JSON into a fenced block — was rejected: it would be a second copy that silently goes stale, and the spec's drift requirement forbids it.

**Describe only the settings that govern how work happens, not every setting.** Credentials, connection labels, and model identifiers are recorded as a brief identification line rather than itemized. Rationale: the notes exist to answer "how do I work here", and the provider-connection detail is a `jq` query away while the execution model is what a new agent cannot guess.

**Acceptance is a shell one-liner, not a script or test.** The check is `test -f NOTES.md && head -n 1 NOTES.md | grep -q '^# '`. Rationale: the worktree has no package manager, so any test harness would mean adding a dependency and a file outside the envelope. A file-existence-plus-heading assertion is exactly the observable behavior the spec requires, and it is runnable by hand in any shell.

Alternative considered: asserting the presence of every required section heading in the same command. Rejected for the acceptance check — it hardcodes the section list into a second place that could itself drift, and a human reviewer catches a missing section immediately. The section list is still normative in the spec.

**Open Items names the absence of product code explicitly.** The most misleading thing about an empty recovered repository is silence: an agent may assume a codebase exists and go looking for it. Stating plainly that there is no product code yet, and that this work package covers only `NOTES.md`, is worth one line.

## Risks / Trade-offs

- [Notes drift from `orca-companion.json` as settings change] → Every configuration line names its JSON path, so a maintainer updating a setting has an obvious line to update, and the Working Agreements section restates only the constraints a worker must not violate. Drift is detectable in any diff touching the companion file.
- [The notes become the place everyone dumps detail] → The spec fixes the section set and forbids duplicating `README.md` or the companion JSON, so growth has to go into the right section or not happen.
- [A shallow acceptance check passes on a thin file] → The check proves the file exists and is recognizable as notes; content quality is enforced by the spec during review rather than by the command. Accepted deliberately, since a content-parsing check would re-encode the document structure in a second place.
- [The OpenSpec scaffolding (`openspec/config.yaml`, the `.gitkeep` files) adds files outside the envelope] → These are OpenSpec root markers, not product artifacts, and they are required for `openspec validate` to resolve the change. The envelope constrains the product impact declared in `proposal.md`, which names only `NOTES.md`.

## Migration Plan

None required. The change adds one new file and modifies nothing; removing `NOTES.md` fully reverts it.

## Open Questions

- Whether a notes file should later be split per work package once more than one exists. Deferred: that decision depends on repository content this work package does not cover, and it does not affect the specs, the approach, or the task breakdown here.
