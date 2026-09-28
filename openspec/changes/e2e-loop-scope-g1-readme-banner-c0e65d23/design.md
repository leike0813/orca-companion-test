# Design

## Context

`README.md` currently begins with the heading `# orca-companion` followed by a
two-line introductory paragraph and an italic placeholder line ("More sections
… will be added in later changes."). There is no visual framing at the top of
the document, and the level-1 heading sits flush against the left margin like
any ordinary Markdown heading. The Work Package Scope Envelope restricts this
change to `README.md`, so the banner must be implemented purely with
GitHub-flavored Markdown primitives already available in the file.

## Goals / Non-Goals

**Goals:**

- Add a banner block at the very top of `README.md` that is visually distinct
  from the rest of the document while remaining plain GitHub-flavored
  Markdown.
- Keep the project name (`# orca-companion`) as the banner's level-1 heading so
  the readme still advertises the project name to crawlers and link previews.
- End the banner with a horizontal rule (`---`) so the rest of the file
  (introductory paragraph and future sections) reads as a separate body region.
- Map the banner's required structure to the `readme-banner` spec so the spec,
  design, and tasks stay aligned.

**Non-Goals:**

- Adding image assets, logos, or new files under the repository root; the Scope
  Envelope is `README.md` only.
- Introducing HTML, raw tags, or templating inside `README.md`; the banner must
  remain reviewable in any Markdown editor.
- Restructuring the rest of the file (the introductory paragraph and italic
  placeholder stay where they are; later work packages will extend the body).
- Introducing the `readme-body` capability or any other capability beyond
  `readme-banner`.

## Decisions

- **Blockquote-framed banner.** The banner uses a Markdown blockquote (`>`)
  prefix on each of its lines so it renders as a visually framed box in
  GitHub-flavored Markdown without needing HTML, custom CSS, or images. A flat
  heading + paragraph layout was rejected because it does not differ enough
  from the rest of the document to function as a hero area.
- **Level-1 heading inside the blockquote.** The project name stays as a
  single `# orca-companion` heading, but the heading now lives inside the
  blockquote so it is part of the banner block. This preserves the existing
  link-preview / search-index signal for the project name while moving it into
  the framed area.
- **One-sentence tagline plus a short fact strip.** Immediately under the
  heading the banner carries a single-sentence tagline (the project's
  purpose) followed by a one-line "strip" of identifying facts (`Spec-driven
  · E2E loop · Codex worker`). The strip uses `·` separators to avoid looking
  like a navigation row, and the whole strip fits on a single line so the
  banner height stays predictable across renderers.
- **Horizontal rule separator.** The banner ends with a `---` line so the
  existing introductory paragraph and italic placeholder below it read as a
  distinct body section rather than a continuation of the banner.
- **No new top-level files.** All banner content lives inside `README.md` so
  the Scope Envelope (`include: ["README.md"]`) remains the only path the
  implementation touches.

## Risks / Trade-offs

- **Blockquote banners render inconsistently across non-GitHub renderers.**
  → GitHub-flavored Markdown renders a multi-line blockquote as a single
  framed box; some other renderers indent each line individually. The banner
  remains readable in either case, and the change targets the GitHub viewer
  used by the project's source-hosting workflow.
- **Tagline and fact strip can drift out of date.** → The spec phrases both as
  required content, so a later work package that wants to update the wording
  must either amend the `readme-banner` spec or open a new change scoped to
  `README.md`.
- **Heading inside a blockquote may look surprising to readers.** → The spec
  calls out the heading-inside-blockquote structure explicitly so validators
  and reviewers know it is intentional, and the design notes the rationale.

## Open Questions

None. The Scope Envelope, capability path, banner shape, and required Markdown
primitives are all fixed by the work package contract and the prior
`readme-banner` decision captured above.
