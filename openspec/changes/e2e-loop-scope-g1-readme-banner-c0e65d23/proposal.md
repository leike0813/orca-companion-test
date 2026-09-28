# Proposal

## Why

`README.md` currently opens with a title and a single descriptive paragraph, so a reader has no signal about how finished or stable the project is. Someone arriving from a link or a search result can easily mistake this demonstration repository for a released tool and follow the "more sections will be added later" line as a promise rather than a placeholder. A short status banner directly under the title states the project's stage up front, so expectations are set before anyone reads further.

## What Changes

- Add a status banner to `README.md` immediately below the `# orca-companion` heading.
- Require the banner to state that the project is a demonstration and not ready for production use.
- Keep the banner a single blockquote line so it stays visually distinct from the body prose that follows it.

## Capabilities

### New Capabilities

- `readme-banner`: Define the required status banner in `README.md`, including its position, form, and the statements it must make about the project's maturity.

### Modified Capabilities

None.

## Impact

- `README.md`: the only file this change creates or edits; it receives the status banner described by the requirements below.
