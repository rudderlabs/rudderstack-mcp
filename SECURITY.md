# Security Policy

## Supported surface

Security reports may cover the hosted RudderStack MCP endpoint at `https://mcp.rudderstack.com/mcp`, its OAuth flow, and the configuration examples or registry metadata in this repository.

This repository does not contain the hosted server implementation. Product support requests and non-security bugs should use the public issue templates instead.

## Reporting a vulnerability

Do not open a public GitHub issue for a suspected vulnerability. Email [security@rudderstack.com](mailto:security@rudderstack.com) with:

- a concise description of the issue and its impact;
- the affected endpoint, OAuth step, MCP client, and client version;
- reproduction steps or a minimal proof of concept; and
- any relevant request or response metadata after removing secrets and customer data.

RudderStack will acknowledge and triage reports through the private reporting channel.

## Protect sensitive data

Never include access or refresh tokens, authorization codes, client secrets, cookies, workspace IDs, source write keys, event payloads, customer data, or other credentials in a public issue or report. Redact sensitive request headers and response bodies. If a secret was exposed, revoke or rotate it immediately before reporting the incident.
