# Demo script

About 5 minutes, in the Codex desktop app. The repo is https://github.com/nhutnt245/ai-agent-demo.

Note: labels can differ by Codex app version. This script is path A (GitHub plugin). Path B (hand-configured GitHub MCP server) is at the end.

## Setup checklist

- [ ] Open the `ai-agent-demo` folder in Codex desktop.
- [ ] Open Plugins in Codex and choose GitHub. Sign in if it is not already logged in, then click **Try now**. You can also put the GitHub tag in the chat box and run the sample prompts there.
- [ ] If sign-in lets you choose repository access, authorize **only `ai-agent-demo`**. Do not grant access to any organization.
- [ ] Type `/skills` to confirm `commit-message` is listed. `/mcp` lists only MCP servers configured by hand; the GitHub plugin is separate and does not appear there, so a missing GitHub entry is normal.
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

## 3. The GitHub plugin reads this repo

Type:

```
Using GitHub, summarize pull request #1 and list the 5 most recent commits in https://github.com/nhutnt245/ai-agent-demo.
```

- **Codex should:** use the GitHub integration to read a PR and list commits. It may ask permission first. Approve it.
- **Audience sees:** GitHub tool use, then a short summary of PR #1 and the recent commits.

Optional, the repo files: `Using GitHub, show me the contents of AGENTS.md in https://github.com/nhutnt245/ai-agent-demo.` Codex reads it through the GitHub integration, not the local disk.

## 4. Both together (optional)

Type:

```
Read pull request #1 in https://github.com/nhutnt245/ai-agent-demo with GitHub, then write a commit message for a change titled after it.
```

- **Codex should:** use the GitHub integration to read the PR, then the skill to format the message.
- **Audience sees:** both pieces working in one answer.

## 5. Wrap up

Say it in one line: `AGENTS.md` told the AI the rules, the skill taught it how, the GitHub plugin gave it access (path A), and the AI chose each on its own.

## If something goes wrong

- Open Plugins in Codex and choose GitHub if it needs to be selected or signed in again (see `README.md`). The GitHub plugin does not appear in `/mcp`, which lists only manually configured MCP servers.
- If the skill is missing, run `/skills`.

## Path B: hand-configured GitHub MCP server (optional)

Use this to show a real MCP server in `/mcp`. It is separate from the GitHub plugin in path A. Docs: [Codex MCP](https://developers.openai.com/codex/mcp), [GitHub MCP server for Codex](https://github.com/github/github-mcp-server/blob/main/docs/installation-guides/install-codex.md).

1. Create a fine-grained personal access token limited to **only** `ai-agent-demo`, with read-only **Contents** and **Pull requests** (metadata read access is automatic).
2. Export it in your shell as `GITHUB_PAT`. Never put the token in a repo file, config snippet or prompt.
3. Add the server (endpoint `https://api.githubcopilot.com/mcp/`):

   ```
   codex mcp add github --url https://api.githubcopilot.com/mcp/ --bearer-token-env-var GITHUB_PAT
   ```

   Or in `~/.codex/config.toml`, which holds only the variable name, not the token:

   ```toml
   [mcp_servers.github]
   url = "https://api.githubcopilot.com/mcp/"
   bearer_token_env_var = "GITHUB_PAT"
   ```

4. Run `codex mcp list`, then restart Codex and type `/mcp`. `github` should appear.
5. Run the prompts from step 3 above, still aimed at https://github.com/nhutnt245/ai-agent-demo.

OAuth note: the GitHub remote server does not support Dynamic Client Registration, so OAuth needs a pre-registered client. Plain `codex mcp login` does not work automatically; use the token above.
