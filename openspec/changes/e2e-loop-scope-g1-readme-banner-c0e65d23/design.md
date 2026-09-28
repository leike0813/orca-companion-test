# Design

## Context

The baseline repository contains four files at the root: `README.md`,
`NOTES.md`, `orca-companion.json`, and `.gitignore`. `README.md` is the
project-facing entry point and currently contains only a project H1, a
single-line italic blurb, and a trailing italic line promising that richer
sections (Installation, Usage, etc.) will be added by later changes. None of
that content is pinned by any spec today, so any downstream change can
silently edit, reorder, or remove it.

This change introduces the `readme-banner` capability so `README.md` grows a
contractually pinned introductory surface. The capability mirrors the
work-package slug `e2e-loop-scope#g1:readme-banner` and is intentionally
narrow: it pins exactly two things in `README.md` -- the H1 on line 1 and a
one-line banner blockquote on line 3 -- and leaves everything else free for
downstream changes to append. The banner is also constrained to be a
documentation-only surface so it stays a Markdown blurb and never becomes a
shadow configuration or executable assertion.

## Goals / Non-Goals

**Goals:**

- Establish a stable, well-known banner at the top of `README.md` that
  downstream changes, automation, and consumers can rely on as a fixed
  anchor.
- Pin the H1 text on line 1 and the banner blockquote's leading sentence on
  line 3 verbatim so the surface does not drift between changes.
- Pin the position of the banner to line 3 (with line 2 as a required blank
  separator) so downstream consumers can compute byte-exact positions and
  rely on a single LF line ending.
- Keep the banner a documentation-only surface so it cannot drift into
  executable content, version pins, or behavior assertions that would shadow
  the project's declarative sources.
- Keep the contract minimal so downstream changes can extend `README.md`
  freely below the banner without amending this capability.

**Non-Goals:**

- Filling `README.md` with richer content (Installation, Usage,
  Contributing, etc.). Those sections will be added by later changes after
  the banner.
- Modifying `NOTES.md`, `orca-companion.json`, `.gitignore`, or any other
  baseline file. The Work Package Scope Envelope restricts this change to
  `README.md` only.
- Pinning prose that appears after the banner. Only the H1 and the banner
  blockquote are pinned.
- Introducing tooling, scripts, or CI checks that read or write `README.md`.
- Forcing line-endings on the whole repository. Only the banner contract
  requires LF endings on `README.md`; the broader file-format policy is left
  to future changes.

## Decisions

- **Capability path: `readme-banner`.** The capability name mirrors the
  work-package slug `e2e-loop-scope#g1:readme-banner` so the spec ID and the
  dispatch handle stay aligned. Future richer README capabilities
  (`readme-install`, `readme-usage`, etc.) can extend without renaming this
  one.
- **Pin a single H1, not a family of headings.** Pinning only the H1 keeps
  the contract narrow and avoids dragging in heading-level conventions that
  do not yet exist.
- **Banner form: single-line Markdown blockquote (`>` line).** A blockquote
  visually sets the banner apart from the H1 and from any later prose, is
  trivial to grep deterministically, and renders cleanly in plain Markdown
  viewers and on GitHub. A multi-line or stacked blockquote is rejected so
  the surface stays byte-deterministic.
- **Pin banner position to line 3 exactly.** Earlier revisions allowed
  `H1 + 1` or `H1 + 2` to tolerate optional separation. The capability now
  pins line 3 exactly so downstream consumers can compute byte-exact
  positions without ambiguity. Line 2 is the required blank separator.
- **Require LF line endings in `README.md`.** CR-only or CRLF endings would
  shift byte positions across platforms and break byte-exact assertions. The
  capability requires LF so the position pin is portable.
- **Pinned leading sentence, free body.** Only the leading sentence of the
  banner is pinned verbatim. Future changes can adjust the trailing
  prose of the same banner line without amending this capability, provided
  the leading sentence remains intact and the banner stays a single line.
- **Banner is a documentation-only surface.** The banner MUST be plain
  Markdown prose with no fenced code, inline HTML, version pin,
  machine-readable identifier, or behavior/configuration/command assertion.
  This mirrors the documentation-only contract already used by the
  `notes-basics` capability for `NOTES.md`, and prevents the banner from
  drifting into a shadow configuration.
- **Trailing italic line is intentionally unpinned.** The current italic
  sentence `_More sections ... will be added in later changes._` is
  documentation, not contract. The implementer may keep it, move it, or
  remove it; downstream changes that add real sections will likely remove
  it anyway.
- **Documentation-only after the banner.** The third requirement explicitly
  states that any prose after the banner is documentation-only, which
  guarantees downstream changes have room to grow `README.md` without
  bumping the version of this capability.

## Risks / Trade-offs

- **Grep fragility for the pinned phrase.** The banner's leading sentence is
  pinned verbatim, including punctuation, whitespace, and the `**Note:**`
  emphasis. Downstream formatting tools that auto-wrap or auto-emphasize
  Markdown could break the grep. The trade-off favors a stable pinned
  surface over flexible formatting; future changes that need to break the
  pin must bump this capability deliberately.
- **Single-line blockquote is less expressive than a multi-line one.** A
  longer banner would have to either lose its pinned form or force this
  capability to track every line. Restricting the banner to a single line
  keeps the contract tiny at the cost of one sentence of expressiveness.
- **Other capabilities may want to share `README.md`.** If a downstream
  capability wants to pin its own heading inside `README.md`, the
  `readme-banner` capability does not preclude that -- the contract only
  pins the H1 and the banner blockquote. The risk is that an over-zealous
  downstream capability could try to relocate or restyle the banner; the
  "byte-identical" wording in the third requirement explicitly forbids that.
- **Documentation-only requirement adds a third contract dimension.**
  Reviewers now have to confirm not just the wording and position of the
  banner but also that it stays prose. The trade-off favors preventing
  accidental shadow-configurations over leaving the banner maximally
  expressive.
