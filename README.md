# AI agent demo: skills and MCP

A tiny repo for a live demo. You prompt an AI tool (Claude Code; Codex optional).
The AI then uses a **skill** and an **MCP server** by itself. There is no custom agent code.

- Skill: `commit-message` writes a commit message in this repo's style.
- MCP: the GitHub MCP server lets the AI read data from GitHub.

## Setup (5 minutes)

1. Install [Claude Code](https://docs.claude.com/en/docs/claude-code) and clone this repo.
2. Create a GitHub personal access token (GitHub > Settings > Developer settings). Read-only access to the repos you want to query is enough.
3. Set the token in your shell. Never put it in a file in this repo:

   ```bash
   export GITHUB_PAT="your_token_here"
   ```

4. Start Claude Code from the repo root, in the same shell:

   ```bash
   claude
   ```

5. Approve the project `github` server when asked. Check it with `claude mcp list`.

`.mcp.json` reads the token from `${GITHUB_PAT}`, so the secret stays out of git.

## Sample prompts

- Triggers the skill: `I changed the README to add a setup section. Write me a commit message.`
- Triggers the MCP server: `Using GitHub, list the 5 most recent open issues in anthropics/claude-code.`

The full script is in [docs/demo-script.md](docs/demo-script.md). More background: [docs/overview.md](docs/overview.md), [docs/skill-vs-mcp.md](docs/skill-vs-mcp.md).
