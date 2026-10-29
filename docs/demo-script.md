# Demo script

About 5 minutes. Before you start, finish the setup in `README.md` (Codex open on this repo, GitHub connected in the Codex UI).

## 0. Show the setup (30 seconds)

Show `AGENTS.md`, `.agents/skills/commit-message/SKILL.md`. Say that GitHub is connected in the Codex UI, with no token in the repo. Point out that there is no agent code.

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
Using GitHub, list the 5 most recent open issues in openai/codex.
```

- **The AI should:** call a GitHub MCP tool (for example, list issues). Codex may ask permission first. Approve it.
- **Audience sees:** a tool call to the `github` server, then a short list of real issues from GitHub.

## 3. Both together (optional)

Type:

```
Look at the latest open issue in openai/codex and write a commit message for a fix titled after it.
```

- **The AI should:** use the MCP server to read the issue, then the skill to format the message.
- **Audience sees:** both pieces working in one answer.

## 4. Wrap up

Say it in one line: the skill taught the AI how, the MCP server gave it access, and the AI chose both on its own.

## If something goes wrong

- Type `/mcp` in the Codex composer to see connected servers. If GitHub is missing or needs sign-in, connect it again (see `README.md`).
- If the skill is missing, run `/skills`.
