# Maintainer Notes — orca-companion

This file is the maintainer-facing note for the `orca-companion`
repository. It explains what the repository is for, what it deliberately
leaves out, and where the work that grows out of it is tracked.

## Purpose

`orca-companion` exists as an end-to-end demonstration target for the
`orca-companion` agent harness. The repository is intentionally tiny so
that the harness can drive it through a full change lifecycle —
planning, implementation, validation, and archival — without any of the
noise that a real product codebase would introduce. Each OpenSpec
change in `openspec/changes/` is a self-contained fixture that exercises
one slice of that lifecycle.

The repository is the harness's playground, not a deliverable product.
Its value comes from being a stable, predictable surface that the
harness can repeatedly plan and execute against.

## What this repo is _not_

To keep the harness loops honest, the repository deliberately does
**not** contain:

- Production code. There are no source trees, no build pipelines, no
  packaging, and no runtime binaries. Anything that looks like a real
  feature implementation is out of scope by design.
- Real install instructions. There is no installer, no release artefact,
  and no documented upgrade path. The repository is not something an
  end user is expected to clone and run.
- Multi-component configurations. The only configuration shipped with
  the repository is `orca-companion.json`, which is the harness config
  itself. There are no databases, services, queues, or external
  integrations to wire up.
- Credentials or secrets. The repository never holds API keys,
  signing material, private endpoints, or tokens. All harness
  credentials are referenced by name (for example `smoke-key`) and
  resolved by the harness out of band.
- User-facing documentation. There is no `docs/` site, no
  tutorials, and no marketing copy. Anything that points an end user at
  the repository as a usable product is intentionally absent.

If a future change proposes to add any of the above, that proposal
should explain why the harness needs it and why the existing fixture
shape is no longer sufficient.

## Where follow-up work lives

Follow-up work for the `orca-companion` demo is tracked in two places,
and contributors should check both before starting a new slice:

- GitHub issues on the `orca-companion` repository. Issues are the
  primary planning surface for new harness scenarios, bug fixes in
  the fixture itself, and cross-cutting improvements that span more
  than one OpenSpec change.
- OpenSpec changes under `openspec/changes/`. Each subdirectory is one
  proposed change with its own `proposal.md`, `tasks.md`, and
  `specs/` deltas. A new change should be added in its own directory
  alongside the existing ones and should reference the GitHub issue
  that motivated it.

When a change is finished, it is archived by the harness into
`openspec/changes/archive/` together with its specs, so the history of
what has been demonstrated remains auditable. The currently active
change is the one whose directory is not under `archive/`.

## File conventions

This file is plain GitHub-flavored Markdown. It does not use YAML or
TOML front-matter, does not embed HTML, and does not contain build-step
directives. Future maintainer notes should follow the same convention
so that the file stays renderable on GitHub without any preprocessing.
