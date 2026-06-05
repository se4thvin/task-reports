# task-reports

Two Claude Code skills that generate your team's **completion writeups** for Notion — auto-filled from the work you just did, with real commits and PRs, ready to paste.

- **`/bug-report`** — Bug Report writeup (Root Cause, Fix Required, Acceptance Criteria, Commits & PRs, testing checklists).
- **`/wi-report`** — WI (Work Item) writeup (Acceptance Criteria, Commits & PRs, testing checklists).

Each skill reads git for the real commits, checks for an existing PR and **creates one if it's missing**, drafts acceptance criteria from the actual work, and leaves `[FILL OUT]` only where it genuinely doesn't know. Testing checkboxes are left unchecked and the QA section is left for QA.

## Install

```
/plugin marketplace add se4thvin/task-reports
/plugin install task-reports
```

## Usage

| Command | Use it when | Produces |
|---------|-------------|----------|
| `/bug-report` | You fixed a bug this session | Bug Report block with root cause + fix |
| `/wi-report` | You finished a feature / work item | WI Report block |

Both are **user-invoked only** — they never run automatically. Run the command after the work is done; the skill fills the template from the session and your git state, creating a PR if one doesn't exist yet.

## What gets filled vs left blank

- **Filled:** acceptance criteria, root cause & fix (bug report), commit hashes + subjects, PR link (existing or newly created).
- **Left as `[FILL OUT]`:** anything the skill genuinely can't determine — it never invents criteria, causes, or links.
- **Left unchecked / blank:** all Engg/QA testing checkboxes and the QA (Aya) section — those are filled in later by the people who test.

## License

MIT — see [LICENSE](LICENSE).
