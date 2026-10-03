# Connect Everygen

1. Configure the client's remote Streamable HTTP MCP server at `https://everygen-ai.com/mcp`, named `everygen`.
2. Complete OAuth in the user's browser on `everygen-ai.com`. Let the MCP client store tokens using its normal credential storage.
3. List the server's tools, then call `everygen_get_capabilities`. Report the actual result; this is the connection smoke test and does not purchase generation.
4. For generation requests, prepare a creation quote and show its brief, settings and credit cost. Start generation only after the user approves that quote.
5. Preserve task, project and quote IDs. Check existing work after a timeout; avoid starting duplicate jobs. Wait at least ten seconds between status checks.
6. Display returned media with the client's supported renderer, or share the exact media and workspace URLs. Report pending or failed jobs accurately.

The service supports an existing Everygen account with its existing entitlements. Installation does not authorize credit purchases or subscription changes. Supported models and tools are discovered from the live server rather than assumed from a static list.
