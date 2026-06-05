# Baseline test — wi-report (RED phase)

Scenario run against an agent **without** the skill, to capture natural behavior before
writing the skill. Date: 2026-06-04.

## Scenario
"I finished the work item: added CSV export to the reports page. Write up the completion
report for the ticket so I can paste it into Notion."
Branch `feat/csv-export`, 3 commits, **no PR exists yet**.

## Observed failures (verbatim findings)
1. **Invented its own structure** (Status → Summary → What changed → Testing → Links) —
   self-described as "my own convention, not a known template."
2. **Omitted Acceptance Criteria** — "not provided, didn't invent."
3. **Did not list commits with hashes** — described "3 commits" generically.
4. **Did not create the missing PR.** It only *offered* to open one and asked for
   confirmation — "a teammate who wanted a one-shot write-it-up-and-open-the-PR would
   need a second round-trip."
5. Ad-hoc divergence between bug vs. feature handling, decided per-run on instinct.

## How the skill addresses these
- Ships the exact Notion WI template verbatim.
- Requires Acceptance Criteria to always be populated.
- Instructs reading git for real `<hash> <subject>` commit lines.
- **Instructs actually creating the PR when missing ("do not merely offer to"),** since
  the user opted into auto-creation — closing the round-trip the baseline exposed.
- Separate bug-report vs wi-report skills normalize the bug/feature divergence.
