---
name: pr-summary
description: Reads the current branch diff against the base branch and drafts a PR title and description. Trigger on phrases like "draft a PR description", "summarize my branch", "write a PR", or "/pr-summary".
---

# PR Summary

Draft a pull request title and description for the current branch.

## Steps

1. Identify the base branch:
   ```bash
   git remote show origin | grep 'HEAD branch' | awk '{print $NF}'
   ```
   Fall back to `main` if the above fails.

2. Get the diff summary:
   ```bash
   git log --oneline $(git merge-base HEAD origin/main)..HEAD
   git diff $(git merge-base HEAD origin/main)..HEAD --stat
   ```

3. Read the full diff for context:
   ```bash
   git diff $(git merge-base HEAD origin/main)..HEAD
   ```

4. Draft the PR using this structure:

```
## Title
<verb>: <what changed> [ticket if known]

## Summary
- <bullet: what it does>
- <bullet: why it matters>
- <bullet: any non-obvious tradeoff or constraint>

## Test plan
- [ ] <how to verify the golden path>
- [ ] <edge case to check>
```

## Rules

- Title prefix: `feat:` for new capability, `fix:` for bug fix, `eng:` for infra/tooling/refactor, `revert:` for rollbacks.
- Summary bullets: 2–4. No filler. No "this PR".
- Test plan: at least 2 checkboxes. Concrete steps, not vague "test the feature".
- If there's no diff (empty branch), say so and stop.
- If a ticket number is visible in branch name or commit messages, append it to the title.
