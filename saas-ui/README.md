# saas-ui

You hand your agent a SaaS brief and you receive production UI code with React + TypeScript + Tailwind v4 + shadcn/new-york.

## Use cases

You launch a landing page for a defined audience with one job to do.
Prompt: `Build a landing page for a solo CRM. Audience is non-technical founders. Job is convert trial to paid.`

You replace placeholder cards with real hierarchy.
Prompt: `Rebuild this dashboard with quiet surfaces and one bold moment. Keep existing routes.`

You ship app screens with shared tokens.
Prompt: `Build a pricing section with 3 tiers plus monthly/yearly toggle for the solo CRM.`

You fix a screen that looks AI-generated.
Prompt: `Make this settings screen look like Linear. Remove gradient hero and numbered gimmicks.`

## How you work

You describe subject, audience, and job in one sentence. You approve a 10-line plan covering color, type, layout, and the one memorable element. You receive code, file paths, run steps, design choices in 3 bullets, and one trade-off.

The plan includes a self-check. You see what changed when the first draft looks interchangeable with any other SaaS.

## Output

You receive blocks in `components/<feature>/<Block>.tsx` and pages in `app/<route>/page.tsx`. Primitives live in `components/ui/` with `cn()` from `lib/utils`. Tokens live in CSS through `@theme`, not scattered hex. Icons come from `lucide-react`. Type uses `next/font` with one body face plus one distinct display face.

You receive accessible defaults: 360px with no sideways scroll, visible keyboard focus, `prefers-reduced-motion` respected, AA contrast for body text. Dark mode ships when you request it, through CSS vars plus `dark:` variant.

## When not to use

You need repo rules for agents. You use `agents-md`.
You need a reusable reviewer role. You use `sub-agent-builder`.
You need docs from code. You use `doc-ai`.

## Stack

- React + TypeScript strict, typed props, no `any` leakage
- Tailwind CSS v4 with `@theme`, no `tailwind.config.js`
- shadcn new-york in `components/ui/`
- `lucide-react` for icons, no emoji icons
- `next/font` for type

## Structure

```text
saas-ui/
├── SKILL.md   # skill instruction
├── README.md  # this file
└── LICENSE    # MIT (repo root)
```

## Install

Copy the folder to your tool, then prompt with the use cases above. Full paths live in the repo root README.

```bash
cp -r SKILL_IA/saas-ui ~/.claude/skills/saas-ui
```

## License

MIT. See `LICENSE` at the repo root.
