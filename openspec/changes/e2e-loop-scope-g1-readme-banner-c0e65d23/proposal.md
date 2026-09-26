# Proposal

## Why

The `orca-companion` repository is the end-to-end loop demonstration target
for the Orca agent harness. Its baseline `README.md` (committed at
`e951e88`) currently contains only an H1 title, a one-sentence description,
and an italic note that defers further sections ("More sections
(Installation, Usage, etc.) will be added in later changes."). Nothing on
the page identifies the repository's role as a demonstration anchor for
the Orca e2e-loop, so a reader landing on the GitHub front page has to
infer that role from the repo name alone.

Adding a short, visually distinctive banner directly under the title makes
the project's role obvious at a glance, and gives future Work Packages a
stable surface to extend (for example, swapping in a status badge or
linking to the integration branch) without re-litigating what the banner
means. This Work Package establishes the `readme-banner` capability: the
contract that `README.md` must satisfy with respect to that banner.

## What Changes

- **Add** a Markdown blockquote banner at the top of `README.md`, placed
  immediately after the H1 title and before any other body content. The
  banner identifies `orca-companion` as an Orca e2e-loop demonstration
  target.
- **Define** a new OpenSpec capability `readme-banner` that captures the
  required content, position, and formatting of that banner so future
  changes can reference and extend it without rewriting the contract
  implicitly.
- **No source code, configuration, or other tracked files are modified.**
  This Work Package Scope Envelope restricts all changes to `README.md`,
  and the change is intentionally narrow so the Work Package can be
  admitted against the existing baseline without touching unrelated
  surfaces (such as `NOTES.md`, `.gitignore`, or `orca-companion.json`).

## Capabilities

### New Capabilities
- `readme-banner`: Defines the Markdown banner at the top of `README.md`
  that signals the project's role as an Orca e2e-loop demonstration
  target. The capability locks in the banner's placement (immediately
  after the H1 title), its required wording (must identify the project
  as an Orca e2e-loop demonstration target), and its format
  (GitHub-flavored Markdown blockquote with a leading emoji). Any
  future change that introduces, replaces, or removes that banner MUST
  update this capability through an `ADDED` or `MODIFIED Requirements`
  block.

### Modified Capabilities
- _(none — `README.md` exists at baseline, but no capability currently
  governs the banner, and no other tracked file references the banner
  contract yet.)_

## Impact

- Modified file: `README.md` at the repository root (the only path
  inside the Work Package Scope Envelope).
- The banner is added directly below the existing H1 title
  (`# orca-companion`); the title itself, the one-sentence description,
  and the italic deferral note are preserved unchanged.
- No new tracked files are created, no other files are modified or
  deleted, and no runtime dependencies, external services, or build
  artefacts are introduced.
- Future changes that touch the banner wording, placement, or format
  MUST update the `readme-banner` spec via an OpenSpec `MODIFIED
  Requirements` block rather than rewriting the contract implicitly.

