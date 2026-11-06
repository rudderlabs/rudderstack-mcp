# RudderStack MCP

[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en-US/install-mcp?name=RudderStack&config=eyJ1cmwiOiJodHRwczovL21jcC5ydWRkZXJzdGFjay5jb20vbWNwIn0%3D)
[![Install in VS Code](https://img.shields.io/badge/VS_Code-Install-0098FF?logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjYgNiA4NCA4NCI+PHBhdGggZmlsbD0iI2ZmZiIgZmlsbC1ydWxlPSJldmVub2RkIiBkPSJNNjUuNTY2IDg5LjQyNjRDNjYuODg5IDg5Ljk0MTggNjguMzk3NiA4OS45MDg3IDY5LjczMjkgODkuMjY2Mkw4Ny4wMjcxIDgwLjk0NDZDODguODQ0NCA4MC4wNzAxIDkwIDc4LjIzMSA5MCA3Ni4yMTMyVjE5Ljc4NzJDOTAgMTcuNzY5NSA4OC44NDQ0IDE1LjkzMDMgODcuMDI3MSAxNS4wNTU5TDY5LjczMjkgNi43MzM5NUM2Ny45ODA0IDUuODkwNjkgNjUuOTI5NSA2LjA5NzI0IDY0LjM5MTQgNy4yMTU0M0M2NC4xNzE2IDcuMzc1MTcgNjMuOTYyNCA3LjU1MzUyIDYzLjc2NTkgNy43NTAwN0wzMC42NTgzIDM3Ljk1NDhMMTYuMjM3MiAyNy4wMDgxQzE0Ljg5NDggMjUuOTg5MSAxMy4wMTcxIDI2LjA3MjYgMTEuNzcwMiAyNy4yMDY3TDcuMTQ0OTUgMzEuNDE0MUM1LjYxOTg2IDMyLjgwMTQgNS42MTgxMSAzNS4yMDA3IDcuMTQxMTcgMzYuNTkwMkwxOS42NDc2IDQ4LjAwMDFMNy4xNDExNyA1OS40MDk5QzUuNjE4MTEgNjAuNzk5NSA1LjYxOTg2IDYzLjE5ODggNy4xNDQ5NSA2NC41ODYxTDExLjc3MDIgNjguNzkzNEMxMy4wMTcxIDY5LjkyNzYgMTQuODk0OCA3MC4wMTExIDE2LjIzNzIgNjguOTkyMUwzMC42NTgzIDU4LjA0NTNMNjMuNzY1OSA4OC4yNTAxQzY0LjI4OTcgODguNzc0MSA2NC45MDQ2IDg5LjE2ODggNjUuNTY2IDg5LjQyNjRaTTY5LjAxMjggMjguOTMxMUw0My44OTE3IDQ4LjAwMDFMNjkuMDEyOCA2Ny4wNjlWMjguOTMxMVoiLz48L3N2Zz4=)](https://insiders.vscode.dev/redirect/mcp/install?name=rudderstack&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Install in Visual Studio](https://img.shields.io/badge/Visual_Studio-Install-C16FDE?logo=data:image/svg%2bxml;base64,PHN2ZyBmaWxsPSIjZmZmIiByb2xlPSJpbWciIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48dGl0bGU+VmlzdWFsIFN0dWRpbzwvdGl0bGU+PHBhdGggZD0iTTE3LjU4My4wNjNhMS41IDEuNSAwIDAwLTEuMDMyLjM5MiAxLjUgMS41IDAgMDAtLjAwMSAwQS44OC44OCAwIDAwMTYuNS41TDguNTI4IDkuMzE2IDMuODc1IDUuNWwtLjQwNy0uMzVhMSAxIDAgMDAtMS4wMjQtLjE1NCAxIDEgMCAwMC0uMDEyLjAwNWwtMS44MTcuNzVhMSAxIDAgMDAtLjA3Ny4wMzYgMSAxIDAgMDAtLjA0Ny4wMjggMSAxIDAgMDAtLjAzOC4wMjIgMSAxIDAgMDAtLjA0OC4wMzQgMSAxIDAgMDAtLjAzLjAyNCAxIDEgMCAwMC0uMDQ0LjAzNiAxIDEgMCAwMC0uMDM2LjAzMyAxIDEgMCAwMC0uMDMyLjAzNSAxIDEgMCAwMC0uMDMzLjAzOCAxIDEgMCAwMC0uMDM1LjA0NCAxIDEgMCAwMC0uMDI0LjAzNCAxIDEgMCAwMC0uMDMyLjA1IDEgMSAwIDAwLS4wMi4wMzUgMSAxIDAgMDAtLjAyNC4wNSAxIDEgMCAwMC0uMDIuMDQ1IDEgMSAwIDAwLS4wMTYuMDQ0IDEgMSAwIDAwLS4wMTYuMDQ3IDEgMSAwIDAwLS4wMTUuMDU1IDEgMSAwIDAwLS4wMS4wNCAxIDEgMCAwMC0uMDA4LjA1NCAxIDEgMCAwMC0uMDA2LjA1QTEgMSAwIDAwMCA2LjY2OHYxMC42NjZhMSAxIDAgMDAuNjE1LjkxN2wxLjgxNy43NjRhMSAxIDAgMDAxLjAzNS0uMTY0bC40MDgtLjM1IDQuNjUzLTMuODE1IDcuOTczIDguODE1YTEuNSAxLjUgMCAwMC4wNzIuMDY1IDEuNSAxLjUgMCAwMC4wNTcuMDUgMS41IDEuNSAwIDAwLjA1OC4wNDIgMS41IDEuNSAwIDAwLjA2My4wNDQgMS41IDEuNSAwIDAwLjA2NS4wMzggMS41IDEuNSAwIDAwLjA2NS4wMzYgMS41IDEuNSAwIDAwLjA2OC4wMzEgMS41IDEuNSAwIDAwLjA3LjAzIDEuNSAxLjUgMCAwMC4wNzMuMDI1IDEuNSAxLjUgMCAwMC4wNjYuMDIgMS41IDEuNSAwIDAwLjA4LjAyIDEuNSAxLjUgMCAwMC4wNjguMDE0IDEuNSAxLjUgMCAwMC4wNzUuMDEgMS41IDEuNSAwIDAwLjA3NS4wMDggMS41IDEuNSAwIDAwLjA3My4wMDMgMS41IDEuNSAwIDAwLjA3NyAwIDEuNSAxLjUgMCAwMC4wNzgtLjAwNSAxLjUgMS41IDAgMDAuMDY3LS4wMDcgMS41IDEuNSAwIDAwLjA4Ny0uMDE1IDEuNSAxLjUgMCAwMC4wNi0uMDEyIDEuNSAxLjUgMCAwMC4wOC0uMDIyIDEuNSAxLjUgMCAwMC4wNjgtLjAyIDEuNSAxLjUgMCAwMC4wNy0uMDI4IDEuNSAxLjUgMCAwMC4wOS0uMDM3bDQuOTQ0LTIuMzc3YTEuNSAxLjUgMCAwMC40NzYtLjM2MiAxLjUgMS41IDAgMDAuMDktLjExMiAxLjUgMS41IDAgMDAuMDA0LS4wMDcgMS41IDEuNSAwIDAwLjA4LS4xMjUgMS41IDEuNSAwIDAwLjA2Mi0uMTIgMS41IDEuNSAwIDAwLjAwOS0uMDE3IDEuNSAxLjUgMCAwMC4wNC0uMTA4IDEuNSAxLjUgMCAwMC4wMTUtLjAzNyAxLjUgMS41IDAgMDAuMDMtLjEwNyAxLjUgMS41IDAgMDAuMDA5LS4wMzcgMS41IDEuNSAwIDAwLjAxNy0uMSAxLjUgMS41IDAgMDAuMDA4LS4wNSAxLjUgMS41IDAgMDAuMDA2LS4wOSAxLjUgMS41IDAgMDAuMDA0LS4wOFYzLjk0MmExLjUgMS41IDAgMDAwLS4wMDMgMS41IDEuNSAwIDAwMC0uMDMyIDEuNSAxLjUgMCAwMC0uMDEtLjE1IDEuNSAxLjUgMCAwMC0uODQtMS4xN0wxOC4yMDYuMjFhMS41IDEuNSAwIDAwLS42MjItLjE0NnpNMTggNi45MnYxMC4xNjNsLTYuMTk4LTUuMDh6TTMgOC41NzRsMy4wOTkgMy40MjctMy4xIDMuNDI2eiIvPjwvc3ZnPg==)](https://aka.ms/vs/mcp-install?%7B%22name%22%3A%22rudderstack%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Add to Kiro](https://kiro.dev/images/add-to-kiro.svg)](https://kiro.dev/launch/mcp/add?name=rudderstack&config=%7B%22url%22%3A%22https%3A%2F%2Fmcp.rudderstack.com%2Fmcp%22%7D)
[![Install in Goose](https://block.github.io/goose/img/extension-install-dark.svg)](https://block.github.io/goose/extension?url=https%3A%2F%2Fmcp.rudderstack.com%2Fmcp&type=streamable_http&id=rudderstack&name=RudderStack&description=Manage%20your%20RudderStack%20workspace%20from%20Goose)
[![Add to LM Studio](https://files.lmstudio.ai/deeplink/mcp-install-dark.svg)](https://lmstudio.ai/install-mcp?name=rudderstack&config=eyJ1cmwiOiJodHRwczovL21jcC5ydWRkZXJzdGFjay5jb20vbWNwIn0%3D)
[![Connect in Claude](https://img.shields.io/badge/Claude-Connect-D97757?logo=claude&logoColor=white)](#claude)
[![Install in Claude Code](https://img.shields.io/badge/Claude_Code-Install-D97757?logo=claude&logoColor=white)](#claude-code)
[![Install in Gemini CLI](https://img.shields.io/badge/Gemini_CLI-Install-8E75B2?logo=googlegemini&logoColor=white)](#gemini-cli)
[![Install in Cline](https://img.shields.io/badge/Cline-Install-555555?logo=cline&logoColor=white)](#cline)

[![Official MCP Registry](https://img.shields.io/badge/MCP_Registry-io.github.rudderlabs%2Frudderstack--mcp-0A0A0A?logo=modelcontextprotocol&logoColor=white)](https://registry.modelcontextprotocol.io/v0/servers?search=io.github.rudderlabs/rudderstack-mcp)
[![AllMCPs Verified](https://allmcps.com/api/badge/rudderstack-mcp)](https://allmcps.com/mcp/rudderstack-mcp?verify=1d39113b-927a-479a-a499-80c4a7be74e4)
[![Listed on Glama](https://img.shields.io/badge/Listed_on-Glama-4B5563)](https://glama.ai/mcp/connectors/com.rudderstack.mcp/rudder-stack-mcp)
[![Listed on Toolradar](https://img.shields.io/badge/Listed_on-Toolradar-4B5563)](https://toolradar.com/tools/rudderstack-mcp)
[![Listed on MCP Repository](https://img.shields.io/badge/Listed_on-MCP_Repository-4B5563)](https://mcprepository.com/rudderlabs/rudderstack-mcp)
[![Listed on mcpservers.org](https://img.shields.io/badge/Listed_on-mcpservers.org-4B5563)](https://mcpservers.org/servers/www-rudderstack-com-docs-ai-features-rudderstack-mcp-connect)

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
