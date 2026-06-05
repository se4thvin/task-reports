# Security

These skills generate text and run read-only git commands, plus optionally create a pull
request on your behalf (`gh pr create`) when one is missing for the current branch.

- The skills never push to or create PRs against a repo you didn't ask them to report on.
- They read git history and PR metadata via the `gh` CLI using your existing credentials.
- They do not transmit data anywhere other than the GitHub operations you authorize.

If you discover a security issue, please open an issue or contact the maintainer at
https://github.com/se4thvin.
