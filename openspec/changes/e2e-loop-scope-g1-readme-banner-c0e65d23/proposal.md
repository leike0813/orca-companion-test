# Proposal

## Why

The repository's `README.md` is intentionally minimal: it carries the project
title `# orca-companion` and a one-line italic blurb, but it has no
contractually pinned introductory surface. Today, the first content line under
the H1 is an italic sentence whose exact wording, position, and prominence
are not pinned by any spec, and any downstream change can silently reshape or
remove it without a spec-level signal.

That lack of pinning makes `README.md` a moving target for downstream changes,
automation, and consumers who want to refer to a stable banner. This change
introduces the `readme-banner` capability, which fixes the introductory surface
of `README.md`: a single H1 with the exact text `# orca-companion`, followed
by a single-line Markdown blockquote banner whose leading sentence is pinned
verbatim and whose position is fixed to line 3 of the file. The banner also
remains a documentation-only surface, so it cannot drift into a pseudo-config
that quietly contradicts the project's declarative sources. Downstream changes
can extend `README.md` strictly by appending new sections after the banner,
without renaming, replacing, or relocating the banner itself.

## What Changes

- Replace (or directly precede) the existing italic blurb under the
  `# orca-companion` H1 in `README.md` with a pinned Markdown blockquote
  banner.
- The banner MUST be a single-line blockquote that begins with the literal
  phrase:

      > **Note:** this repository is an end-to-end loop demonstration project for the orca-companion agent harness.

- The banner MUST sit exactly on line `3` of `README.md`: line `1` is the H1,
  line `2` is a single blank Markdown separator, and line `3` is the banner
  blockquote. No other content MAY appear between the H1 and the banner, or
  inside the banner itself.
- The banner MUST be a documentation-only surface: plain Markdown prose with
  no fenced code block, inline HTML, version pin, semantic-version string,
  machine-readable identifier, or behavior/configuration/command assertion.
- The trailing italic line
  `_More sections (Installation, Usage, etc.) will be added in later changes._`
  MAY remain below the banner, or be removed by the implementer; it is not
  pinned by this change.
- No file other than `README.md` is modified, renamed, or removed.

## Capabilities

### New Capabilities
- `readme-banner`: pins the introductory surface of `README.md` -- a fixed H1
  on line 1 and a single-line Markdown blockquote banner on line 3 whose
  leading sentence is pinned verbatim and whose contents remain a
  documentation-only surface -- so downstream changes can extend `README.md`
  after the banner without renames, relocations, or migrations.

### Modified Capabilities
None.

## Impact

- `README.md` -- the only path inside the Work Package Scope Envelope. The
  current italic blurb under the H1 is replaced (or supplemented) with a
  pinned Markdown blockquote banner, the blank separator on line 2 is
  formalized, and the banner is constrained to be a documentation-only surface
  so it cannot drift into executable content. No other file in the repository
  is touched by this change.
