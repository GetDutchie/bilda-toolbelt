---
name: hand-off
description: Generates a paste-ready session summary (current state, blockers, next steps) for handing off to a teammate, another Bilda instance, or a Slack thread. Different from /memorialize, which writes a structured file for Bilda's own memory. Trigger on phrases like "hand this off", "wrap up the session", "write a handoff", or "/hand-off".
---

# Hand-off

Generate a concise session summary the user can paste into Slack, Linear, or a Bilda chat in another instance.

> **Not the same as `memorialize`** — that skill writes a memory file to disk at `.claude/memories/` for Bilda's future self. This skill produces paste-ready output for *another human or tool*, not for Bilda.

## Steps

1. Gather context:
   - Current branch: `git branch --show-current`
   - Recent commits: `git log --oneline -10`
   - Uncommitted work: `git status --short`
   - Any open TODOs visible in recent conversation

2. Produce the following markdown block (no extra preamble — output starts at the heading):

```markdown
## Hand-off: <branch or topic>

**What's done**
- <bullet: completed work this session>

**Current state**
<one sentence: where things stand right now>

**Blockers / unknowns**
- <bullet, or "None">

**Next steps**
1. <concrete next action>
2. <follow-on>

**To pick this up**
```bash
git checkout <branch>
# <any setup command needed>
```
```

## Rules

- Keep each section tight. Bullets over paragraphs.
- "What's done" = only work from this session, not ancient history.
- "Next steps" = ordered. First item should be doable in under 30 minutes.
- "To pick this up" = the literal commands someone needs to resume, no explanation.
- If there's nothing done yet (empty session), say so rather than inventing content.
