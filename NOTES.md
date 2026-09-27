## Overview

The orca-companion repository hosts an end-to-end demonstration harness for the
orca-companion agent runtime. This `NOTES.md` file is the single, top-level
home for project-wide notes captured by contributors and harness runs.

## Conventions

- Keep `NOTES.md` as plain UTF-8 Markdown at the repository root; do not nest
  project notes under subdirectories.
- Preserve the three baseline headings (`Overview`, `Conventions`,
  `Open Questions`) and their order; add new sections only via an OpenSpec
  change that updates the `project-notes` capability.
- Write each baseline section as a short paragraph or bullet list so future
  changes can extend it without rewriting existing prose.

## Open Questions

- How should harness runs surface new conventions discovered during execution;
  should they auto-suggest a NOTE patch or only flag them in reports?
- Should `Open Questions` link to upstream GitHub issues once the tracker is
  wired in, or remain free-form until a tracking convention is chosen?
