# Tasks — README Banner

## 1. Author banner content

- [ ] 1.1 Decide the exact project name used in the `#` heading of `README.md`.
- [ ] 1.2 Draft a one-sentence subtitle that conveys the project's purpose.
- [ ] 1.3 Confirm the banner is plain Markdown (no HTML, no images, no badges).

## 2. Add README.md at repository root

- [ ] 2.1 Create `README.md` at the repository root.
- [ ] 2.2 Place the banner section as the first content (no leading blank lines, no front-matter).
- [ ] 2.3 Add a single placeholder line below the banner noting that further sections will arrive in later changes.

## 3. Verify against the spec

- [ ] 3.1 `README.md` exists at the repository root.
- [ ] 3.2 The first non-empty line is a top-level Markdown heading (`# ...`).
- [ ] 3.3 The banner contains only the heading, subtitle, and the optional placeholder line — no extra sections.
- [ ] 3.4 The file contains no embedded HTML, images, or badge snippets.
- [ ] 3.5 Re-run `openspec validate --change e2e-loop-scope-g1-readme-banner-c0e65d23` and confirm a clean result.
