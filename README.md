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

### Claude

In **Settings → Connectors**, choose **Add custom connector**, name it `RudderStack`, and enter `https://mcp.rudderstack.com/mcp`.

For clients that require a local stdio command, use:

```bash
npx -y mcp-remote https://mcp.rudderstack.com/mcp
```

See [`examples/.mcp.json`](examples/.mcp.json) for the corresponding JSON configuration.

### VS Code

Create `.vscode/mcp.json` in your workspace using [`examples/.vscode/mcp.json`](examples/.vscode/mcp.json), then start the `rudderstack` server from VS Code's MCP controls. This example uses `mcp-remote` to connect to the hosted endpoint; sign in through your browser when prompted. You do not need to supply a client ID or client secret.

If a native HTTP connection in VS Code asks for a client ID, use the stdio example instead. Native VS Code OAuth requires the hosted server to allow the exact callback URL `https://vscode.dev/redirect`; supplying a client ID is not a workaround for a missing redirect allowlist entry.

### Cursor

Copy [`examples/.cursor/mcp.json`](examples/.cursor/mcp.json) to `.cursor/mcp.json`, then enable `rudderstack` in **Settings → Tools & Integrations → MCP Tools**.

### Windsurf and other clients

Add a custom MCP server with command `npx` and arguments `-y`, `mcp-remote`, and `https://mcp.rudderstack.com/mcp`. Clients with native Streamable HTTP support can use the endpoint directly.

## Authentication and permissions

RudderStack uses OAuth 2.0 with PKCE and dynamic client registration. A compatible client discovers the authorization metadata, opens RudderStack login in your browser, and stores the resulting credentials according to that client's security model.

Tools run with the permissions of the RudderStack user and workspace you authorize. Review tool calls before approving them, especially write operations.

## Tool access

Most tools inspect workspace settings, pipelines, schemas, metrics, profiles, audiences, documentation, and service status. Some tools make control-plane changes, including:

- switching the active workspace for the MCP session;
- creating or updating audiences;
- connecting audiences to destinations;
- creating or updating transformations; and
- connecting transformations to destinations.

Transformation tests and audience previews do not persist control-plane configuration, but they can execute code or submit temporary work. See [`docs/tools.md`](docs/tools.md) for every tool exposed by the hosted `/mcp` endpoint, its classification, and conditionally available tools.

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
