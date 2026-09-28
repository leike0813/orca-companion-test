# Proposal

## Why

`README.md` describes this repository as an e2e-loop demonstration project, but that
signal is currently a single sentence buried in the middle of the file, below the
title. A reader skimming the first screen sees a project name and nothing about its
status, and the closing line explicitly defers every remaining section (Installation,
Usage, and others) to future changes. The practical consequence is that the repository
looks more finished than it is: nobody is told up front that it exists to exercise the
`orca-companion` agent harness rather than to be depended on.

## What Changes

- Add a status banner to `README.md`, placed directly beneath the top-level title, that
  states in the banner's own words that the repository is a demonstration of the agent
  harness and carries no stability or support guarantees.
- Keep the banner in a form that renders the same way on GitHub and on a plain-text
  `cat`, so the warning survives both readings of the file.
- Drop the closing placeholder sentence that defers all further sections to later
  changes, since the banner now states the project's scope and its absence is only
  noise.
- No behaviour, script, or configuration is modified; this change touches documentation
  only.

## Capabilities

### New Capabilities
- `readme-banner`: `README.md` carries a status banner immediately below its title that
  declares the repository's demonstration status and lack of guarantees.

### Modified Capabilities
<!-- None. -->

## Impact

- `README.md`: the only file added or changed by this change. It gains a status banner
  below the title and loses the trailing placeholder sentence about future sections.
