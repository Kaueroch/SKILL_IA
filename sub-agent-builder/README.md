# sub-agent-builder

Authored skill that turns a short purpose into a reusable code subagent:
interview, propose routines, and write a single `<name>.md`.

## When to use

Use when asking to create an agent, code agent, subagent, reviewer,
helper, bot, or describing a repeatable coding role — even without saying
the word "agent". Matches "create agent", "new agent", "code reviewer".

## How it works

- You state the purpose; the skill proposes the rest (name, triggers,
  permissions, scope, commit/before/after routines).
- Output is a single `<name>.md` file with frontmatter (`description`,
  `mode: subagent`, `permission`) + body (role, when to use, workflow,
  guardrails, kept routines, output format).
- The skill always asks one batch of questions before writing and only
  includes routines you keep.

## Structure

```text
sub-agent-builder/
├── SKILL.md   # skill instruction (English)
├── README.md  # this file
└── LICENSE    # MIT (repo root)
```

## License

MIT — see `LICENSE` at the repo root.
