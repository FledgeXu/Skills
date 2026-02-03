---
name: "pr-review-update"
description: "Use only when updating code based on PR reviews."
---

## Prerequisites

- Require GitHub CLI `gh`. Check `gh --version`. If missing, ask the user to install `gh` and stop.
- Require `jq`. Check `jq --version`. If missing, ask the user to install `jq` and stop.
- Require authenticated `gh` session. Run `gh auth status`. If not authenticated, ask the user to run `gh auth login` (and re-run `gh auth status`) before continuing.

## Workflow

- Fetch latest PR review summary, latest inline review comment (with `diff_hunk`), and latest issue comments using:
  - `gh api repos/:owner/:repo/pulls/$(gh pr view --json number --jq .number)/reviews --jq 'sort_by(.submitted_at) | last | {user:.user.login, state, body, submitted_at}'`
  - `gh api repos/:owner/:repo/pulls/$(gh pr view --json number --jq .number)/comments --jq 'sort_by(.created_at) | last | {user:.user.login, path, line, body, created_at, diff_hunk}'`
  - `gh api repos/:owner/:repo/issues/$(gh pr view --json number --jq .number)/comments --jq 'sort_by(.created_at) | reverse | .[] | {user:.user.login, body, created_at}'`
- **Apply code changes** to address the review feedback and comments, keeping the PR scope focused.
- Resolve all completed review comments on the PR. Example CLI flow:
  - `OWNER=$(gh repo view --json owner --jq .owner.login)`
  - `REPO=$(gh repo view --json name --jq .name)`
  - `NUMBER=$(gh pr view --json number --jq .number)`
  - `gh api graphql -f query='query($owner:String!,$repo:String!,$number:Int!){repository(owner:$owner,name:$repo){pullRequest(number:$number){reviewThreads(first:100){nodes{id isResolved}}}}}' -f owner=$OWNER -f repo=$REPO -F number=$NUMBER --jq '.data.repository.pullRequest.reviewThreads.nodes[] | select(.isResolved==false) | .id' | xargs -I{} gh api graphql -f query='mutation($threadId:ID!){resolveReviewThread(input:{threadId:$threadId}){thread{id isResolved}}}' -f threadId={}`
- Confirm status, then stage everything: `git status -sb` then `git add -A`.
- Commit tersely with the description: `git commit -m "{description}"`
- Run checks if not already. If checks fail due to missing deps/tools, install dependencies and rerun once.
- Push with tracking: `git push -u origin $(git branch --show-current)`
- If git push fails due to workflow auth errors, pull from master and retry the push.
- Add a PR comment summarizing the changes made in response to reviews:
  - `gh pr comment --body "{address review feedback and update implementation details.}"`
