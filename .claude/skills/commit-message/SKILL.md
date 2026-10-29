---
name: commit-message
description: Write a commit message in this repo's convention. Use when the user asks for a commit message, or to describe, summarize or commit staged or recent changes.
---

# commit-message

1. Look at the change: run `git diff --staged` (or `git diff` if nothing is staged).
2. Write one commit message: `type: short summary`, then an optional body.
3. Show the message to the user. Do not run `git commit` unless asked.

Quick rules:

- Types: `feat`, `fix`, `docs`, `chore`, `refactor`.
- Summary is imperative, lowercase, at most 50 characters, no final period.
- Never include secrets or tokens.

For the full rules and examples, read [references/conventions.md](references/conventions.md) only if you need them.
