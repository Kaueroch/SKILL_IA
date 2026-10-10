---
name: doc-ai
description: Read a codebase and write technical documentation grounded in the actual code — project overview, per-module docs, architecture and data flow, diagrams, and tech debt with improvement suggestions. Use whenever the user asks to document a project, document code, generate docs or a README, map an architecture, explain what a codebase does, or onboard onto an unfamiliar repo, even if they don't say the word "documentation".
---

# doc-ai — Technical Documentation from Code

Turn a codebase into accurate, useful documentation. Every claim must trace back
to something you actually read in the code. Never invent endpoints, files, or
behavior.

## When not to use

- The user only asked a one-off question about a snippet (just answer directly).
- The project already has a spec-driven flow for the change (e.g. an SDD
  `/sdd-08-docs` step) — link the specs instead of duplicating them.

## Workflow

### Phase 1 — Discover (read before you claim)

1. Identify the stack from manifests (`package.json`, `pom.xml`, `go.mod`,
   `requirements.txt`, `docker-compose.yml`, etc.): language, framework,
   database, auth, how it runs.
2. Map the structure: entry points, routers/controllers, services, data layer,
   frontend routes, shared libs. Record real paths.
3. Trace one end-to-end flow (e.g. login, main CRUD) to confirm you understand
   how the layers connect.
4. Note how to run and verify: dev/build/test/lint commands from the repo
   (README, CI config, `AGENTS.md` if present).
5. List what you could NOT determine from the code as open questions — never
   guess to fill a gap.

### Phase 2 — Ask before writing

Always confirm scope with the user before writing files. Ask about:

1. **Destination** — new `docs/` folder, rewrite/extend the README, or both.
   Be specific: which docs, replacing what.
2. **Depth** — pick one:
   - `overview`: purpose, stack, architecture, how to run.
   - `per-module`: overview plus one doc per module (purpose, key flows,
     key files, API/routes).
   - `complete`: everything above plus architecture diagrams (mermaid),
     data model, and mapped tech debt.
3. **Language** — default to the user's language unless they say otherwise.
4. **Improvements** — whether the doc should include a suggested-improvements
   section (default: yes, suggestions only).

One question batch, then write. Do not start Phase 3 on assumptions.

### Phase 3 — Write

- One file per unit: `docs/overview.md`, `docs/<module>.md`, plus
  `docs/README.md` as the index. Keep each file focused; link instead of
  repeating.
- Every doc states purpose first, then how it works, then where (real paths
  with `path:line` references for key functions).
- Diagrams as mermaid code blocks (architecture, request flow, data model).
  Only diagram what you verified in code.
- No placeholders, no `TODO: fill in`. If something is unknown, say so
  explicitly and mark it as an open question.
- Match the repo's voice: plain verbs, sentence case, no filler. Document what
  the code does today, not what it should do.

### Phase 4 — Improvements (suggest, never surprise)

- Improvements live in their own section (`## Suggested improvements`), each
  item with: location, observed problem, why it matters, risk of changing.
- **Never apply code changes without explicit user confirmation.** Documenting
  does not imply permission to refactor. If the user confirms, change the
  smallest scope that fixes the issue and re-verify (Phase 5).
- Do not bundle unrelated refactors with documentation edits.

### Phase 5 — Verify

- Run the repo's own checks (lint/build/tests) after any file change and
  record the exact commands and results in your final summary.
- Fix markdown link targets you created (index ↔ files) before finishing.
- Final message: what was documented, where, what was left open, and (if any)
  improvements applied with evidence.

## Rules

- Evidence before synthesis: read the file before citing it.
- Docs live with the code they describe; update the index when adding files.
- Keep the skill lean: SKILL.md stays under 500 lines; no bundled resources
  until a repeated pattern across runs justifies one.
