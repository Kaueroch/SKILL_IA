# sub-agent-builder

You describe a repeatable coding role in one sentence and you receive a single reusable subagent file.

## Use cases

You repeat the same PR checklist and want it encoded.
Prompt: `Create a read-only code-reviewer for TypeScript PRs. It checks diff scope, tests, and naming.`

You debug the same stack every week.
Prompt: `Create a debug-helper for Node APIs. It reads logs, reproduces with tests, and reports evidence.`

You enforce commit standards across repos.
Prompt: `Create a commit-helper that writes conventional commits and blocks secrets.`

You support a specific folder or language.
Prompt: `Create a migration-helper scoped to packages/billing. It touches SQL plus Drizzle code.`

## How you work

You state purpose in one sentence. You answer one batch: name, trigger, powers, scope, output language, destination. You keep routines you want and drop the rest.

You receive one `<name>.md` file with frontmatter plus role, triggers, workflow, guardrails, kept routines, and output format. Headings stay in English. Body follows your output language.

Powers stay explicit. Read-only review uses `edit: deny` with `bash: allow` for checks like `git diff` and tests. Editing roles use `edit: allow` or `ask`.

## Output shape

```markdown
---
description: <what it does + when to use, 1-2 sentences>
mode: subagent
permission:
  edit: allow|ask|deny
  bash: allow|ask|deny
---

# <Name>
## When to use
## When NOT to use
## Workflow
## Guardrails
## Routines
## Output format
```

You invoke with `@<name>` in OpenCode and Claude Code. You reuse the same markdown as custom agent file in Cursor, Codex, Copilot, and Gemini.

## When not to use

You ask a one-off coding question. You ask directly, no agent file needed.
You need repo-level rules in `AGENTS.md`. You use `agents-md`.
You need project docs. You use `doc-ai`.
You need UI built. You use `saas-ui`.

## Structure

```text
sub-agent-builder/
├── SKILL.md   # skill instruction
├── README.md  # this file
└── LICENSE    # MIT (repo root)
```

## Install

Copy the folder to your tool, then prompt with the use cases above. Full paths live in the repo root README.

```bash
cp -r SKILL_IA/sub-agent-builder ~/.claude/skills/sub-agent-builder
```

## License

MIT. See `LICENSE` at the repo root.
