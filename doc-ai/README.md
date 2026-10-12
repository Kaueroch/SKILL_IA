# doc-ai

You point at a codebase and you receive technical docs grounded in files you actually read. No invented endpoints. No invented behavior.

## Use cases

You join an unfamiliar repo and need a map fast.
Prompt: `Document this repo at overview level in docs/overview.md. Include stack, entry points, and run commands.`

You prepare handoff with per-module detail.
Prompt: `Write per-module docs for auth and billing. Include purpose, key flows, key files with path:line refs.`

You review architecture before a refactor.
Prompt: `Map request flow plus data model with mermaid diagrams. Mark unknowns as open questions.`

You onboard a new hire.
Prompt: `Write complete docs with overview, per-module pages, diagrams, and tech debt with risks.`

## How you work

You confirm destination, depth, language, and whether you want suggestions. Destinations include new `docs/` folder, README rewrite, or both. Depths include `overview`, `per-module`, `complete`.

You answer one batch of questions. You receive one file per unit: `docs/overview.md`, `docs/<module>.md`, plus `docs/README.md` as index. Each file states purpose first, then behavior, then locations with `path:line` refs. Diagrams use mermaid and cover code you verified.

You receive improvements in a separate section with location, observed problem, impact, and risk. You approve before any code change happens. Docs never trigger a refactor by surprise.

## Depths

- `overview`: purpose, stack, architecture, run commands
- `per-module`: overview plus one doc per module with routes and key files
- `complete`: all above plus diagrams, data model, mapped tech debt

## When not to use

You ask a one-off question about a snippet. You ask directly, no skill needed.
You follow a spec-driven flow with an `/sdd-08-docs` step. You link the specs.
You need repo rules for agents. You use `agents-md`.
You need UI code. You use `saas-ui`.

## Rules

- You trace every claim to a file you read.
- You write no placeholders, no `TODO: fill in`. You mark gaps as open questions.
- You keep SKILL.md under 500 lines with no bundled resources until a repeated pattern earns one.

## Structure

```text
doc-ai/
├── SKILL.md   # skill instruction
├── README.md  # this file
└── LICENSE    # MIT (repo root)
```

## Install

Copy the folder to your tool, then prompt with the use cases above. Full paths live in the repo root README.

```bash
cp -r SKILL_IA/doc-ai ~/.claude/skills/doc-ai
```

## License

MIT. See `LICENSE` at the repo root.
