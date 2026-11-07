# daverainford-plugins

Personal Claude Code plugin marketplace.

## Use

```
/plugin marketplace add <github-user>/claude-plugins   # or a local path
/plugin install example-plugin@daverainford-plugins
```

## Layout

```
.claude-plugin/marketplace.json     # marketplace catalog; one entry per plugin
plugins/<name>/
  .claude-plugin/plugin.json        # plugin manifest
  skills/<skill>/SKILL.md           # optional
  commands/*.md                     # optional
  agents/*.md                       # optional
  hooks/hooks.json                  # optional
  .mcp.json                         # optional
```

## Add a plugin

1. Create `plugins/<name>/` with a `.claude-plugin/plugin.json`.
2. Add an entry to `plugins` in `.claude-plugin/marketplace.json` with `"source": "./plugins/<name>"`.
3. Validate: `claude plugin validate .`
