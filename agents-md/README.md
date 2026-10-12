# agents-md

Authored skill that writes or updates a repo-level `AGENTS.md` so any coding
agent can build, test, and ship in the project: setup commands, code style,
guardrails, and commit/before/after routines.

## When to use

Use when asking for `AGENTS.md`, repo instructions, agent onboarding,
a contributor guide for AI, or describing repeatable repo workflow —
even without saying the file name. Matches "bootstrap AGENTS.md",
"standardize workflow", "commit rules", "how should agents work here".

## How it works

- The skill reads the repo first (stack, structure, real verify commands).
- You confirm destination (root vs. nested), depth (minimal, standard,
  complete), language, and which routines to encode.
- Output is `AGENTS.md` with only verified commands — unknown commands are
  marked explicitly, never invented.

## Difference from sub-agent-builder

- `sub-agent-builder` creates one reusable subagent (`<name>.md`, `mode: subagent`).
- `agents-md` writes repo rules (`AGENTS.md` at the repo root).

## Structure

```text
agents-md/
├── SKILL.md   # skill instruction (English)
├── README.md  # this file
└── LICENSE    # MIT (repo root)
```

## License

MIT — see `LICENSE` at the repo root.
