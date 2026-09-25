# Design

## Context

The repository starts from a single isolated baseline commit (`dedbbad e2e26: isolated project baseline`) on a dedicated work-package branch. `README.md` currently contains only an H1, a one-line description, and a forward-looking italic note. The Work Package Scope Envelope for this change is restricted to `README.md`; no other path may be edited, created, or removed. Subsequent work packages in the `e2e-loop-scope` generation are expected to expand `README.md` (Installation, Usage, etc.) and may rely on the banner being the canonical place where the project's demo nature and harness-driven workflow are announced.

## Goals / Non-Goals

**Goals:**
- Insert a single banner block at the top of `README.md` that signals the project's demo nature, the orca-companion agent harness as the driver, and the expectation that more sections will follow in later changes.
- Keep the banner visually distinct from the rest of the file (blockquote) so it is unmissable to a first-time visitor.
- Restate the existing forward-looking note inside the banner so the banner is the single source of "what to expect next."
- Stay strictly within `README.md`; touch no other file in the repository.

**Non-Goals:**
- No new top-level sections, no H2/H3 headings, no lists, no tables, no images, no badges, no external links, no HTML, no fenced code blocks.
- No changes to `orca-companion.json` (which encodes harness configuration for the orca-companion agent) or to `.gitignore`.
- No introduction of a CI workflow, release script, or repository metadata change.
- No rewriting of the existing one-line project description paragraph; it stays in place below the banner.

## Decisions

1. **Banner is a Markdown blockquote, not a callout/admonition.** A blockquote (`>`) is the lowest-common-denominator Markdown construct supported by GitHub, GitLab, Bitbucket, VS Code, and command-line viewers. Admonitions (`> [!NOTE]`) and HTML details/summary blocks vary by renderer; a plain blockquote keeps the banner visible everywhere.

2. **Banner goes directly under the H1, before any other prose.** Placing the banner first guarantees a visitor sees the demo/harness/forward-looking signals before the short description. Putting it after the description would bury the context that the rest of the file may grow incrementally.

3. **Three banner lines, each carrying one piece of information.** One line for "demo," one line for "orca-companion agent harness drives the project," one line for "more sections later." Splitting the content across three lines keeps each piece skimmable and gives the validator a straightforward grep-style check.

4. **Forward-looking note moves into the banner, not duplicated.** The current italic note (`_More sections (Installation, Usage, etc.) will be added in later changes._`) is rewritten as a plain banner line. This keeps a single source of truth and avoids a redundant line after the description paragraph.

5. **No tooling, no scripts, no automation.** Because the Scope Envelope restricts edits to `README.md`, the implementation phase is a single hand-edit (or single-shot rewrite) of one file. There is no script, no generator, and no template engine to introduce or maintain.

## Risks / Trade-offs

- **Risk:** A reviewer might want badges (build status, license) on the README. *Mitigation:* The Scope Envelope forbids introducing external resources or new files. Badges require image URLs, which violate the self-contained-banner requirement. The decision to omit them is intentional; later work packages can address them if a future Scope Envelope allows it.
- **Risk:** The banner could feel redundant with the existing one-line description. *Trade-off:* The description focuses on *what* the project is; the banner focuses on *how* it is being built and *what is coming next*. Keeping both is deliberate — they answer different questions.
- **Risk:** Future work packages may want to reposition the banner (e.g. behind a collapsible details block). *Mitigation:* The capability spec keeps the banner a flat blockquote so the constraint is auditable; if a future change wants to alter the banner's rendering, it must update the capability first.
- **Risk:** The implementation phase is small enough to over-engineer (linting, validation scripts). *Trade-off:* The change is intentionally tiny — one file, ~5 lines of new content. Adding tooling around it would expand the Scope Envelope and is therefore rejected.
