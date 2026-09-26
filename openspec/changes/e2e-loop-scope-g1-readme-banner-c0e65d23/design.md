# Design — `e2e-loop-scope-g1-readme-banner-c0e65d23`

## Context

See `proposal.md` — Why. The current state is a repository in which
`README.md` carries only an H1 title, a one-sentence description, and
an italic note that defers further sections. The artifact introduced by
this Work Package is a single, hand-authored Markdown addition: one
blockquote banner inserted between the H1 title and the existing
description. The deliverable is a static document; there is nothing to
compile, bundle, deploy, migrate, or wire to a runtime.

The banner sits inside the `README.md` file that this Work Package's
Scope Envelope already permits editing, so no other tracked path is
touched. The full layout of the file after this change is: H1 title,
blank line, banner blockquote, blank line, original description, blank
line, original italic deferral note.

## Goals / Non-Goals

- **Goals**:
  - Produce a conformant `README.md` that satisfies every
    `### Requirement` declared in `specs/readme-banner/spec.md`
    (`ADDED Requirements` block).
  - Insert the banner immediately below the H1 title, leaving the rest
    of the baseline file unchanged in content and order.
  - Make the banner's wording, format, and placement machine-checkable
    from `README.md` alone, so a future validator can verify it
    without re-reading the change artifacts.
- **Non-Goals**:
  - No new tracked file outside `README.md` (in particular, no
    badge image, no separate `docs/banner.md`, no CI workflow).
  - No HTML, no embedded SVG, no JavaScript-rendered banner — the
    banner is plain CommonMark so it renders correctly on the GitHub
    front page with no extra tooling.
  - No reorganisation of the existing description or deferral note; the
    banner is additive.
  - No restructuring of `NOTES.md`, `.gitignore`, or
    `orca-companion.json`. Future Work Packages may revisit any of
    those surfaces — they are explicitly outside this Scope Envelope.

## Decisions

- **Decision: render the banner as a single-line `> `-prefixed
  Markdown blockquote.**
  - _Rationale_: a blockquote is the simplest CommonMark construct
    that GitHub renders with a coloured left border and indented body,
    giving the banner a clear visual identity without HTML, images, or
    CSS. It is also trivial to parse and verify with a `grep` /
    `awk` pipeline, which keeps validators cheap.
  - _Alternatives considered_:
    - HTML `<blockquote>` or `<div class="banner">` — rejected,
      because it forces every downstream renderer (GitHub mobile,
      plain-text editors, OpenSpec validators) to interpret HTML and
      diverges from the rest of `README.md`, which is pure
      CommonMark.
    - A Markdown table — rejected, because a one-row table does not
      render with the same visual emphasis and adds parsing
      complexity for marginal benefit.
    - A badge image (`![banner](...)`) — rejected, because it
      introduces a binary asset and a remote URL dependency that are
      out of Scope Envelope.
- **Decision: prefix the banner with a single emoji.**
  - _Rationale_: an emoji gives the banner a strong visual cue that
    survives plain-text rendering (where the blockquote bar is lost)
    and signals "this is a callout, not body prose" at a glance. It
    also provides a cheap, parseable hook for the
    `### Requirement: Banner uses a Markdown blockquote with an emoji
    prefix` check.
  - _Alternatives considered_:
    - Plain text prefix such as `[BANNER]` — rejected, less visually
      distinctive, and easy to confuse with body prose.
    - No prefix at all — rejected, leaves the banner looking like
      ordinary indented prose, defeating the visual-distinctiveness
      goal.
- **Decision: anchor the banner wording on two substrings —
  `orca-companion` and `Orca e2e-loop`.**
  - _Rationale_: substring anchoring makes the wording requirement
    checkable with `grep` alone, without a Markdown AST parser, and
    leaves room for future Work Packages to refine the wording (for
    example, "Orca e2e-loop integration target") without re-anchoring
    the capability.
  - _Alternatives considered_:
    - Pin the exact banner sentence — rejected, it makes every
      future wording tweak a spec change for no real benefit.
    - Pin a regex covering the full sentence — rejected, more brittle
      than two substrings and harder to read.
- **Decision: hand-author the banner; do not generate it.**
  - _Rationale_: the banner is a single blockquote line; the cost of
    generating it exceeds the cost of writing it, and a generator
    would be a new dependency surface that is out of Scope Envelope.
  - _Alternatives considered_:
    - Generate the banner from `orca-companion.json` — rejected, adds
      a script and execution surface that exceed the Scope Envelope
      (`["README.md"]`).
- **Decision: keep the existing baseline description and italic
  deferral note verbatim and in their original order.**
  - _Rationale_: the `readme-banner` capability is additive by
    design; future Work Packages (for example, adding Installation or
    Usage sections) will own the deferral note's eventual removal.
    Touching it here would expand the Scope Envelope silently.
  - _Alternatives considered_:
    - Reword the description to defer to the banner — rejected,
      changes a baseline surface that is not in scope.

## Risks / Trade-offs

- **Risk: future Work Packages reword the banner without updating the
  spec.**
  → Mitigation: the `### Requirement: Banner change is reflected in
  the spec on update` requirement locks the contract; any drift is
  caught at apply time.
- **Risk: the emoji chosen today becomes outdated or visually
  inconsistent with future banners in sibling repositories.**
  → Mitigation: the capability pins the *presence* of an emoji but
  not its codepoint, so a future Work Package can swap the emoji
  without rewriting the contract.
- **Risk: a future Work Package widens the Scope Envelope to add a
  badge, image, or external link to the banner.**
  → Mitigation: that is the right answer for richer banners — open a
  new change rather than mutating this one. The Scope Envelope is
  fixed for this Work Package (`["README.md"]`).
- **Trade-off: the banner adds two visible lines to the top of the
  page.** That is the cost of making the project's role obvious at a
  glance; the cost is bounded because the rest of `README.md` is
  intentionally empty at baseline, so the banner does not push any
  baseline content off the first screen.

## Migration Plan

- _None._ This is the first banner on `README.md`. The only
  "migration" is the act of inserting the banner for the first time;
  there is no prior banner to migrate from. The baseline `README.md`
  content (description and italic deferral note) is preserved verbatim
  and in order.

## Open Questions

None. Every durable surface this Work Package needs to reference
already exists at baseline (`README.md` and the `e951e88` commit),
so no design-level ambiguity needs to be resolved before
implementation.

