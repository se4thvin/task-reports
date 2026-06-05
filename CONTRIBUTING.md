# Contributing

## Adding or changing a skill

Skills follow a test-first (TDD) discipline — see `docs/development/tests/` for the
baseline tests that justify each skill's design.

To add a new skill to this plugin:

1. **Baseline test first.** Run the scenario against an agent *without* the skill and
   record how it fails in `docs/development/tests/baseline-<skill>.md`. No skill without
   a failing baseline first.
2. **Create `skills/<skill-name>/SKILL.md`** with two-field frontmatter (`name:` matching
   the directory name; `description:` in "Use when …" trigger style) and a Markdown body.
3. **(Optional) Add a command** at `commands/<command>.md` (`description` + optional
   `argument-hint` frontmatter; body invokes the skill via `$ARGUMENTS`).
4. **Bump `version`** in `.claude-plugin/plugin.json` and the matching plugin entry in
   `.claude-plugin/marketplace.json`.
5. **Update `marketplace.json` `source.sha`** to the new release commit SHA after pushing.
6. **Update `README.md` and `CHANGELOG.md`.**

## Release checklist

1. Commit changes.
2. Push to `main`, note the new commit SHA.
3. Set `source.sha` in `marketplace.json` to that SHA, bump versions, commit, push.
