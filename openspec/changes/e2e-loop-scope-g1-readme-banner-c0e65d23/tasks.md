# Tasks

## 1. Rewrite the README banner

- [ ] 1.1 Replace the introductory block of `README.md` so the file begins with an H1 title `orca-companion`, followed by a non-empty tagline paragraph, followed by an italic status banner line; verify by inspection that no `## H2` heading appears before all three constructs. [verification: `head -n 20 README.md` shows the H1 title as the first non-blank line, the tagline paragraph immediately below it, and an italic line immediately below the paragraph, with no `##` heading above them]
- [ ] 1.2 Remove the legacy italic placeholder copy `_More sections (Installation, Usage, etc.) will be added in later changes._` and re-express the same forward-looking intent as a status banner line owned by the new `readme-banner` capability; verify the file no longer contains the literal legacy sentence. [verification: `grep -F 'More sections (Installation, Usage, etc.)' README.md` exits non-zero]
- [ ] 1.3 Ensure the banner block is plain UTF-8 CommonMark Markdown with no scripts, image embeds, or badge URLs and verify by file inspection. [verification: `file README.md` reports ASCII or UTF-8 text and `grep -E '<script|!\[|https://img.shields.io' README.md` exits non-zero]

## 2. Stage and validate the change

- [ ] 2.1 `git add README.md` and verify `git status` shows `README.md` staged for commit at the repository root. [verification: `git diff --cached --name-only` prints exactly `README.md`]
- [ ] 2.2 Run `openspec validate e2e-loop-scope-g1-readme-banner-c0e65d23 --strict` from the repository root and verify it exits 0 with no findings. [verification: the command exits 0 and prints `Valid: ...` (or equivalent) without listing any failing checks]
- [ ] 2.3 Confirm the change's `## Impact` section in `proposal.md` mentions only paths inside the Work Package Scope Envelope and verify by inspection. [verification: `awk '/^## Impact/{flag=1; next} /^## /{flag=0} flag && /^- /' proposal.md` lists only `README.md`]
