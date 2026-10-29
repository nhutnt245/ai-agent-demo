# AI agent demo: skills and MCP

A tiny repo for a live demo. You prompt an AI tool (OpenAI Codex).
The AI then uses a **skill** and an **MCP server** by itself. There is no custom agent code.

- Skill: `commit-message` writes a commit message in this repo's style.
- MCP: the GitHub MCP server lets the AI read data from GitHub.

## Setup (5 minutes)

1. Install [Codex](https://developers.openai.com/codex) (CLI) and clone this repo.
2. Create a GitHub personal access token (GitHub > Settings > Developer settings). Read-only access to the repos you want to query is enough.
3. Set the token in your shell. Never put it in a file in this repo:

   ```bash
   export GITHUB_PAT="your_token_here"
   ```

4. Start Codex from the repo root, in the same shell, and trust the project when asked (Codex only loads project config from trusted projects):

   ```bash
   codex
   ```

5. Check the server with `/mcp` inside Codex, or `codex mcp list`. Check the skill with `/skills`.

`.codex/config.toml` sets `bearer_token_env_var = "GITHUB_PAT"`, so Codex reads the token from your shell and the secret stays out of git.

If your Codex does not pick up the project config, copy the `[mcp_servers.github]` block from `.codex/config.toml` into `~/.codex/config.toml`.

## Sample prompts

- Triggers the skill (make a small uncommitted edit first, for example to `README.md`, so there is a diff): `I changed the README to add a setup section. Write me a commit message.`
- Triggers the MCP server: `Using GitHub, list the 5 most recent open issues in openai/codex.`

The full script is in [docs/demo-script.md](docs/demo-script.md). More background: [docs/overview.md](docs/overview.md), [docs/skill-vs-mcp.md](docs/skill-vs-mcp.md).
