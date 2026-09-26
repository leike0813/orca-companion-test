# Proposal

## Why

The current `README.md` only carries the project title and a single
description line, with a trailing italic note promising "more sections"
in later changes. A first-time visitor — human or agent — landing on the
repository has no immediate, unambiguous signal that the project is an
internal `orca-companion` agent-harness e2e-loop demonstration target and
not a real product. That ambiguity is the gap this change closes: the
README needs an at-a-glance banner that fixes the project's role before
any other content is read.

## What Changes

- Add an internal-use / demo-fixture banner at the very top of
  `README.md`, immediately after the `# orca-companion` title.
- The banner MUST explicitly identify the repository as the
  `orca-companion` agent-harness e2e-loop demonstration target.
- The banner MUST make clear that the repository is _not_ a real
  product, has _no_ install path, and is _not_ intended for end-user
  consumption.
- The banner MUST stay a plain-Markdown, GitHub-renderable block: no
  HTML, no images, no fenced build-step directives, and no YAML / TOML
  front-matter.
- Existing README content (the one-line description and the italic
  "more sections" note) MAY be re-ordered or re-worded so the banner
  reads first; no other files are touched.

## Capabilities

### New Capabilities

- `project-readme`: Defines the at-a-glance contract that the
  repository's `README.md` MUST open with a clearly delimited
  internal-use banner identifying it as the `orca-companion`
  agent-harness e2e-loop demonstration target.

### Modified Capabilities

_None._ No existing OpenSpec capability is being changed by this
proposal; the change introduces a single new capability and otherwise
leaves the repository unchanged.

## Impact

- `README.md` (the single path declared in the Work Package Scope
  Envelope). The change adds an internal-use banner at the top of
  `README.md` and may lightly adjust the wording of the existing
  description / "more sections" note so the banner reads first. No
  other file in the repository is added, removed, or modified by this
  change.
