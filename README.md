# bilda-toolbelt

Your personal Bilda plugin marketplace. Skills, agents, commands, and hooks that travel with you across every VAPE instance.

## What this is

Bilda (the AI assistant inside VAPE) can load custom capabilities from a GitHub repo you own. This template gives you a working starting point — one skill installed out of the box, scaffolding for the rest, and instructions throughout.

## Quick start

**1. Create your fork**

Click **Use this template → Create a new repository** (or go to `https://github.com/GetDutchie/bilda-toolbelt/generate`). Name it whatever you want — `my-bilda-toolbelt`, `<yourname>-bilda`, anything.

**2. Open VAPE Settings → Claude Plugins**

Add two entries:

| Field | Value |
|-------|-------|
| Marketplaces | `<your-github-username>/<your-repo-name>` |
| Plugins | `toolbelt@bilda-toolbelt` |

**3. Restart your VAPE instance**

Bilda clones your repo on boot. Ask it `what's in my toolbelt?` to confirm the intro skill loaded.

## Learn more

Full guide with screenshots, copy-paste skill templates, and advanced tips:
**[vape-pages.dutchie.dev/bilda-toolbelt](https://vape-pages.dutchie.dev/bilda-toolbelt/)** (password: dutchie)

## Structure

```
plugins/toolbelt/
├── .claude-plugin/plugin.json   ← bump version after every change
├── skills/intro/SKILL.md        ← starter skill (delete when ready)
├── agents/README.md             ← drop custom agents here
├── commands/README.md           ← drop slash commands here
└── hooks/README.md              ← wire event hooks here
```

## Editing tips

- Push → restart — VAPE does `git pull` on your marketplace repo every boot, so changes land automatically on the next instance start.
- Private repos work as long as your `GITHUB_TOKEN` has `repo` scope.
- You can add multiple marketplaces in VAPE Settings.
