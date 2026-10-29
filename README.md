# AI agent demo: skills and MCP

A tiny repo for a live demo. You prompt an AI tool (OpenAI Codex).
The AI then uses a **skill** and the **GitHub plugin** by itself. There is no custom agent code.

- Skill: `commit-message` writes a commit message in this repo's style.
- GitHub plugin: connects the AI to GitHub so it can read data from this repo.

## Setup (5 minutes)

1. Install [Codex](https://developers.openai.com/codex) and open this repo in it.
2. Open Plugins in Codex and choose GitHub. Sign in if it is not already logged in, then click **Try now**. You can also put the GitHub tag in the chat box and run the sample prompts there.
3. If sign-in lets you choose repository access, authorize **only the `ai-agent-demo` repo**. Do not grant access to any organization.
4. Type `/skills` to check the skill. `/mcp` lists servers configured by hand; the GitHub plugin is a separate integration, so an empty `/mcp` list is normal.

No personal access token is used, and nothing secret is stored in this repo.

Note: labels can differ by Codex app version. See [OpenAI's plugin guide](https://help.openai.com/en/articles/20001256-plugins-in-chatgpt) for current plugin guidance.

## Sample prompts

- Triggers the skill (make a small uncommitted edit first, for example to `README.md`, so there is a diff): `I changed the README to add a setup section. Write me a commit message.`
- Triggers the GitHub integration: `Using GitHub, summarize pull request #1 and list the 5 most recent commits in https://github.com/nhutnt245/ai-agent-demo.`

The full script is in [docs/demo-script.md](docs/demo-script.md). More background: [docs/overview.md](docs/overview.md), [docs/skill-vs-mcp.md](docs/skill-vs-mcp.md).
