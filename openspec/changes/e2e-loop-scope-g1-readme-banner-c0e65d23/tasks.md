# Tasks

## 1. Author README.md banner

- [ ] 1.1 Insert a Markdown blockquote banner as the first non-empty
      content of `README.md`, immediately above the existing
      `# orca-companion` title, and verify with
      `awk 'NF{print; exit}' README.md | grep -E '^>[[:space:]]'` that
      the first non-empty line begins with `>` followed by content.
- [ ] 1.2 Add a Markdown link from the banner blockquote whose link
      target is the relative string `NOTES.md`, and verify with
      `grep -E '^>[[:space:]]*.*\]\(NOTES\.md\)' README.md` that the
      link is present on a blockquote line.
- [ ] 1.3 Confirm the prose inside the banner is not a byte-for-byte
      copy of any prose block already present in `NOTES.md`, and verify
      by extracting the banner prose and confirming `diff` reports
      differences against every paragraph-level block in `NOTES.md`.

## 2. Verify the change against its spec

- [ ] 2.1 Run
      `openspec validate e2e-loop-scope-g1-readme-banner-c0e65d23
      --strict --json` and verify the response reports zero validation
      errors for the `readme-banner` capability and zero violations of
      the Impact scope envelope.
- [ ] 2.2 Run
      `openspec status e2e-loop-scope-g1-readme-banner-c0e65d23
      --json` and verify every required artifact (`proposal`, `specs`,
      `design`, `tasks`) is reported as `done`.
