# lsp-agents

Claude Code plugin providing LSP and semantic search-first agents for plan mode.

Replaces the default Explore and Plan subagents (which only use Grep/Glob/Read)
with agents that prioritize `mcp__semvex__search_code_tool` and LSP for code
navigation.

## Agents

| Agent | Purpose | Primary tools |
|---|---|---|
| `lsp-explore` | Codebase exploration | Semvex semantic search, LSP (definitions, references, call hierarchy) |
| `lsp-plan` | Architecture and implementation planning | Same as lsp-explore, plus structured plan output |

### Tool hierarchy

Both agents follow the same decision chain:

1. **Semvex** (`mcp__semvex__search_code_tool`) — conceptual queries ("authentication logic", "error handling")
2. **LSP** — structural navigation (definitions, references, call hierarchy, type info)
3. **Grep/Glob** — fallback for exact text patterns and file name matching

## Requirements

- [semvex-mcp](https://github.com/SlanyCukr/semvex-mcp) running as an MCP server
- LSP servers configured for your project languages (e.g. `typescript-lsp`, `pyright-lsp` plugins)

## Installation

### As a local plugin

```bash
claude --plugin-dir /path/to/lsp-agents
```

### As a marketplace plugin

Add to your Claude Code plugins marketplace, then enable in settings:

```json
{
  "enabledPlugins": {
    "lsp-agents@your-marketplace": true
  }
}
```

## Usage with daneel-claude-code

The [daneel-claude-code](https://github.com/SlanyCukr/daneel-claude-code) tweakcc
customizations include plan-mode system prompts that reference `lsp-agents:lsp-explore`
and `lsp-agents:lsp-plan`. Install this plugin to activate those references.
