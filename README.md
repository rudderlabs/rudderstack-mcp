# RudderStack MCP

[![AllMCPs Verified](https://allmcps.com/api/badge/rudderstack-mcp)](https://allmcps.com/mcp/rudderstack-mcp?verify=1d39113b-927a-479a-a499-80c4a7be74e4)

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

### One-click install

Open your client's button below. The client adds the server, then opens a browser so you can sign in to RudderStack.

[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en-US/install-mcp?name=RudderStack&config=eyJ1cmwiOiJodHRwczovL21jcC5ydWRkZXJzdGFjay5jb20vbWNwIn0%3D)
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install_RudderStack_MCP-0098FF?logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=rudderstack&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Install in VS Code Insiders](https://img.shields.io/badge/VS_Code_Insiders-Install_RudderStack_MCP-24bfa5?logo=visualstudiocode&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=rudderstack&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D&quality=insiders)
[![Install in Visual Studio](https://img.shields.io/badge/Visual_Studio-Install_RudderStack_MCP-C16FDE?logo=visualstudio&logoColor=white)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22rudderstack%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Add to Kiro](https://kiro.dev/images/add-to-kiro.svg)](https://kiro.dev/launch/mcp/add?name=rudderstack&config=%7B%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Install in Goose](https://block.github.io/goose/img/extension-install-dark.svg)](https://block.github.io/goose/extension?url=https%3A%2F%2Fmcp.rudderstack.com%2Fmcp&type=streamable_http&id=rudderstack&name=RudderStack&description=Manage%20your%20RudderStack%20workspace%20from%20Goose)
[![Add to LM Studio](https://files.lmstudio.ai/deeplink/mcp-install-dark.svg)](https://lmstudio.ai/install-mcp?name=rudderstack&config=eyJ1cmwiOiJodHRwczovL21jcC5ydWRkZXJzdGFjay5jb20vbWNwIn0%3D)

Claude Code:

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
