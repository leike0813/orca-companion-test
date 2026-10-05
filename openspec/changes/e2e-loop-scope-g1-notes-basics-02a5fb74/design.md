# Design

## Context

See `proposal.md` for motivation. The current state that matters here: the repository root contains a readme stub, an OpenSpec scaffold, and orchestration configuration, and there is no document that orients a reader. The change is documentation only, adds no code, and introduces no dependency, so the design is limited to making the document's structure and its verifiability explicit.

## Goals / Non-Goals

**Goals:**

- One file, `NOTES.md`, at the repository root, holding all of the new orientation content.
- A heading structure that a shell check can assert without a Markdown parser.
- A path-reference rule simple enough to check with `grep` and `test` alone.

**Non-Goals:**

- Restructuring, renaming, or generating other documentation, and changing the OpenSpec scaffold.
- Any runtime code, configuration, dependency, or CI wiring.
- Guaranteeing the notes stay permanently accurate; the requirement only asks that they are accurate at the time of this change.

## Decisions

**A single root-level file rather than a documentation directory.** The audience is a reader who has just opened the repository and wants orientation in one hop. A `docs/` tree would add a navigation step for four short sections and would pull a new directory into a change scoped to one file. Alternative considered: one file per topic — rejected, the content is too small to justify the structure.

**A fixed, flat heading structure verified with `grep`.** The document uses one level-one title followed by exactly four level-two sections in a fixed order. Asserting this with `grep -n '^#'` keeps verification dependency-free; a Markdown parser would be a new dependency for no behavioral gain. Alternative considered: allowing any headings and validating rendering — rejected, "renders fine" is not an acceptance condition.

**Path references are backticked tokens, and any backticked token that contains a `/` or ends in `.md` is treated as a repository path.** This gives one mechanical rule that separates paths from prose and from backticked commands (a command such as a git invocation contains no slash and no `.md` suffix). Alternative considered: require paths to live in a dedicated list — rejected, it pushes the rule into prose instead of making the document itself self-describing.

## Risks / Trade-offs

- The path rule is a convention, not a parser: a backticked token that names a path without a `/` and without a `.md` suffix would not be checked. Mitigation: every path the document names today carries a slash or a `.md` suffix, and the check reports the count of checked references so an empty result is visible.
- Heading order is a real constraint, so reordering sections later would fail the check even though the document would still read well. Mitigation: the check is cheap to rerun and a future change can adjust it deliberately.
- The notes can drift from the tree as the repository evolves. Mitigation: this is a known limitation of a hand-written document; no generation step is introduced, to keep the change to a single file.

## Migration Plan

Not applicable. The change adds a new file and modifies nothing; removing `NOTES.md` is a complete rollback.

## Open Questions

None. The document's language, length, and tone are left to the author, and none of them change the requirements or the checks.
