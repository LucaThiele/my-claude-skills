---
name: anthropic-commit-push-pr
description: Commit all changes, push to remote, and open a pull request in one step
allowed-tools: Bash
---

Commit all staged and unstaged changes, push to the remote, and open a pull request.

## Steps

1. Run `git status` and `git diff` to understand what has changed.
2. Stage changes for relevant files (avoid blanket `git add -A` if there are untracked files that look like secrets or build artifacts).
3. Write a clear commit message that explains *why* the change was made, not just what. Use a HEREDOC to pass it to `git commit -m`.
4. Push the branch to the remote with `git push -u origin HEAD`.
5. Create a PR with `gh pr create`. Use a HEREDOC for the body. Include:
   - A short title (under 70 characters)
   - A `## Summary` section with 1-3 bullet points
   - A `## Test plan` section with a short checklist
   - The footer: `🤖 Generated with [Claude Code](https://claude.com/claude-code)`
6. Print the PR URL clearly so it's easy to copy.
7. If a Slack MCP server is configured and a channel is specified in CLAUDE.md, post the PR URL to that channel.

## Rules

- Never use `--no-verify` to skip hooks.
- Never force-push unless the user explicitly asked.
- If the push fails because the branch is behind, stop and tell the user — do not auto-rebase.
- If `gh` is not installed or not authenticated, stop and tell the user what to run.
