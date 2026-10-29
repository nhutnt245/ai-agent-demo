# Demo script

About 5 minutes. Before you start, finish the setup in `README.md` (token set, `claude` running in the repo root).

## 0. Show the setup (30 seconds)

Show `AGENTS.md`, `.mcp.json` and `.claude/skills/commit-message/SKILL.md`. Point out that there is no agent code.

## 1. Skill prompt

First make a small uncommitted edit so there is a diff to summarize. In another terminal:

```bash
printf '\n## Setup\n\nSee the setup steps above.\n' >> README.md
```

Undo it after the demo with `git checkout README.md`. Then type:

```
I changed the README to add a setup section. Write me a commit message.
```

- **The AI should:** load the `commit-message` skill, check the git diff, and read `references/conventions.md` if needed.
- **Audience sees:** a skill being used, then a message like `docs: add setup section to readme`. No commit is made.

## 2. MCP prompt

Type:

```
Using GitHub, list the 5 most recent open issues in anthropics/claude-code.
```

- **The AI should:** call a GitHub MCP tool (for example, list issues). Claude Code may ask permission first. Approve it.
- **Audience sees:** a tool call to the `github` server, then a short list of real issues from GitHub.

## 3. Both together (optional)

Type:

```
Look at the latest open issue in anthropics/claude-code and write a commit message for a fix titled after it.
```

- **The AI should:** use the MCP server to read the issue, then the skill to format the message.
- **Audience sees:** both pieces working in one answer.

## 4. Wrap up

Say it in one line: the skill taught the AI how, the MCP server gave it access, and the AI chose both on its own.

## If something goes wrong

- Run `claude mcp list`. If `github` is not connected, check `echo $GITHUB_PAT` is set, then restart `claude`.
- Never paste the token on screen.
