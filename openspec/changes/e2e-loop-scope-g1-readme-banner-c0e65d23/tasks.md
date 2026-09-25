# Tasks

## 1. Draft the banner copy

- [ ] 1.1 Draft three short banner lines covering: (a) the project is a demo, (b) the orca-companion agent harness is the driver, (c) more sections (Installation, Usage, etc.) will arrive in later changes
- [ ] 1.2 Confirm the existing forward-looking italic note is restated inside the banner rather than kept as a separate line beneath the description

## 2. Edit README.md

- [ ] 2.1 Insert the banner block immediately under the H1 title (`# orca-companion`), formatted as a Markdown blockquote (`>` prefix)
- [ ] 2.2 Leave the existing one-line project description paragraph (`An e2e-loop demonstration project ...`) in place below the banner
- [ ] 2.3 Remove or rewrite the trailing italic forward-looking note so that the banner is the single source of "what to expect next"
- [ ] 2.4 Keep the diff scoped to `README.md` only — do not touch `orca-companion.json`, `.gitignore`, or any other file

## 3. Validate the resulting README

- [ ] 3.1 Render the file mentally and confirm the banner is the first thing a visitor reads after the H1 title
- [ ] 3.2 Verify the file has exactly one H1, the banner blockquote, and the existing description paragraph — no extra sections, no broken Markdown
- [ ] 3.3 Verify no trailing whitespace, no inline images, no fenced code blocks, no HTML, and no external links were introduced by the banner
