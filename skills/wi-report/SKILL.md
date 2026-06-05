---
name: wi-report
description: Use when the user explicitly invokes /wi-report or asks to generate a WI (Work Item) report / completion summary for a feature or task built in this session. Produces the filled WI Report template (acceptance criteria, commits, PR), auto-filling from the actual work and creating a PR if one is missing. Never auto-invoke - only run when explicitly requested.
---

# WI Report

Generate the team's WI (Work Item) completion writeup for a feature or task built in this session, auto-filled from the real work, and output it as one copy-pasteable block.

## When to use
- The user invokes `/wi-report` or asks for a WI report / completion writeup for a work item.
- **Never auto-invoke.** Only run when explicitly asked.

## Steps
1. **Identify the work.** Determine the feature/task from this session. If you genuinely can't tell what to report, ask before continuing — do not guess.
2. **Find the repo.** Locate the git repo for the changed project (it may not be the cwd). If there is no repo, leave commit/PR fields as `[FILL OUT]` and say so.
3. **Collect commits.** `git log <base>..HEAD --oneline` (or the commits made this session). Record each as `<short-hash> <subject>`. Read git — do not describe commits from memory.
4. **PR — create it if missing.**
   - Check existing: `gh pr list --head "$(git branch --show-current)" --json number,title,url`.
   - If none exists: commit any pending work, push the branch, then `gh pr create` (fill title/body from the work). **Actually create it — do not merely offer to.** Then report what you did and the resulting URL.
   - If you cannot push or create (no remote, no `gh`, auth fails), leave `[FILL OUT]` and state the blocker. Don't silently skip.
5. **Fill the template** below:
   - **Acceptance Criteria** — concrete, checkable conditions proving the work item is done, one per `- [ ]`. Always populate this; it is the field agents most often skip.
   - **PR(s) / Commit(s)** — real URLs and hashes from steps 3–4.
   - Only leave `[FILL OUT]` where you truly don't know. **Never invent** criteria or links.
6. **Leave testing unchecked.** All Engg/QA checkboxes stay unchecked and QA fields stay blank — testing hasn't happened yet. The `[ignore this]` marker means "don't populate this section"; do not print the marker in the output.
7. **Output** the filled report as a single markdown block the user can paste into Notion.

## Template (skeleton — fill it, don't emit verbatim)
```
WI Report

Acceptance Criteria

- [ ]  [FILL OUT]

Associated Commits and PRs

- PR(s):
    - [FILL OUT]
- Commit(s):
    - [FILL OUT]

Engg Testing Checklist

- [ ]  Tested Locally (All Acceptance Criteria Met)
- [ ]  Tested in Dev (All Acceptance Criteria Met)

QA Testing Checklist (Aya)

- [ ]  Tested in Staging (All Acceptance Criteria Met)
    - Date & Time:
    - Notes:
- [ ]  Tested in Prod (All Acceptance Criteria Met)
    - Date & Time:
    - Notes:
```

## Common mistakes
- Inventing your own report structure instead of using this exact template → must match.
- Emitting the blank skeleton instead of filling it from the work → defeats the purpose.
- Skipping Acceptance Criteria → always populate it.
- Only offering to create the missing PR instead of creating it → create it.
- Inventing PR/commit links instead of reading git → links must be real.
- Checking testing boxes → those are for the human/QA to check later.
- Populating the QA (Aya) section → leave it blank.
