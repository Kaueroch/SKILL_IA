# agents-md

You point at a repo and you receive an `AGENTS.md` that tells any coding agent how to build, test, and ship there. Every command comes from files you can open.

## Use cases

You onboard agents to a repo without guesswork.
Prompt: `Generate a standard AGENTS.md for this repo. Verify commands against package.json and CI.`

You inherit a repo with no instructions.
Prompt: `Write a minimal AGENTS.md with setup, verify, and guardrails. Mark unknowns explicitly.`

You standardize commit routines across a team.
Prompt: `Add commit routines with conventional messages, pre-commit checks, and post-task evidence.`

You run a monorepo with package-specific rules.
Prompt: `Write root AGENTS.md plus packages/billing/AGENTS.md with local test commands.`

## How you work

You confirm destination, depth, language, and routines. Destinations include root `AGENTS.md`, nested `packages/<name>/AGENTS.md`, or both.

You answer one batch. You receive `AGENTS.md` with verified commands only. Unknown commands read `detect in target repo`, never a guess. User claims without repo evidence read `unverified per user request`, never a fact.

Depths map to sections. `minimal` covers overview plus setup plus testing plus guardrails. `standard` adds code style plus commit routines. `complete` adds architecture notes plus security notes plus PR instructions.

## Output shape

```markdown
# AGENTS.md
## Project overview
## Setup commands
## Code style
## Testing instructions
## Guardrails
## Commit routines
## PR instructions
```

You place the file at `<repo-root>/AGENTS.md`. It works across OpenCode, Claude Code, Cursor, Codex, Copilot, and Gemini. Closest `AGENTS.md` wins for monorepos: shared rules at root, package specifics nested.

## Difference from sub-agent-builder

You need one reusable role across repos. You use `sub-agent-builder` and you receive `<name>.md` with `mode: subagent`.
You need rules for one repo. You use this skill and you receive `AGENTS.md` at the repo root.

## When not to use

You ask a one-off coding question. You ask directly.
You need a reusable role. You use `sub-agent-builder`.
You need human docs. You use `doc-ai`.

## Structure

```text
agents-md/
├── SKILL.md   # skill instruction
├── README.md  # this file
└── LICENSE    # MIT (repo root)
```

## Install

Copy the folder to your tool, then prompt with the use cases above. Full paths live in the repo root README.

```bash
cp -r SKILL_IA/agents-md ~/.claude/skills/agents-md
```

## License

MIT. See `LICENSE` at the repo root.
