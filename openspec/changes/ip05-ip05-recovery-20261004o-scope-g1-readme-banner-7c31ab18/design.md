# Design

## Context

See `proposal.md` for the motivation. The concrete constraints shaping the approach:

- The work package's scope envelope admits exactly one product path, `README.md`, so the design cannot add a `docs/` page, a `STATUS.md`, or a second document to carry the banner's content.
- `README.md` is currently one line. Anything added to it competes with a file that was deliberately kept minimal, and with `NOTES.md`, which already records the same subject matter in depth. Duplication between the two is the failure mode to design against, not the extra content itself.
- `NOTES.md` is a sibling work package's output and treats `README.md` as "the project title, and nothing else". This change amends that description: the README gains a banner, and it still must not become a second copy of the notes.
- There is no package manager, test runner, or build step, so acceptance has to be decidable with a read-only shell command in a bare worktree.
- A banner is read far more often than it is maintained. It has to stay correct after every later work package lands, which argues for stating only facts that change rarely, and for pointing at the files that carry the volatile detail.

## Goals / Non-Goals

**Goals:**

- Make the README answer, in one glance, the two questions a cold reader has: is this project lost, and where is the actual state recorded.
- Keep the banner cheap to keep true: every fact in it should be one that a work package is unlikely to invalidate, and anything volatile belongs behind a pointer.
- Make acceptance a single read-only command, so verification needs no infrastructure the repository does not have.

**Non-Goals:**

- Making the README a general readme — build instructions, usage, contributing, badges. There is nothing to describe yet; the repository has no product code and no toolchain, so any such section would be fiction that later work has to delete.
- Restating the companion configuration or the recovery items. That is `NOTES.md`'s job, and copying it is precisely the drift this design avoids.
- Reorganizing or renaming `NOTES.md`, or adding an index of in-flight changes. Both are outside this work package's envelope.

## Decisions

**The banner is a blockquote block immediately below the title.** Rendering the status as a `>` blockquote makes it visually distinct from body prose on GitHub and in most Markdown viewers, so a reader sees "this is a status note" before they read a word of it, and a future maintainer sees that the block is not the start of a documentation section. The alternative — a `## Status` heading — was rejected: it promotes the banner to a peer of the project title and invites the file to grow additional sections, which is the drift the design is built to prevent.

**The banner is three to five short lines, each stating a different fact.** The facts that earn a line are: the project is a recovered Orca worktree and recovery is still in progress; there is no product code yet, by design rather than by loss; the project basics and open items live in `NOTES.md`; the outstanding specified work lives under `openspec/changes/`. Everything else stays out. A reader who wants the detail follows a pointer; a reader who does not gets an accurate summary in one screen.

**Every fact is stated as a claim or a pointer, never as a copy.** The banner names the recovery state in a single clause and links to `NOTES.md` for the configuration, the working agreements, and the open items. The rejected alternative was embedding a condensed version of the notes in the README, which would create two places to update for every configuration change and would drift silently, since nothing detects the disagreement.

**The banner is greppable rather than merely present.** The recovery status, the absence of product code, and the `NOTES.md` pointer each appear as a literal, greppable string rather than as prose that varies between edits. Rationale: the acceptance command, and any future drift check, must not have to parse Markdown structure or fuzzy-match English. Fixed wording is what makes a one-line `grep` a sufficient acceptance check.

**The title line is preserved unchanged as the first line.** The banner is inserted after it, never before it. The existing heading already names the project and is referenced by the repository's identity, and moving or rewording it would be a change the work package does not need to make. Keeping it first also means the acceptance check's title assertion is a regression guard on the existing file rather than a new requirement.

**Acceptance is a shell one-liner, not a script or test.** The check asserts that `README.md` exists, that its first line is a top-level heading, that a `NOTES.md` pointer is present, and that the banner appears within the first few lines. Rationale: the worktree has no package manager, so any test harness would mean adding a dependency and a file outside the envelope. Alternative considered: asserting every required banner fact by separate `grep` calls. Rejected as brittle — it hardcodes the banner's wording into a second place that could itself drift, and a reviewer reads a one-line banner directly.

## Risks / Trade-offs

- [The banner goes stale as recovery completes] → The banner's durable claim is that recovery is specified work in `openspec/changes/`, not that it is unfinished; when the last change is archived, the pointer becomes trivially true rather than false. The absence of product code is likewise a statement about the present that a future work package will knowingly revise. Both are cheap to correct, and a diff touching `README.md` makes the correction visible.
- [The README becomes a second copy of the notes] → The spec fixes the banner's length and forbids restating the notes, and the acceptance check verifies a pointer rather than content parity, so a banner that grows into a documentation section fails review against a named requirement rather than silently.
- [A shallow acceptance check passes on an empty or off-topic banner] → Accepted deliberately. The check proves the file exists, keeps its title, and carries the pointer in the expected position; whether the prose is accurate and useful is enforced by the spec during review, because a content-parsing check would re-encode the banner's wording in a second file.
- [The banner overstates certainty about a project mid-recovery] → Mitigated by phrasing the status as a state of record — what is specified, and where it is tracked — rather than as a judgement about the recovery's health.
- [The sibling notes' description of the README becomes inaccurate] → Expected and intended: this change amends that description. It is a documentation-consequence of this work package, not a defect, and is left to the work package that owns the notes file to describe the banner.
- [The OpenSpec scaffolding adds files outside the envelope] → These are OpenSpec root markers, not product artifacts, and they are required for `openspec validate` to resolve the change. The envelope constrains the product impact declared in `proposal.md`, which names only `README.md`.

## Migration Plan

None required. The change inserts a block into an existing file and alters no other behavior; deleting the banner block fully reverts it to the single title line.

## Open Questions

- Whether the banner should gain a recovery status badge or per-work-package progress lines once several changes are in flight. Deferred: that decision depends on repository content this work package does not cover, and it does not affect the specs, the approach, or the task breakdown here.
