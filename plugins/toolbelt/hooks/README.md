# Hooks

Wire event-driven shell scripts via `hooks.json` in this directory.

## hooks.json shape

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "${CLAUDE_PLUGIN_ROOT}/hooks/my-hook.sh",
            "description": "What this hook does"
          }
        ]
      }
    ]
  }
}
```

## Supported events

- `PreToolUse` — runs before a tool call (can block it)
- `PostToolUse` — runs after a tool call completes
- `Stop` — runs when Bilda finishes a turn
- `Notification` — runs on system notifications

## Matchers

Match on tool name: `Bash`, `Edit`, `Write`, `Read`, `Glob`, `Grep`, `Agent`, etc. Use `"*"` to match all tools.

## Example: log every bash command

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "${CLAUDE_PLUGIN_ROOT}/hooks/log-bash.sh",
            "description": "Append bash commands to ~/bash-audit.log"
          }
        ]
      }
    ]
  }
}
```

`hooks/log-bash.sh`:
```bash
#!/bin/bash
echo "$(date -u +%Y-%m-%dT%H:%M:%SZ) $CLAUDE_TOOL_INPUT" >> ~/bash-audit.log
```

## Reference

- Canonical examples: [GetDutchie/claude-marketplace/plugins/zsh-rocket/hooks/](https://github.com/GetDutchie/claude-marketplace/tree/main/plugins/zsh-rocket/hooks)
- Agent Skills spec: https://agentskills.io/specification

After adding, push to your repo and restart your VAPE instance. VAPE pulls the latest on every boot.
