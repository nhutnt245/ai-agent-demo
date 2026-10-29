# Demo script

About 5 minutes, in the Codex desktop app. The repo is https://github.com/nhutnt245/ai-agent-demo.

Note: exact UI labels may differ by app version. Follow the [Codex MCP docs](https://developers.openai.com/codex/mcp) for your version.

## Setup checklist

- [ ] Open the `ai-agent-demo` folder in Codex desktop.
- [ ] Connect the GitHub MCP server from the UI (docs: **Settings > MCP servers**), then select **Authenticate** to sign in with OAuth.
- [ ] On the GitHub authorization screen, authorize **only `ai-agent-demo`**. Do not grant access to any organization.
- [ ] Type `/mcp` in the composer to confirm GitHub is connected. Type `/skills` to confirm `commit-message` is listed.
- [ ] Make a small uncommitted edit so there is a diff: `printf '\n## Setup\n\nSee the setup steps above.\n' >> README.md`. Undo it after the demo with `git checkout README.md`.

## 1. AGENTS.md is read by the agent

Type:

```
What are you allowed to do in this repo, and what must you ask me before doing?
```

- **Codex should:** read `AGENTS.md` and answer from it. No skill or MCP tool is needed.
- **Audience sees:** an answer matching the "What is allowed" and "Ask first" sections of `AGENTS.md`.

## 2. The commit-message skill

Type:

```
I changed the README to add a setup section. Write me a commit message.
```

- **Codex should:** load the `commit-message` skill, check the git diff, and read `references/conventions.md` if needed.
- **Audience sees:** a skill being used, then a message like `docs: add setup section to readme`. No commit is made.

## 3. The GitHub MCP reads this repo

Type:

```
Using GitHub, summarize pull request #1 and list the 5 most recent commits in nhutnt245/ai-agent-demo.
```

- **Codex should:** call GitHub MCP tools on the `github` server (for example, read a PR and list commits). It may ask permission first. Approve it.
- **Audience sees:** tool calls to the `github` server, then a short summary of PR #1 and the recent commits.

Optional, the repo files: `Using GitHub, show me the contents of AGENTS.md in nhutnt245/ai-agent-demo.` Codex reads it through the MCP server, not the local disk.

## 4. Both together (optional)

Type:

```
Read pull request #1 in nhutnt245/ai-agent-demo with GitHub, then write a commit message for a change titled after it.
```

- **Codex should:** use the MCP server to read the PR, then the skill to format the message.
- **Audience sees:** both pieces working in one answer.

## 5. Wrap up

Say it in one line: `AGENTS.md` told the AI the rules, the skill taught it how, the MCP server gave it access, and the AI chose each on its own.

## If something goes wrong

- Type `/mcp` to see connected servers. If GitHub is missing or needs sign-in, connect it again (see `README.md`).
- If the skill is missing, run `/skills`.
