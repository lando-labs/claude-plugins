# Lando Labs Plugin Marketplace

This is the **marketplace registry** for Lando Labs Claude Code plugins. It contains only the `marketplace.json` that points to plugin repos.

## Structure

```
claude-plugins/              ← This repo (marketplace)
├── .claude-plugin/
│   └── marketplace.json     ← Registry of all plugins
├── cami-plugin/             ← Separate repo (gitignored)
└── vibecoding-sprint/       ← Separate repo (gitignored)
```

**Important**: Plugin subdirectories are separate git repos, gitignored by this marketplace repo. They just live here for convenient local development.

## Plugins in This Marketplace

| Plugin | Purpose |
|--------|---------|
| **cami** | Agent management - scout, architect, deploy |
| **vibecoding-sprint** | Sprint planning with GitHub + semver |
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
2. If developing locally, clone/create the plugin repo as a subdirectory
3. Add the directory name to `.gitignore`

**To test locally**:
```bash
claude --plugin-dir ./cami-plugin
```

## Agents

### plugin-architect
Located in `cami-plugin/agents/plugin-architect.md`. Use proactively when building plugins, creating plugin.json or marketplace.json, writing SKILL.md files, or structuring plugin directories.

### agent-architect
Located in `cami-plugin/agents/agent-architect.md`. Use proactively when creating or refining Claude Code agents, designing agent system prompts, or architecting multi-agent systems.

## References

- [Plugin Marketplace Docs](https://code.claude.com/docs/en/plugin-marketplaces)
- [Plugin Creation Docs](https://code.claude.com/docs/en/plugins)
