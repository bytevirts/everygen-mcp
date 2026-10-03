# Everygen

Create images, short videos, narration, music and multi-shot video projects from an MCP-compatible assistant.

This is the official connection package for **[Everygen](https://everygen-ai.com)**, published by `bytevirts`. It connects to **everygen-ai.com**. Check the domain when connecting services with similar names.

## Connection

| Setting | Value |
|---|---|
| Display name | Everygen |
| MCP endpoint | `https://everygen-ai.com/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 authorization code with S256 PKCE |
| Registry name | `io.github.bytevirts/everygen` |

An Everygen account is required. Sign in on the Everygen authorization page and approve the requested permissions. The client manages tokens; do not paste a password or a fixed bearer token into the configuration. The service uses your existing Everygen credits. Review and approve each generation quote before starting work.

### Claude

Add a custom connector with the endpoint above, then connect your Everygen account. This repository also includes a Claude plugin manifest and `.mcp.json` for clients supporting that package format.

For Claude Code, the remote connection can be added with:

```sh
claude mcp add --transport http everygen https://everygen-ai.com/mcp
```

Use Claude Code's `/mcp` interface to complete OAuth and inspect connection status.

### Cursor

Add the following server entry to your MCP settings, or use the Cursor plugin package in this repository:

```json
{
  "mcpServers": {
    "everygen": {
      "url": "https://everygen-ai.com/mcp"
    }
  }
}
```

Connect and complete the OAuth flow when prompted. The plugin declares the same remote service in `mcp.json`.

### Cline and other clients

Use the client's remote Streamable HTTP MCP connection flow with `https://everygen-ai.com/mcp`. The client must support OAuth authorization code with PKCE. Complete the browser authorization and then list tools to verify the connection. Consult the client's documentation for its configuration field names; they differ between clients.

## First verification

Ask the assistant to call `everygen_get_capabilities` and list the supported media types. This discovery step does not generate media. Available models and settings come from the service and may change.

For a first creation, ask: **“Create a square watercolor illustration of a fox. Show me the credit cost first.”** The assistant should prepare a quote, show the proposed request and cost, and wait for your approval before starting it.

Generated media and Director projects are asynchronous. Preserve the returned task or project ID and poll that ID. A pending response or timeout is not permission to submit a second generation. Retry with the original quote where applicable.

## Capabilities

- Generate images from a creative brief and supported references.
- Generate short videos using supported models and owned library references.
- Create narration using available preset voices and generate music.
- Plan and produce multi-shot projects with AI Director.
- Browse the connected account's assets and retrieve task/project status.

Tools work through standard MCP results. Clients with MCP Apps support can additionally show interactive results; other clients can use returned media URLs and workspace links. A client accepting this configuration is not a guarantee that its public marketplace has approved a listing.

## Data and account access

Requests operate on the connected account's owned assets and projects. Media generation can send the authorized brief and references to the model providers described in the privacy policy. Account permissions and consent are controlled by OAuth. Disconnect or revoke access when you no longer want the integration connected.

This public repository contains connection metadata, documentation and brand assets. It does not contain application source code, credentials or reviewer accounts.

## Support

- [Website](https://everygen-ai.com)
- [Support](https://everygen-ai.com/support)
- [Privacy policy](https://everygen-ai.com/privacy-policy)
- [Terms of service](https://everygen-ai.com/terms-of-service)
- Contact: `support@everygen-ai.com`
