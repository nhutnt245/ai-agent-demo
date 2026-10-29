# Overview

## What this repo is

A small, text-only repo used for a live demo about AI agents, skills and MCP.
It has no application code and no dependencies.

## The idea

The AI tool (OpenAI Codex) is the agent. It reads `AGENTS.md`, decides what to do from your prompt, and calls tools on its own.
This repo gives it two things to use:

- a **skill** (`.agents/skills/commit-message/`): instructions for writing commit messages;
- an **MCP server** (GitHub, connected in the Codex UI): a way to read data from GitHub.

## Purpose of the demo

Show the audience that:

1. You prompt in plain language, and the AI picks the right skill or tool.
2. A skill teaches the AI *how* to do a task.
3. An MCP server gives the AI *access* to an outside service.

## Where to go next

- Setup and prompts: `README.md`
- Skill vs MCP: `skill-vs-mcp.md`
- Live script: `demo-script.md`
