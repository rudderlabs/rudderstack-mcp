# RudderStack MCP

[![Add to Cursor](assets/badges/cursor.svg)](https://cursor.com/en-US/install-mcp?name=RudderStack&config=eyJ1cmwiOiJodHRwczovL21jcC5ydWRkZXJzdGFjay5jb20vbWNwIn0%3D)
[![Install in VS Code](assets/badges/vscode.svg)](https://insiders.vscode.dev/redirect/mcp/install?name=rudderstack&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Install in Visual Studio](assets/badges/visual-studio.svg)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22rudderstack%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Add to Kiro](assets/badges/kiro.svg)](https://kiro.dev/launch/mcp/add?name=rudderstack&config=%7B%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Install in Goose](assets/badges/goose.svg)](https://block.github.io/goose/extension?url=https%3A%2F%2Fmcp.rudderstack.com%2Fmcp&type=streamable_http&id=rudderstack&name=RudderStack&description=Manage%20your%20RudderStack%20workspace%20from%20Goose)
[![Add to LM Studio](assets/badges/lm-studio.svg)](https://lmstudio.ai/install-mcp?name=rudderstack&config=eyJ1cmwiOiJodHRwczovL21jcC5ydWRkZXJzdGFjay5jb20vbWNwIn0%3D)

[![Works with Claude](assets/badges/claude.svg)](#claude)
[![Works with Claude Code](assets/badges/claude-code.svg)](#claude-code)
[![Works with ChatGPT](assets/badges/chatgpt.svg)](#chatgpt)
[![Works with Codex](assets/badges/codex.svg)](#codex)
[![Works with Gemini CLI](assets/badges/gemini-cli.svg)](#gemini-cli)
[![Works with Cline](assets/badges/cline.svg)](#cline)
[![Works with Windsurf](assets/badges/windsurf.svg)](#windsurf-and-other-clients)
[![Docker MCP Catalog, coming soon](assets/badges/docker.svg)](https://github.com/docker/mcp-registry/pull/6695)

[![Official MCP Registry](https://img.shields.io/badge/MCP_Registry-published-10b981?style=flat&logo=modelcontextprotocol&logoColor=white&labelColor=1e293b)](https://registry.modelcontextprotocol.io/v0/servers?search=io.github.rudderlabs/rudderstack-mcp)
[![AllMCPs Verified](https://allmcps.com/api/badge/rudderstack-mcp)](https://allmcps.com/mcp/rudderstack-mcp?verify=1d39113b-927a-479a-a499-80c4a7be74e4)
[![Listed on Glama](https://img.shields.io/badge/Glama-listed-10b981?style=flat&labelColor=1e293b)](https://glama.ai/mcp/connectors/com.rudderstack.mcp/rudder-stack-mcp)
[![Listed on Toolradar](https://img.shields.io/badge/Toolradar-listed-10b981?style=flat&labelColor=1e293b)](https://toolradar.com/tools/rudderstack-mcp)
[![Listed on MCP Repository](https://img.shields.io/badge/MCP_Repository-listed-10b981?style=flat&labelColor=1e293b)](https://mcprepository.com/rudderlabs/rudderstack-mcp)
[![Listed on mcpservers.org](https://img.shields.io/badge/mcpservers.org-listed-10b981?style=flat&labelColor=1e293b)](https://mcpservers.org/servers/www-rudderstack-com-docs-ai-features-rudderstack-mcp-connect)

Connect AI assistants and developer tools to your RudderStack workspace through the hosted [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) server.

> [!IMPORTANT]
> This public repository contains registry metadata, setup examples, and documentation for the hosted RudderStack MCP server. It does **not** contain the server implementation source code, and its MIT license applies only to this repository's contents.

- **Endpoint:** `https://mcp.rudderstack.com/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** OAuth 2.0 with browser-based RudderStack login and authorization
- **Canonical setup guide:** [RudderStack MCP documentation](https://www.rudderstack.com/docs/ai-features/rudderstack-mcp/)
- **Tool reference:** [Read and write capabilities](docs/tools.md)

## Connect

Native remote-MCP clients can connect directly to:

```text
https://mcp.rudderstack.com/mcp
```

On the first connection, the client opens a browser so you can sign in to RudderStack and authorize access. No token or client secret belongs in these configuration files.

### Claude Code

```bash
claude mcp add --transport http --scope user rudderstack https://mcp.rudderstack.com/mcp
```

### Claude

In **Settings → Connectors**, choose **Add custom connector**, name it `RudderStack`, and enter `https://mcp.rudderstack.com/mcp`.

For clients that require a local stdio command, use:

```bash
npx -y mcp-remote https://mcp.rudderstack.com/mcp
```

See [`examples/.mcp.json`](examples/.mcp.json) for the corresponding JSON configuration.

### ChatGPT

Until RudderStack is in the ChatGPT app directory, add it as a custom connector: **Settings → Apps & Connectors → Advanced settings**, turn on **Developer mode**, choose **Create**, enter `https://mcp.rudderstack.com/mcp` with OAuth, then sign in to RudderStack.

### Codex

Add to `~/.codex/config.toml`:

```toml
[mcp_servers.rudderstack]
url = "https://mcp.rudderstack.com/mcp"
```

Then run `codex mcp login rudderstack` and sign in to RudderStack in the browser.

### VS Code

Create `.vscode/mcp.json` in your workspace using [`examples/.vscode/mcp.json`](examples/.vscode/mcp.json), then start the `rudderstack` server from VS Code's MCP controls.

### Cursor

Copy [`examples/.cursor/mcp.json`](examples/.cursor/mcp.json) to `.cursor/mcp.json`, then enable `rudderstack` in **Settings → Tools & Integrations → MCP Tools**.

### Cline

In Cline, open **MCP Servers → Remote Servers**, add a server named `rudderstack` with URL `https://mcp.rudderstack.com/mcp` and transport **Streamable HTTP**, then sign in to RudderStack in the browser when prompted.

### Gemini CLI

Install the extension from this repository:

```bash
gemini extensions install https://github.com/rudderlabs/rudderstack-mcp
```

Then run `/mcp auth rudderstack` in Gemini CLI, sign in to RudderStack in the browser, and approve access. The extension manifest is [`gemini-extension.json`](gemini-extension.json).

### Windsurf and other clients

Add a custom MCP server with command `npx` and arguments `-y`, `mcp-remote`, and `https://mcp.rudderstack.com/mcp`. Clients with native Streamable HTTP support can use the endpoint directly.

## Authentication and permissions

RudderStack uses OAuth 2.0 with PKCE and accepts client ID metadata documents alongside dynamic client registration. A compatible client discovers the authorization metadata, opens RudderStack login in your browser, and stores the resulting credentials according to that client's security model.

Tools run with the permissions of the RudderStack user and workspace you authorize. Review tool calls before approving them, especially write operations. Workspace tools require `workspace_id` (or `workspaceId`) from `user_details` on every call; the endpoint is stateless.

## Tool access

Most tools inspect workspace settings, pipelines, schemas, metrics, profiles, audiences, documentation, and service status. Some tools make control-plane changes or trigger syncs, including:

- creating or updating audiences;
- connecting audiences to destinations;
- creating rETL audience activations;
- triggering audience-activation syncs;
- creating or updating transformations; and
- connecting transformations to destinations.

Transformation tests, audience previews, Reverse ETL failed-record reads, and audience-activation planning do not persist control-plane configuration, but they can execute code or submit temporary warehouse work. See [`docs/tools.md`](docs/tools.md) for every tool exposed by the hosted `/mcp` endpoint, its classification, and conditionally available tools.

## Security and support

- Report suspected vulnerabilities privately as described in [`SECURITY.md`](SECURITY.md).
- For product bugs, use the [bug report form](https://github.com/rudderlabs/rudderstack-mcp/issues/new?template=bug_report.yml).
- For tool requests, use the [tool request form](https://github.com/rudderlabs/rudderstack-mcp/issues/new?template=tool_request.yml).
- Never post access tokens, workspace IDs, event payloads, customer data, or credentials in a public issue.

## Resources

- [RudderStack MCP setup guide](https://www.rudderstack.com/docs/ai-features/rudderstack-mcp/)
- [RudderStack documentation](https://www.rudderstack.com/docs/)
- [Model Context Protocol](https://modelcontextprotocol.io/)
- [Official MCP Registry](https://registry.modelcontextprotocol.io/)

## License

The documentation, examples, and metadata in this repository are available under the [MIT License](LICENSE). This license does not apply to the hosted server's private implementation.
