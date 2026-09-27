## Purpose

NOTES.md is the canonical home for project-internal development notes covering conventions, decisions, and open questions that intentionally stay out of README.md. Downstream changes and contributors extend this baseline rather than maintaining parallel note files.

## Conventions

Add new entries directly under the matching H2 section using short Markdown paragraphs or bullet lists, keep each item self-contained, and prefer linking to a worktree or change directory over embedding long excerpts. README.md remains the source of truth for user-facing material, so NOTES.md only cross-links to it instead of duplicating it.

## Decisions

We place NOTES.md at the repository root next to README.md so it is discoverable at the top level, and we fix the four section headings (Purpose, Conventions, Decisions, Open Questions) so downstream tooling can rely on stable anchors. The initial body content is intentionally minimal so future changes can extend the document without rewrites.

## Open Questions

None at this baseline; future changes that introduce new conventions, decisions, or follow-up items should append them to the matching section above.
