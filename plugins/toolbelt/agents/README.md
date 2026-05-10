# Agents

Drop `<name>.md` here to add a custom sub-agent.

## Frontmatter shape

```markdown
---
name: my-agent
description: When to invoke this agent. Be specific — this is the routing signal.
model: sonnet   # optional: sonnet (default), opus, haiku
---

Agent system prompt goes here.
```

## Example

```markdown
---
name: debugger
description: Deep debugging specialist. Use when stack traces need tracing, flaky tests need isolation, or root cause is unclear. Trigger on "ask debugger" or "debug this".
model: opus
---

You are a systematic debugger. Always start with the stack trace, never guess...
```

## Reference

- Canonical examples: [GetDutchie/claude-marketplace/plugins/dutchie-developer/agents/](https://github.com/GetDutchie/claude-marketplace/tree/main/plugins/dutchie-developer/agents)
- Agent Skills spec: https://agentskills.io/specification

After adding, bump `../.claude-plugin/plugin.json` version and restart your VAPE instance.
