# Skill vs MCP server

## In plain language

- A **skill** is a folder of instructions. It tells the AI how to do a task your way.
- An **MCP server** is a small program that exposes tools. It lets the AI reach something outside itself, such as GitHub.

Think of a skill as a recipe, and an MCP server as a kitchen appliance.

## Comparison

| | Skill | MCP server |
| --- | --- | --- |
| What it is | Markdown instructions | A running server with tools |
| Gives the AI | Know-how and conventions | Access to data and actions |
| Needs sign-in? | No | Often (here: OAuth sign-in to GitHub) |
| Talks to a network service? | No | Yes |
| Example here | `commit-message` | GitHub plugin integration |
| Configured in | `.agents/skills/` | Plugins in Codex |

## When to use which

- Use a **skill** to teach a repeatable way of working: style, steps, checklists.
- Use an **MCP server** when the AI must read or change something in an outside system.
- Use both when a task needs both: for example, read an issue from GitHub (MCP), then write a commit message for the fix (skill).
