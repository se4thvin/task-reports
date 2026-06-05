# Changelog

All notable changes to this project are documented here. This project adheres to
[Semantic Versioning](https://semver.org/).

## [0.1.0] - 2026-06-04

### Added
- Initial release.
- `bug-report` skill + `/bug-report` command — generates the Bug Report completion
  writeup (Root Cause, Fix Required, Acceptance Criteria, Commits & PRs, Engg/QA
  testing checklists), auto-filled from the session's work and git state.
- `wi-report` skill + `/wi-report` command — generates the WI (Work Item) completion
  writeup (Acceptance Criteria, Commits & PRs, Engg/QA testing checklists).
- Both skills read git for real commits and create a PR if one is missing.
- Packaged as a Claude Code plugin + single-plugin marketplace.

### Notes
- Marketplace `name` (`se4thvin-task-reports`) is intentionally different from the plugin
  `name` (`task-reports`) AND unique across the author's other marketplace repos. Reusing
  another repo's marketplace name (e.g. `se4thvin-plugins` from context-handoff) overwrites
  that marketplace's registration in `known_marketplaces.json` and the plugin won't resolve.
- `marketplace.json` `source` uses the `{ source: "url", url, sha }` form pinned to a
  release commit SHA; bump the SHA on every release.
