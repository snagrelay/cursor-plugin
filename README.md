# SnagRelay

> Your users find the bugs. Your agent fixes them. Give Cursor a ticket key and it reads the same evidence a human debugger would open: the broken element, console errors with file and line, failing requests with their bodies, repro steps and a short replay.

## What this plugin does

When installed, the SnagRelay Cursor Plugin gives your agent:

- **`get_issue_context`**: load the full context of a SnagRelay issue (the element, repro steps, console errors with file and line, requests with their request and response bodies, and a link to the screenshot)
- **`get_issue_payload`**: fetch one full request or response body, or one console entry
- **`get_related_history`**: past resolved issues on the same screen or endpoint, with the PR that fixed them
- **`find_issues`**: list or search issues when you have no key
- **`report_progress`**: tell SnagRelay which file the agent is editing
- **`mark_issue_resolved`**: mark an issue resolved with the PR, commit and branch
- **`whoami`**: show the signed-in account and its projects

Plus 6 skills (`/fix-issue`, `/open-pr`, `/resolve-issue`, `/triage`, `/connect`, `/scope`) and a rule that tells the agent to load an issue's context before proposing a fix.

## Install

1. Search **SnagRelay** in Cursor Marketplace (Customize → Marketplace) and install the plugin
2. Cursor shows **Needs authentication** for the `snagrelay` MCP server. Click it
3. Your browser opens a SnagRelay page. Sign in if needed and click **Allow**

There is no token to copy. The server is `https://mcp.snagrelay.com/v1`.

For CI or scripts, create an API token in SnagRelay (Settings → API tokens) and call the same URL with `Authorization: Bearer <token>`.

## Usage

```
# In Cursor Agent chat:
fix PROJ-123
→ Agent calls get_issue_context("PROJ-123") automatically
→ Reads the failing request and its response body, the console error with file and line, and the repro steps
→ Checks earlier similar bugs and what fixed them
→ Proposes a targeted fix
```

## Skills included

| Skill | What it does |
|---|---|
| Fix issue | Load context + propose fix for a SnagRelay issue |
| Triage | List open issues so you can pick one |
| Connect | Diagnose a broken MCP connection |
| Scope | When the agent may call SnagRelay MCP |
| Open PR | Branch `feature/{key}-{summary}`, PR title `[{key}] {type}: {description}`, full description |
| Resolve issue | Commit and open a PR if needed, then mark the issue resolved |

## Requirements

- SnagRelay account (free tier available at [snagrelay.com](https://snagrelay.com))
- Cursor with Plugins support

## Source

This repo is the public listing for the Cursor Marketplace. The MCP server itself lives in the SnagRelay app.
