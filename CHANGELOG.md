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
- Marketplace `name` (`se4thvin-plugins`) is intentionally different from the plugin
  `name` (`task-reports`) to avoid a Claude Code install-classification bug.
- `marketplace.json` `source` uses the `{ source: "url", url, sha }` form pinned to a
  release commit SHA; bump the SHA on every release.
