---
name: connect
description: Diagnose a broken SnagRelay MCP connection.
---

# Connect

1. Call `whoami`.
2. If it fails, tell the user exactly what the error data said:
   - Not a member → ask a project owner to invite them as a **developer** at `/users/invite`.
   - Plan → ask the project owner to upgrade at `/billing`.
   - Invalid/expired token → run `mcp_auth` for the `snagrelay` server (Cursor opens a SnagRelay page; click Allow). The server is `https://mcp.snagrelay.com/v1`, one per signed-in user. To target a specific project, pass `project_id` (from `whoami`'s project list) to the tool, or use the `/v1/projects/{id}` URL. Ignore any old `.snagrelay.json` file; it belongs to the retired VS Code extension and may name a project you can't access.
3. MCP mirrors existing SnagRelay permissions. It does not grant access to anything they cannot already see.
