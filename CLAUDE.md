# Claude Bauchladen

Curated plugin marketplace for Claude Code.

## Marketplace Structure

- `.claude-plugin/marketplace.json` — Central marketplace definition (required by Anthropic spec)
- `plugins/` — Plugin source directory (`pluginRoot` in marketplace.json)

## Marketplace JSON Schema

```json
{
  "name": "claude-bauchladen",
  "owner": { "name": "...", "email": "..." },
  "metadata": {
    "description": "...",
    "version": "1.0.0",
    "pluginRoot": "./plugins"
  },
  "plugins": [
    {
      "name": "plugin-id",              // required, kebab-case
      "source": "./plugins/plugin-id",  // required, relative path or source object
      "description": "...",
      "version": "1.0.0",
      "author": { "name": "...", "email": "..." },
      "homepage": "https://...",
      "repository": "https://...",
      "license": "MIT",
      "keywords": ["tag1"],
      "category": "productivity",
      "strict": true
    }
  ]
}
```

## Plugin Source Types

**Relative path** (local): `"source": "./plugins/my-plugin"`

**GitHub**: `"source": { "source": "github", "repo": "owner/repo", "ref": "v1.0", "sha": "..." }`

**Git URL**: `"source": { "source": "url", "url": "https://gitlab.com/team/plugin.git", "ref": "main" }`

**Git subdirectory** (monorepo): `"source": { "source": "git-subdir", "url": "...", "path": "tools/plugin" }`

**npm**: `"source": { "source": "npm", "package": "@scope/plugin", "version": "^2.0.0" }`

## Plugin Directory Structure

Each plugin in `plugins/<name>/` needs a `plugin.json`:

```json
{
  "name": "plugin-name",
  "description": "...",
  "version": "1.0.0"
}
```

Plugins can contain: skills (commands/agents), hooks, MCP servers, LSP servers.

## Useful Commands

- Validate: `claude plugin validate .` or `/plugin validate .`
- Add marketplace: `/plugin marketplace add owner/claude-bauchladen`
- Install plugin: `/plugin install plugin-name@claude-bauchladen`
- Update: `/plugin marketplace update`

## Reserved Names (cannot use)

claude-code-marketplace, claude-code-plugins, claude-plugins-official, anthropic-marketplace, anthropic-plugins, agent-skills, knowledge-work-plugins, life-sciences

## strict Mode

- `true` (default): plugin.json is authority, marketplace entry supplements
- `false`: marketplace entry is entire definition, plugin must not have own component declarations

## Environment Variables in Plugins

- `${CLAUDE_PLUGIN_ROOT}` — plugin install directory
- `${CLAUDE_PLUGIN_DATA}` — persistent data directory surviving updates
