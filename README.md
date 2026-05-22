<!-- mcp-name: app.steep/mcp -->

# Steep MCP

This repository contains the configuration needed to integrate Steep with
Claude Code, Cursor, and other MCP-compatible clients. The plugin lets your
AI agents interact directly with your Steep workspace, querying metrics,
targets, entities, and team data through natural language.

## Features

The Steep MCP server provides the following capabilities:

- **Metrics**: list metrics in the workspace and query metric data over any
  date range, with optional slicing and breakdowns
- **Targets**: list targets and query target progress
- **Entities & modules**: list entities and the modules they appear in
- **Workspace**: list workspace members and teams

All tools are read-only.

## Prerequisites

Before setting up the Steep MCP server, ensure you have:

- Claude Code CLI, Cursor IDE, or another MCP-compatible client installed
- A Steep account with access to the workspace you want to query

## Installation

### Claude Code & Cowork

Install from the [community plugin marketplace](https://github.com/anthropics/claude-plugins-community):

```bash
/plugin marketplace add anthropics/claude-plugins-community
/plugin install steep@claude-community
```

Alternatively, install directly from this repo:

```bash
git clone https://github.com/SteepHq/steep-mcp.git
claude --plugin-dir ./steep-mcp
```

Either path loads `.claude-plugin/plugin.json` and the sibling `.mcp.json`, configures the Steep MCP server, and prompts you to authenticate via OAuth.
No client ID is needed — Claude Code discovers the auth server and registers itself dynamically.

### Cursor

Install with one click from the [Cursor plugin marketplace](https://cursor.com/en-US/marketplace).

Alternatively, add Steep manually: **Cursor → Settings → MCP** and paste:

```json
{
  "mcpServers": {
    "steep": {
      "url": "https://mcp.steep.app/mcp"
    }
  }
}
```

Save the configuration, then click the connect button to authenticate via OAuth.

### Other MCP clients

Point your client at `https://mcp.steep.app/mcp` (Streamable HTTP transport). Clients supporting
Dynamic Client Registration (RFC 7591) will register automatically.

## Usage Examples

Once configured, you can interact with Steep through your AI assistant using
natural language:

- **List metrics**: "What metrics do we have in Steep?"
- **Query data**: "Show MRR for the last 6 months, broken down by plan"
- **Track targets**: "How are we tracking against our Q2 revenue target?"
- **Explore the data model**: "Which entities slice the customer count metric?"
- **Find people**: "Who's on the growth team in Steep?"

## Updates

Marketplace installs (Claude Code, Cursor) auto-update when we publish a new version. Run `/plugin update steep` in Claude Code to pull the latest.

Cursor handles updates through its own marketplace UI. Users who installed manually via `--plugin-dir` or by editing `mcp.json` directly will keep using whatever revision they cloned — re-clone or re-paste to get changes.

## Documentation & resources

- [Steep documentation](https://help.steep.app)
- [Steep privacy policy](https://steep.app/privacy)
- [Model Context Protocol specification](https://modelcontextprotocol.io)

## Notes & limitations

- **Remote server only**: this configuration connects to Steep's hosted MCP
  server. No local installation is required or supported.
- **Workspace scope**: you can only access data your Steep user account
  already has access to. OAuth scopes are limited to the read scopes the
  server advertises at `/.well-known/oauth-protected-resource`.

## Questions or Issues?

For product questions and integration help, contact
[help@steep.app](mailto:help@steep.app).

For security reports, see [SECURITY.md](./SECURITY.md).

## License

Apache-2.0 — see [LICENSE](./LICENSE).

The Steep name and logo are trademarks of Steep. See [NOTICE](./NOTICE).
