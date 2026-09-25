# Proposal: README Banner

## Why

The current `README.md` only contains an H1 title, a one-line project description, and a forward-looking italic note. For an end-to-end demonstration of the orca-companion agent harness, a visitor landing on the repository gets no immediate signal that:

1. The repository is intentionally a demo harness for orca-companion, not the production harness itself.
2. The project is being driven through a multi-agent coordination loop rather than a traditional hand-edited codebase.
3. The README is a living artifact that will expand (Installation, Usage, etc.) across subsequent work packages.

Without that upfront context, contributors may misread the project as a finished tool or mistake later README additions for unrelated edits. A short, prominent banner at the top of the README fixes that without duplicating the body that later work packages will introduce.

## What Changes

1. **Add a banner block immediately under the H1 title**
   - Rendered as a Markdown blockquote (`>` prefix) so it is visually distinct from the rest of the document.
   - Three short lines that together cover: project purpose, harness context, expectation of incremental content.

2. **Preserve the existing project description**
   - The current `An e2e-loop demonstration project ...` paragraph stays in place beneath the banner.
   - The forward-looking italic note (`More sections (Installation, Usage, etc.) will be added in later changes.`) is restated inside the banner so the banner becomes the single source of "what to expect next."

3. **No structural, functional, or out-of-scope changes**
   - No new top-level sections, no images, no external links, no badges, no HTML.
   - Banner content is plain Markdown — no fenced code blocks, no inline images.
   - No edits to `orca-companion.json`, `.gitignore`, the git history, or any other file outside `README.md`.

## Capabilities

### New Capabilities
- `readme-banner`: Describes the persistent banner block at the top of `README.md` that signals the project's demo nature, the orca-companion agent harness as its driver, and the expectation that more sections will follow in later changes.

### Modified Capabilities
- _None._

## Impact

- `README.md`
