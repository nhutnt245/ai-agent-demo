# Skill vs plugin vs MCP server

## In plain language

- A **skill** is a folder of instructions. It tells the AI how to do a task your way.
- A **plugin** (Codex Plugins page) is a ready-made integration you sign in to. The GitHub plugin used in this demo is a plugin, not an MCP server, and does not appear in `/mcp`.
- An **MCP server** is a small program that exposes tools. You add it by hand (`codex mcp add` or `config.toml`), and it appears in `/mcp`. A GitHub MCP server is an optional alternative (path B in `demo-script.md`).

Think of a skill as a recipe, and a plugin or MCP server as a kitchen appliance.

## Comparison

| | Skill | Plugin | MCP server (hand-added) |
| --- | --- | --- | --- |
| What it is | Markdown instructions | Integration chosen in the Codex UI | A server with tools you configure yourself |
| Gives the AI | Know-how and conventions | Access to data and actions | Access to data and actions |
| Needs sign-in? | No | Often (here: sign-in to GitHub) | Yes (here: a token in `GITHUB_PAT`) |
| Talks to a network service? | No | Yes | Yes |
| Example here | `commit-message` | GitHub plugin (path A) | GitHub MCP server (path B) |
| Configured in | `.agents/skills/` | Plugins in Codex | `codex mcp add` or `config.toml` |
| Shows in `/mcp`? | No | No | Yes |

## When to use which

- Use a **skill** to teach a repeatable way of working: style, steps, checklists.
- Use a **plugin** or an **MCP server** when the AI must read or change something in an outside system.
- Use both when a task needs both: for example, read an issue from GitHub (plugin), then write a commit message for the fix (skill).
