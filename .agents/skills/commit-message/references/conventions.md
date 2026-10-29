# Commit message conventions

## Format

```
type: short summary

Optional body: what changed and why.
```

## Types

| Type | Use for |
| --- | --- |
| `feat` | A new feature or demo piece |
| `fix` | A bug or mistake fixed |
| `docs` | Documentation only |
| `chore` | Config, tooling, housekeeping |
| `refactor` | Restructure with no behavior change |

## Rules

- Summary line: imperative mood ("add", not "added"), lowercase, at most 50 characters, no final period.
- Blank line between summary and body.
- Body lines wrap at 72 characters. Explain why, not only what.
- One logical change per commit.
- Never put secrets, tokens or personal data in a message.

## Examples

- `docs: add skill vs mcp comparison`
- `fix: correct env var name in readme`
- `chore: add github mcp server config`
