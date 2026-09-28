# Proposal

## Why

`README.md` today opens with a title and a one-line description, then jumps
straight to a placeholder line promising that Installation and Usage sections
will arrive in later changes. A reader landing on the repository therefore
cannot tell what kind of project this is — a demo harness rather than a
consumable package — and has no signal about how much of the README is meant to
be present. The document needs a fixed banner section that states the project's
nature and sets that expectation up front.

## What Changes

- Add a standard banner section to `README.md`, positioned directly below the
  title and above the description prose.
- Define what the banner must carry: a status label naming the project as a
  demonstration harness, and a one-sentence statement of what the repository is
  for.
- Keep the existing description paragraph intact below the banner so the
  project description stays in one place.
- Documentation only. No runtime code, build pipeline, dependency, or harness
  configuration changes.

## Capabilities

### New Capabilities

- `readme-banner`: Describes the banner section that `README.md` must carry at
  the top of the document, the parts it is required to contain, and the
  scenarios a reader can rely on when opening or updating the file.

### Modified Capabilities

None. `project-notes` exists as a separate in-flight capability and is
unchanged by this work; `readme-banner` is the first capability in this
repository to describe `README.md` itself.

## Impact

- `README.md` (modified): the only file this change is permitted to touch; it
  gains the banner section while keeping its existing description paragraph.
- Documentation only. No APIs, dependencies, build, or runtime systems are
  affected.
