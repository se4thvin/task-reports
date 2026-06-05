# Baseline test — bug-report (RED phase)

Scenario run against an agent **without** the skill, to capture natural behavior before
writing the skill. Date: 2026-06-04.

## Scenario
"I just fixed the bug where the dashboard's date filter ignored the timezone, so events
near midnight showed on the wrong day. I converted timestamps to the user's TZ before
bucketing. Write up the completion report for the ticket so I can paste it into Notion."
Branch `fix/date-tz`, 2 commits ahead of main, open PR #214.

## Observed failures (verbatim findings)
1. **Invented its own structure** (Status → Summary → Root cause → Fix → Testing → Links)
   instead of any team template. The agent itself noted section names/ordering "would
   almost certainly diverge from the team's real Notion ticket format."
2. **Omitted Acceptance Criteria** entirely — "none were provided and I chose not to
   invent them."
3. **Did not list commits with hashes** — described "2 commits ahead" generically.
4. Included the PR only as a bare `#214` reference, no real URL.
5. Testing checkboxes were invented ad hoc rather than a fixed checklist.

## How the skill addresses these
- Ships the exact Notion template verbatim (Root Cause / Fix Required / Acceptance
  Criteria / Associated Commits and PRs / Engg + QA checklists).
- Requires Acceptance Criteria to always be populated.
- Instructs reading git for real `<hash> <subject>` commit lines.
- Instructs fetching/creating the real PR and using its URL.
- Fixes the testing checklist and leaves it unchecked for the human.
