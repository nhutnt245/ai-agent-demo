# AI agent demo: skills and MCP

A tiny repo for a live demo. You prompt an AI tool (OpenAI Codex).
The AI then uses a **skill** and an **MCP server** by itself. There is no custom agent code.

- Skill: `commit-message` writes a commit message in this repo's style.
- MCP: the GitHub MCP server lets the AI read data from GitHub.

## Setup (5 minutes)

1. Install [Codex](https://developers.openai.com/codex) and open this repo in it.
2. In the Codex UI, connect the GitHub MCP server and sign in with OAuth. Codex docs: [MCP](https://developers.openai.com/codex/mcp).
3. On the GitHub authorization screen, authorize **only the `ai-agent-demo` repo**. Do not grant access to any organization.
4. Type `/mcp` in the Codex composer to check that GitHub is connected. Type `/skills` to check the skill.

No personal access token is used, and nothing secret is stored in this repo.

Note: the exact button and menu names can differ by Codex app version. The Codex docs describe adding an MCP server under **Settings > MCP servers** and selecting **Authenticate** when it asks for OAuth sign-in. Follow the docs for your version.

## Sample prompts

- Triggers the skill (make a small uncommitted edit first, for example to `README.md`, so there is a diff): `I changed the README to add a setup section. Write me a commit message.`
- Triggers the MCP server: `Using GitHub, list the 5 most recent open issues in openai/codex.`

The full script is in [docs/demo-script.md](docs/demo-script.md). More background: [docs/overview.md](docs/overview.md), [docs/skill-vs-mcp.md](docs/skill-vs-mcp.md).
