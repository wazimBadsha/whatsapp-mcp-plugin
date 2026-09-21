# ChatGPT and Grok MCP compatibility

This repository keeps stdio as the default local MCP transport and adds Streamable HTTP for remote MCP clients.

## ChatGPT

Run the MCP server with:

```bash
MCP_TRANSPORT=http MCP_HOST=0.0.0.0 MCP_PORT=8000 MCP_PATH=/mcp uv run whatsapp-mcp-server/main.py
```

Expose the endpoint through HTTPS and an authentication/authorization layer before connecting it to ChatGPT. The remote endpoint is:

```
https://YOUR-DOMAIN.example/mcp
```

Configure it as a custom MCP app/connector in ChatGPT Developer Mode where custom MCP apps are available.

## Grok

Grok supports custom MCP connectors. Use the same Streamable HTTP endpoint:

```
https://YOUR-DOMAIN.example/mcp
```

For local development, keep stdio enabled or use a secure tunnel. Do not expose an unauthenticated WhatsApp MCP server directly to the public internet.

## Claude and local MCP hosts

The default remains:

```bash
MCP_TRANSPORT=stdio uv run whatsapp-mcp-server/main.py
```

## Security

The server handles private WhatsApp messages and write-capable tools. Remote deployment must use HTTPS, authentication/authorization, least-privilege tool exposure, and appropriate network controls.
