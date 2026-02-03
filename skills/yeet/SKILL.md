---
name: "yeet"
description: "Use only when the user explicitly asks to stage, commit, push, and open a GitHub pull request in one flow using the GitHub CLI (`gh`)."
---

## Prerequisites

- Require GitHub CLI `gh`. Check `gh --version`. If missing, ask the user to install `gh` and stop.
- Require `jq`. Check `jq --version`. If missing, ask the user to install `jq` and stop.
- Require authenticated `gh` session. Run `gh auth status`. If not authenticated, ask the user to run `gh auth login` (and re-run `gh auth status`) before continuing.

## Naming conventions

- Branch: `codex/{description}` when starting from main/master/default.
- Commit: `{description}` (terse).
- PR title: `[codex] {description}` summarizing the full diff.

## Workflow

- If on main/master/default, create a branch: `git checkout -b "codex/{description}"`
- Otherwise stay on the current branch.
- Confirm status, then stage everything: `git status -sb` then `git add -A`.
- Commit tersely with the description: `git commit -m "{description}"`
- Fetch latest PR review summary, latest inline review comment (with `diff_hunk`), and latest issue comments using:
  - `gh api repos/:owner/:repo/pulls/$(gh pr view --json number --jq .number)/reviews --jq 'sort_by(.submitted_at) | last | {user:.user.login, state, body, submitted_at}'`
  - `gh api repos/:owner/:repo/pulls/$(gh pr view --json number --jq .number)/comments --jq 'sort_by(.created_at) | last | {user:.user.login, path, line, body, created_at, diff_hunk}'`
  - `gh api repos/:owner/:repo/issues/$(gh pr view --json number --jq .number)/comments --jq 'sort_by(.created_at) | reverse | .[] | {user:.user.login, body, created_at}'`
- Run checks if not already. If checks fail due to missing deps/tools, install dependencies and rerun once.
- Push with tracking: `git push -u origin $(git branch --show-current)`
- If git push fails due to workflow auth errors, pull from master and retry the push.
- Open a PR and edit title/body to reflect the description and the deltas: `GH_PROMPT_DISABLED=1 GIT_TERMINAL_PROMPT=0 gh pr create --draft --fill --head $(git branch --show-current)`
- Write the PR description to a temp file with real newlines (e.g. pr-body.md ... EOF) and run pr-body.md to avoid \\n-escaped markdown.
- PR description (markdown) must be detailed prose covering the issue, the cause and effect on users, the root cause, the fix, and any tests or checks used to validate.
