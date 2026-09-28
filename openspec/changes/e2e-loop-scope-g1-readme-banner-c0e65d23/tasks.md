# Tasks

## 1. Banner

- [x] 1.1 Draft the banner text so it names the e2e-loop demonstration purpose and the
  `orca-companion` agent harness in its own words.
- [x] 1.2 Include an explicit statement that the repository offers no stability,
  compatibility, or support guarantees.
- [x] 1.3 Express the banner with plain Markdown only, so it reads the same on GitHub and
  in a plain-text read; use no badge, image, colour, or HTML.

## 2. Placement

- [x] 2.1 Insert the banner in `README.md` immediately after the level-1 title and before
  the existing prose description.
- [x] 2.2 Confirm the file still has exactly one level-1 title and exactly one banner.
- [x] 2.3 Remove the trailing placeholder sentence about Installation, Usage, and other
  sections being added in later changes.
- [x] 2.4 Leave the existing title and prose description otherwise unchanged.

## 3. Verification

- [x] 3.1 Run `grep -n 'no stability' README.md` and confirm the banner line is found
  below the title line reported by `grep -n '^# ' README.md`.
- [x] 3.2 Run `grep -c 'orca-companion' README.md`-style count checks and confirm the
  banner statement appears exactly once.
- [x] 3.3 Run `grep -n 'will be added in later changes' README.md` and confirm it matches
  no lines, so the deferred-sections placeholder is gone.
- [x] 3.4 Confirm `git status --porcelain` lists no modified path outside `README.md`.
