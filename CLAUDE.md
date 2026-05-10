# bilda-toolbelt

Personal Bilda plugin marketplace. Skills/agents/commands/hooks that load on every VAPE instance boot.

## Rules

- New skills: `plugins/toolbelt/skills/<name>/SKILL.md` with `name` + `description` frontmatter.
- New agents: `plugins/toolbelt/agents/<name>.md`.
- New commands: `plugins/toolbelt/commands/<name>.md`.
- Hooks wired in `plugins/toolbelt/hooks/hooks.json`.
- After pushing, tell user to restart their VAPE instance. VAPE `git pull`s the marketplace on every boot (vape `cmd/vape-machine/bootstrap.go:605-607`) — no version bumps needed.
- **Don't change the marketplace `name` field** in `.claude-plugin/marketplace.json`. The install string `toolbelt@bilda-toolbelt` resolves against that field, not the repo name. Stable name = forks keep working.

## Install strings (for VAPE Settings)

- Marketplace: `GetDutchie/<this-repo-name>` (template prefills owner=GetDutchie)
- Plugin: `toolbelt@bilda-toolbelt`

## Branches

- `main` — template content. Forked by users.
- `assets` — orphan branch hosting PR screenshots (raw.githubusercontent.com URL). Don't merge.

## Reference

- Full guide: https://vape-pages.dutchie.dev/bilda-toolbelt/
- Canonical marketplace: https://github.com/GetDutchie/claude-marketplace
