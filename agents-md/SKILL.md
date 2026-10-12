---
name: agents-md
description: Write or update a repo-level AGENTS.md that tells any coding agent how to build, test, and ship in this project — setup commands, code style, guardrails, and commit/before/after routines. Use this whenever the user asks for AGENTS.md, repo instructions, agent onboarding, contributor guide for AI, or says bootstrapping, standardize workflow, commit rules, even if they don't say the file name explicitly.
license: MIT
---

# agents-md — Repo Instructions for Coding Agents

Write one `AGENTS.md` at the repo root (plus nested ones for monorepos)
so any coding agent can build, test, and ship without guessing.
This skill writes repo rules, not reusable subagents (that is `sub-agent-builder`).

## When not to use

- The user wants a reusable role across repos (use `sub-agent-builder`).
- The user asked a one-off coding question (just answer directly).
- The user wants project documentation for humans (use `doc-ai`).

## Workflow

### Phase 1 — Discover (read before you claim)

1. Identify the stack from manifests (`package.json`, `pom.xml`, `go.mod`,
   `requirements.txt`, `docker-compose.yml`, CI config): language, framework,
   database, auth, how it runs.
2. Map the structure: entry points, routers/controllers, services, data layer,
   frontend routes, shared libs. Record real paths.
3. Find how to verify: install, dev, build, test, lint commands from the repo
   (README, CI, existing `AGENTS.md`/`CLAUDE.md` if present).
4. Check for existing `AGENTS.md` files (root + nested). If one exists, update
   it in place instead of rewriting from scratch.
5. List what you could NOT determine as open questions — never guess a command.

### Phase 2 — Ask once, then propose

Ask one batch, then write. Do not start Phase 3 on assumptions.

Ask about (skip what the user already answered):

1. **Destination** — root `AGENTS.md`, nested `packages/<name>/AGENTS.md`,
   or both. Default: root only.
2. **Depth** — pick one: `minimal` (setup + verify + guardrails),
   `standard` (plus code style + testing + commit routines),
   `complete` (plus architecture map, security notes, PR instructions).
3. **Language** — default to the user's language for body text; keep commands
   and paths verbatim.
4. **Routines** — confirm which commit/before/after routines to encode
   (see catalog). Only include what the user keeps.

Then propose additions from the Routines catalog. Frame them as:
"Since you didn't mention X, I suggest Y because Z. Keep it?"

### Phase 3 — Write (AGENTS.md, nothing else)

Write `AGENTS.md` with this shape. Keep `minimal` to Setup + Verify +
Guardrails; add sections as depth grows:

```markdown
# AGENTS.md

## Project overview

<1-3 sentences: what this repo is, stack, who it serves.>

## Setup commands

- Install deps: `<real command>`
- Start dev: `<real command>`
- Build: `<real command>`

## Code style

- <verified convention, e.g. TypeScript strict, single quotes>
- <where shared primitives live: real paths>

## Testing instructions

- Run checks: `<real command, e.g. pnpm test>`
- Focus one test: `<real command with pattern>`
- Fix failures until green before finishing.

## Guardrails

- Never `commit`, `push`, `--force`, or open a PR unless explicitly asked.
- Never skip hooks (`--no-verify`), never edit secrets/config unasked.
- Evidence before synthesis: read the file before citing it.

## Commit routines (only the ones the user kept)

- Pre-commit: `git status`, `git diff`; run lint/build/targeted tests;
  record exact commands + results. No secrets, no bundled refactors.
- Message: `type(scope): short imperative summary`. One logical change
  per commit, no empty commits.
- Done: re-read the diff from the base branch; report files changed
  (`path:line`), checks run + results, what was left open.

## PR instructions (only if depth is complete or user kept it)

- Title format: `<real convention or state none>`
- Always run lint + tests before committing.
```

Rules for the file:

- Every command must be one you found in the repo (manifest, README, CI).
  If a command is unknown, write "detect in target repo" explicitly instead
  of inventing one. Never invent build/test commands as defaults.
- User claims are not verification: if the user says "we use pytest" but the
  repo shows no evidence, write "unverified per user request: `<command>` —
  confirm against manifest/CI" rather than stating it as fact or silently
  dropping it.
- Depth maps to sections: `minimal` = Project overview + Setup commands +
  Testing instructions + Guardrails (no Commit/PR sections even if a kept
  routine overlaps — fold it into Guardrails as one line). `standard` adds
  Code style + Commit routines. `complete` adds architecture/security notes +
  PR instructions.
- Keep it scannable: short bullets, real paths with `path:line` where they
  matter, no prose essays. Explain the why in one clause per rule so agents
  generalize beyond examples.
- No placeholders, no `TODO`. If something is unknown, say so explicitly.
- One `AGENTS.md` per response unless the user confirmed nested files.
  For monorepos, the closest `AGENTS.md` to the edited file wins — keep
  shared rules at the root, package specifics nested.
- Treat it as living documentation: updating beats rewriting.

### Placement (tell the user where the file goes)

- Standard: `<repo-root>/AGENTS.md` — works across OpenCode, Claude Code,
  Cursor, Codex, Copilot, Gemini, and 60k+ repos using the open format.
- Monorepo: add `<package-dir>/AGENTS.md` for package-specific rules.
- Symlink only if the user asks (`AGENT.md`/`CLAUDE.md` compat).

## Routines catalog (suggest, never impose)

Offer only what fits the repo. Each suggestion needs a why:

- **Setup first**: install + dev + build commands up top. Why: agents fail
  without a working baseline.
- **Verify loop**: lint + build + targeted tests before finishing. Why:
  catches breakage before it spreads.
- **Read-before-claim**: `git status`, `git diff`, `git log --oneline -10`
  before editing. Why: prevents touching the wrong files.
- **Message rule**: conventional commit, imperative, scoped. Why: history
  stays searchable.
- **No-surprise pushes**: never commit/push/PR unasked. Why: destructive
  actions need consent.
- **Post-task evidence**: report exact commands + results. Why: claims
  without evidence erode trust.
- **Smallest diff**: smallest scope that fixes it; separate refactors. Why:
  reviewable changes ship faster.

## Phase 4 — Verify

- Show the file path and full content (or diff if updating).
- Run the repo's own checks after writing (lint/build/tests) and record the
  exact commands and results in your final summary. If the repo has no
  checks (e.g. a markdown-only repo), that IS the result: report
  `git status --short` plus "no lint/build/tests found" instead of
  improvising verification.
- State which routines were kept vs. dropped and why.
- Keep the skill lean: SKILL.md stays under 500 lines; no bundled resources
  until a repeated pattern across runs justifies one.
