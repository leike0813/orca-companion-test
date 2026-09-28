# Tasks

## 1. Add The Banner

- [x] 1.1 Insert a single `>`-prefixed line in `README.md` as the first content after the `# orca-companion` heading, separated from it by a blank line, stating that the project is an e2e demonstration and is not ready for production use.
- [x] 1.2 Leave the existing descriptive paragraph and the italic placeholder line unchanged below the banner.

## 2. Verify

- [x] 2.1 Run `head -3 README.md` and confirm the second line is blank and the third is the single `>`-prefixed banner, proving the banner is the first content after the title.
- [x] 2.2 Re-read `README.md` and confirm it satisfies every requirement in the `readme-banner` delta spec: banner is the first content after the title, is a single blockquote line, and states both demonstration status and production non-readiness.
- [x] 2.3 Run `openspec validate e2e-loop-scope-g1-readme-banner-c0e65d23 --strict` and confirm it reports no errors.
