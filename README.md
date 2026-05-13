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

Choose the installation method for your client:

### Claude Code

If you're using Claude Code CLI, you can install this as a plugin by cloning
it locally:

```bash
git clone https://github.com/SteepHq/steep-mcp.git
cd steep-mcp
claude --plugin-dir ./
```

The Steep MCP server will be automatically configured when the plugin loads.
You will be prompted to authenticate into your Steep workspace via OAuth.

The Claude plugin uses the following MCP configuration (`.mcp.json`):

```json
{
  "mcpServers": {
    "steep": {
      "type": "http",
      "url": "https://mcp.steep.app/mcp"
    }
  }
}
```

Claude Code discovers the OAuth authorization server via the resource
metadata at `https://mcp.steep.app/.well-known/oauth-protected-resource` and
registers itself dynamically — no client ID needs to be configured.

### Cursor

Open **Cursor → Settings → Cursor Settings** (or use the keyboard shortcut
`Cmd+,` on macOS, `Ctrl+,` on Windows/Linux) and navigate to the **MCP** tab.

Add the following configuration to connect to the remote Steep MCP server:

```json
{
  "mcpServers": {
    "steep": {
      "url": "https://mcp.steep.app/mcp"
    }
  }
}
```

Save the configuration. A connect button will appear once the entry is added;
click it to authenticate into your Steep workspace.

## Usage Examples

Once configured, you can interact with Steep through your AI assistant using
natural language:

- **List metrics**: "What metrics do we have in Steep?"
- **Query data**: "Show MRR for the last 6 months, broken down by plan"
- **Track targets**: "How are we tracking against our Q2 revenue target?"
- **Explore the data model**: "Which entities slice the customer count metric?"
- **Find people**: "Who's on the growth team in Steep?"

## Documentation & Resources

- [Steep documentation](https://help.steep.app)
- [Steep privacy policy](https://steep.app/privacy)
- [Model Context Protocol specification](https://modelcontextprotocol.io)

## Notes & Limitations

- **Remote server only**: this configuration connects to Steep's hosted MCP
  server. No local installation is required or supported.
- **Read-only**: every tool is read-only; the MCP server cannot modify metrics,
  targets, or any other workspace state.
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
