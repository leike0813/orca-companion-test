# Design

## Context

The repository is a documentation-and-config demo: `README.md` holds the
project description, `NOTES.md` holds the working notes, and
`orca-companion.json` holds harness configuration. There is no source tree, no
build, and no test runner. See `proposal.md` for why the change is wanted and
`specs/readme-banner/spec.md` for the behavior contract.

Two constraints shape the approach. First, the Work Package Scope Envelope
permits exactly one file, `README.md`, so the design cannot introduce a
templating step, a linter, or a generator to keep the banner in shape. Second,
the README already ends with a placeholder promising later sections, so the
banner has to set reader expectations without contradicting that line.

## Goals / Non-Goals

**Goals:**

- Produce a `README.md` banner that satisfies every requirement in the spec
  delta by hand, so compliance is verifiable by reading the file.
- Keep the banner stable in shape: a reader who has seen one banner knows what
  to look for in the next.

**Non-Goals:**

- Automated enforcement or generation of the banner — outside the scope
  envelope and unsupported by anything already in the repository.
- Writing the Installation and Usage sections the README currently defers; the
  banner only explains that the rest of the document is still a stub.
- Editing `NOTES.md` or any other file.

## Decisions

### Banner is plain Markdown prose directly under the title

The banner is an ordinary Markdown block — a short status line followed by one
sentence of purpose — placed immediately after the `#` title, with no fenced
code block, badge image, or HTML.

*Rationale:* the spec requires the parts to be present and in a known position,
and plain Markdown is the only form that stays inside a single-file scope while
remaining checkable by eye and readable on any renderer.

*Alternative considered:* a shields.io badge image was rejected because it
introduces an external dependency on a third-party host, which cannot be
verified offline and would break the single-file, no-network constraint.

### Status label is literal text, not a level

The banner states the project's status in words (that this is a demonstration
harness for the agent harness) rather than encoding a maturity level in a
single word.

*Rationale:* a one-word label such as `alpha` needs a definition somewhere, and
there is nowhere inside the scope envelope to define one; prose carries its own
meaning on first read.

*Alternative considered:* an `alpha`/`beta`/`stable` keyword was rejected for
the same reason — it defers the explanation to a document that does not exist.

### Existing description paragraph is preserved verbatim

The banner is added above the current description paragraph rather than
replacing it, and the deferred-sections placeholder line is left in place.

*Rationale:* the description is already accurate, and the placeholder is what
tells a reader the document is incomplete; rewriting either would be churn
outside the change's purpose.

*Alternative considered:* folding the description into the banner was
rejected because it would duplicate the purpose sentence across two locations
that could then drift apart.

## Risks / Trade-offs

- [Banner drifts from the project's actual purpose as the demo evolves] → Keep
  the sentence about what the repository demonstrates rather than about its
  internals, so later changes that add features do not invalidate it.
- [Position and parts are unenforced, so a future edit could drop the banner] →
  Accept manual review; the required content is small enough to verify by
  reading the top of the file.
- [No automated check means nothing prevents a second banner being added] →
  Accept; the spec's single-banner requirement is stated for the reader, and
  the scope envelope leaves no place to host a check.

## Migration Plan

Add the banner to `README.md` in a single commit. Rollback is reverting that
commit, which restores the previous README exactly; no other file references
the banner.
