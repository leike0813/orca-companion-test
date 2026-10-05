# Proposal

## Why

The repository landing page currently contains nothing but a bare project title, so a
first-time reader has no signal about what the project is, how mature it is, or where to
start. A short, fixed banner at the top of the README gives every visitor that orientation
without turning the landing page into documentation.

## What Changes

- Add a banner block at the very top of `README.md`, above the existing project title.
- The banner states the project name, a one-line purpose, and a lifecycle/status marker.
- The banner is a stable, machine-checkable structure: a fixed heading, a fixed status line,
  and no free-form prose drifting outside the section.
- The existing `# ip05-cc-06` title is preserved and continues to follow the banner.

## Capabilities

### New Capabilities

- `readme-banner`: The project landing page must open with a banner that names the project,
  summarises its purpose, and declares its lifecycle status in a stable, verifiable layout.

### Modified Capabilities

None. The project has no existing capability specs, and no existing spec-level behaviour is
altered by this change.

## Impact

- `README.md`: a banner section is inserted above the existing project title; no other file
  in the repository changes behaviour, and no dependency, API, or runtime surface is added.

