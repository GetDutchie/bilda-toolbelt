---
name: toolbelt-intro
description: Welcome to your personal Bilda toolbelt. Shows what's installed, how to add skills/agents/commands/hooks, and how to iterate on your customizations. Trigger on phrases like "what's in my toolbelt", "show my customizations", "toolbelt help", or "/toolbelt-intro".
---

# Welcome to Your Bilda Toolbelt

Your personal plugin marketplace is installed and working. This skill is proof.

## What You Have

Your toolbelt lives in the GitHub repo you created from the template. Bilda clones it fresh on every instance boot — so whatever you push is what you get.

```
plugins/toolbelt/
├── skills/      ← you are here
├── agents/      ← custom sub-agents (personas, specialists)
├── commands/    ← slash commands (/your-command)
└── hooks/       ← event hooks (PreToolUse, PostToolUse, Stop, etc.)
```

The `marketplace.json` at the root tells Bilda where to find everything. The `plugin.json` inside `plugins/toolbelt/` is the version stamp — bump it every time you push changes.

## Adding a Skill

1. Create `plugins/toolbelt/skills/<name>/SKILL.md`
2. Add frontmatter — minimum required:

```markdown
---
name: my-skill
description: One sentence that tells Bilda when to use this. Be specific about trigger phrases.
---

# Skill Title

Skill body: instructions, context, commands, whatever Bilda needs.
```

3. Push to your repo
4. Restart your VAPE instance — Bilda pulls the latest on every boot

## Going Further

**Agents** — custom sub-agents with their own persona, model, and instructions. Drop `<name>.md` in `plugins/toolbelt/agents/`. See `agents/README.md` for the frontmatter shape.

**Commands** — slash commands that appear in Bilda's command palette. Drop `<name>.md` in `plugins/toolbelt/commands/`. See `commands/README.md`.

**Hooks** — event-driven shell scripts that run before/after tool use or on session stop. Wire them in `hooks/hooks.json`. See `hooks/README.md`.

**MCP servers** — add to your `CLAUDE.md` or wire via hooks. The `claude-marketplace` repo has working examples.

Full reference: [bilda-toolbelt guide](https://vape-pages.dutchie.dev/bilda-toolbelt/) · [GetDutchie/claude-marketplace](https://github.com/GetDutchie/claude-marketplace)

## Tips

- Push → restart — VAPE does `git pull` on your marketplace repo every boot. No version bumps needed.
- Private repos work — as long as your `GITHUB_TOKEN` has `repo` scope.
- Multiple marketplaces — add more `owner/repo` entries in VAPE Settings.

## When You're Ready

Delete this skill once you've built your own. It's a scaffold, not a fixture.

```bash
rm -rf plugins/toolbelt/skills/intro
```

Bump the version, push, restart. Clean slate.
