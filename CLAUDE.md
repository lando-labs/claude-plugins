# Lando Labs Plugin Marketplace

This is the **marketplace registry** for Lando Labs Claude Code plugins. It contains only the `marketplace.json` that points to plugin repos.

## Structure

```
claude-plugins/                  ← Parent directory (not a git repo)
├── marketplace/                 ← This repo (marketplace registry)
│   ├── .claude-plugin/
│   │   └── marketplace.json     ← Registry of all plugins
│   └── CLAUDE.md
├── cami-plugin/                 ← Separate git repo
├── vibecoding-sprint/           ← Separate git repo
└── research-plugin/             ← Separate git repo
```

**Important**: Plugin directories are sibling git repos to this marketplace. Each plugin is independent.

## Plugins in This Marketplace

| Plugin | Purpose |
|--------|---------|
| **cami** | Agent management - scout, architect, deploy |
| **vibecoding-sprint** | Sprint planning with GitHub + semver |
| **research-plugin** | Multi-source research synthesis |
| **fullstack-guild** | MERN stack agents (external repo) |
| **game-dev-guild** | Phaser 3 agents (external repo) |
| **content-guild** | Writing/marketing agents (external repo) |

## Working With This Repo

**This repo tracks only**:
- `.claude-plugin/marketplace.json`
- `.gitignore`
- `CLAUDE.md`

**To add a new plugin**:
1. Add entry to `marketplace.json`
2. Create the plugin repo as a sibling directory (not nested)

**To test a plugin locally**:
```bash
claude --plugin-dir ../cami-plugin
```

## References

- [Plugin Marketplace Docs](https://code.claude.com/docs/en/plugin-marketplaces)
- [Plugin Creation Docs](https://code.claude.com/docs/en/plugins)
