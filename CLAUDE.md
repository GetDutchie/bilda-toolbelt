# bilda-toolbelt

Personal Bilda plugin marketplace. Skills/agents/commands/hooks that load on every VAPE instance boot.

## Rules

- New skills: `plugins/toolbelt/skills/<name>/SKILL.md` with `name` + `description` frontmatter.
- New agents: `plugins/toolbelt/agents/<name>.md`.
- New commands: `plugins/toolbelt/commands/<name>.md`.
- Hooks wired in `plugins/toolbelt/hooks/hooks.json`.
- After pushing, tell user to restart their VAPE instance. VAPE does `git pull` on the marketplace repo every boot — no version bumps needed.

## Install strings (for VAPE Settings)

- Marketplace: `<your-github-username>/<this-repo-name>`
- Plugin: `toolbelt@bilda-toolbelt`

## Reference

- Full guide: https://vape-pages.dutchie.dev/bilda-toolbelt/
- Canonical marketplace: https://github.com/GetDutchie/claude-marketplace
