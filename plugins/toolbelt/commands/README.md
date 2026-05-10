# Commands

Drop `<name>.md` here to add a slash command that appears in Bilda's command palette.

## Frontmatter shape

```markdown
---
name: my-command
description: What this command does — shown in the palette.
---

Command body: instructions Bilda follows when the command is invoked.
```

## Example

```markdown
---
name: standup
description: Generate a standup update from git log and open PRs
---

Run `git log --since=yesterday --oneline` and `gh pr list --author @me`.
Summarize into three bullets: what I did yesterday, what I'm doing today, any blockers.
Keep it under 100 words.
```

Invoke with `/standup` in Bilda chat.

## Reference

- Canonical examples: [GetDutchie/claude-marketplace/plugins/context-management/commands/](https://github.com/GetDutchie/claude-marketplace/tree/main/plugins/context-management/commands)
- Agent Skills spec: https://agentskills.io/specification

After adding, bump `../.claude-plugin/plugin.json` version and restart your VAPE instance.
