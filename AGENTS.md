# AGENTS.md

Shared guide for any AI agent working in this repo.

## What this repo is

A small demo about AI agents, skills and MCP. It has no application code.
The AI tool you run is the agent. This repo only gives it a skill and an MCP server to use.
See `docs/overview.md`.

## Folder map

- `README.md`: setup and sample prompts for humans.
- `.codex/config.toml`: Codex config for the GitHub MCP server (remote, token from `GITHUB_PAT`).
- `.agents/skills/commit-message/`: skill that writes commit messages. Details in `references/conventions.md`.
- `docs/`: `overview.md`, `skill-vs-mcp.md`, `demo-script.md`.

## What is allowed

- Read any file. Edit text and config files in this repo.
- Use the `commit-message` skill when asked for a commit message.
- Use the GitHub MCP server for read-only questions (repos, issues, PRs).

## Ask first

Ask the user before you:

- create, edit or close anything on GitHub (issues, PRs, comments);
- push, merge, force-push or delete branches;
- delete files, or change anything outside this repo.

## Secrets

Never commit secrets. The GitHub token lives only in the `GITHUB_PAT` environment variable.
Do not write it into any file, prompt or commit message.

## Maintaining this file

Keep this file for knowledge useful to almost every future agent session in this project.
Do not repeat what the codebase already shows; point to the authoritative file or command instead.
Prefer rewriting or pruning existing entries over appending new ones.
When updating this file, preserve this bar for all agents and keep entries concise.
