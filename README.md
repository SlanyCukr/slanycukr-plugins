# slanycukr-plugins

Claude Code plugin marketplace.

## Plugins

| Plugin | Description |
|---|---|
| [lsp-agents](lsp-agents/) | LSP and semantic search-first agents for plan mode |

## Installation

```bash
claude plugins:add-marketplace /path/to/slanycukr-plugins
```

Or clone to `~/.claude/plugins/marketplaces/slanycukr-plugins/` and enable plugins in settings:

```json
{
  "enabledPlugins": {
    "lsp-agents@slanycukr-plugins": true
  }
}
```
