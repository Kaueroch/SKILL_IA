---
name: sub-agent-builder
description: Create reusable code subagents from a short purpose description — interview, propose routines, and write a single <agent-name>.md file. Use this whenever the user asks to create an agent, code agent, subagent, reviewer, helper, assistant, bot, criar agente, novo agente, or describes a repeatable coding role, even if they don't say the word agent explicitly.
license: MIT
---

# sub-agent-builder — Code Subagents from Purpose

Turn a one-sentence purpose into a complete, reusable subagent definition.
The user states the purpose; you propose everything else and write one file.

## When not to use

- The user asked a one-off coding question (just answer directly).
- The user wants repo-level rules in `AGENTS.md`, not a reusable role
  (use `agents-md`).
- The user wants project documentation, not a reusable role (use `doc-ai`).
- The user wants UI built, not a role defined (use `saas-ui`).

## Workflow

### Phase 1 — Discover (purpose first, repo second)

1. Extract the purpose from the conversation. If vague, restate it in one
   sentence and ask for confirmation. Never invent a purpose.
2. Inspect the repo lightly: stack from manifests, existing agents
   (`.opencode/agents/`, `.claude/agents`, `AGENTS.md`), how tests/lint run.
   Record real paths. This grounds tool and routine choices.
3. List what you could NOT determine as open questions — never guess.

### Phase 2 — Ask once, then propose

Ask one batch of questions, then write. Do not start Phase 3 on assumptions.

Ask about (skip what the user already answered):

1. **Name** — lowercase, hyphenated (e.g. `code-reviewer`, `debug-helper`).
2. **Trigger** — one sentence: what it does + when it runs.
3. **Powers** — read-only (explore/review) or can edit and run commands.
4. **Scope** — languages, folders, or repos it applies to.
5. **Output language** — default to the user's language.
6. **Destination** — single `<name>.md` file; where it will be installed.

Then propose additions from the Routines catalog below. Frame them as:
"Since you didn't mention X, I suggest Y because Z. Keep it?"
Only include what the user keeps. The user states purpose; you suggest the rest.

### Phase 3 — Write (one file, nothing else)

Write a single `<agent-name>.md` file with this exact shape:

```markdown
---
description: <what it does + when to use, 1-2 sentences>
mode: subagent
permission:
  edit: allow|ask|deny
  bash: allow|ask|deny
---

# <Name>

<Role: who this agent is, in 2-3 sentences. Why it exists.>

## When to use

- <trigger bullet>
- <trigger bullet>

## When NOT to use

- <out-of-scope bullet>

## Workflow

1. <step with reason, not just command>
2. <step>
3. <verify before finishing>

## Guardrails

- <never commit, push, or open PR unless explicitly asked>
- <never skip hooks, never force-push, never edit secrets/config unasked>
- <evidence before synthesis: read the file before citing it>

## Routines (only the ones the user kept)

### Pre-commit

- `git status`, `git diff` — review own changes first
- Run repo checks (lint/build/test) and record exact commands + results
- No secrets, no unrelated refactors bundled in

### Commit message

- Conventional style: `type(scope): short imperative summary`
- One logical change per commit, no empty commits

### Pre-push / done

- Re-read the diff from the base branch, confirm scope
- Final summary: files changed (with `path:line`), checks run + results,
  what was left open

## Output format

<State exactly what the agent returns: files changed, how to verify,
one known trade-off or next step. Keep prose tight.>
```

Rules for the file:

- Frontmatter needs `description` (always in English, 1-2 sentences, so
  trigger matching works) and `mode: subagent`. Always write `permission`
  with both `edit` and `bash` explicit so the powers are obvious.
  Mapping: read-only/review means `edit: deny`; keep `bash: allow` when the
  agent must run read-only checks (`git diff`, lint, tests), otherwise `ask`
  or `deny`. Keep temperature/model out unless the user asked for one.
- Headings stay in English (`## When to use`, `## Guardrails`, ...); body
  content follows the user's output language. Never translate headings.
- `## Routines` holds one `### <name>` per kept routine only — drop the
  rest, do not leave empty sections. Use the catalog names (`Repo grounding`,
  `Smallest diff`, ...) or the commit trio (`Pre-commit`, `Commit message`,
  `Pre-push / done`) as headings; fold trivially small routines into
  Workflow instead of creating a one-line section.
- If the repo has no manifests, test runner, or agent folder, say so
  explicitly in the agent file ("detect via `package.json` in the target
  repo") instead of guessing commands. Never invent a command as the default.
- Body stays focused: role, triggers, workflow, guardrails, kept routines,
  output format. Explain the why behind each rule in one clause so the
  agent can generalize beyond examples.
- No placeholders, no `TODO`. If something is unknown, say so explicitly.
- One file per agent. Never bundle two agents in one response.

### Install map (tell the user where the file goes)

- OpenCode: `~/.config/opencode/agents/<name>.md` (global) or
  `.opencode/agents/<name>.md` (project). Invoke with `@<name>`.
- Claude Code: `~/.claude/agents/<name>.md` (same frontmatter shape).
- Cursor / Codex / Copilot / Gemini: reuse the same markdown as a custom
  agent or project instruction file; follow that tool's custom-agent path,
  content stays identical.

## Routines catalog (suggest, never impose)

Offer these only when relevant to the purpose. Each suggestion needs a why:

- **Read-before-claim**: inspect `git status`, `git diff`, `git log --oneline -10`
  before acting. Why: prevents editing the wrong files.
- **Repo grounding**: check manifests, `AGENTS.md`, CI config for stack and
  commands. Why: routines must match how this repo actually runs.
- **Pre-commit check**: lint + build + targeted tests pass. Why: catches
  breakage before it spreads.
- **Message rule**: conventional commit, imperative, scoped. Why: history
  stays searchable.
- **No-surprise pushes**: never `commit`, `push`, `--force`, or open PR
  unless explicitly requested. Why: destructive actions need consent.
- **Post-task evidence**: report exact commands run and their results.
  Why: claims without evidence erode trust.
- **Smallest diff**: fix the smallest scope that solves it; separate
  refactors. Why: reviewable changes ship faster.

## Phase 4 — Verify

- Show the file path and full content (or diff if updating an existing agent).
- State how to invoke it (`@<name>` in OpenCode / Claude) and one example prompt.
- Record which routines were kept vs. dropped and why.
- Keep the skill lean: SKILL.md stays under 500 lines; no bundled resources
  until a repeated pattern across runs justifies one.
