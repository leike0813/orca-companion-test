# Tasks

## 1. Add the banner to the README

- [x] 1.1 Insert a banner section into `README.md` directly below the `#` title
  and above the existing description paragraph, containing a plain-text status
  statement that names the repository as a demonstration harness and one
  sentence stating what it is for. Verify with `head -12 README.md` that the
  banner appears between the title and the description paragraph, and that the
  original description paragraph is still present below it.
- [x] 1.2 State in the banner that the remaining README sections are still to be
  added, so a reader scanning for installation or usage guidance knows the
  absence is expected. Verify with `head -12 README.md` that the banner names
  the sections as forthcoming.
- [x] 1.3 Confirm the banner uses plain Markdown text with no remote image or
  badge reference. Verify with `grep -nE '!\[|img\.shields\.io|<img' README.md`
  that no image or badge markup is present.
- [x] 1.4 Confirm the document has exactly one banner. Verify with
  `grep -c '^> \*\*Status:\*\*' README.md` that the banner marker appears once
  and no duplicate banner was introduced.

## 2. Verify the change against its scope

- [x] 2.1 Run `openspec validate e2e-loop-scope-g1-readme-banner-c0e65d23 --strict`
  and confirm it reports the change as valid. Verify by the command exiting with
  a success message.
- [x] 2.2 Confirm the change touched no file outside the scope envelope. Verify
  with `git status --porcelain` that `README.md` is the only modified tracked
  file.
