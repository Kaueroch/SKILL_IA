---
name: saas-ui
description: Build modern, non-generic SaaS UI with React + TypeScript + Tailwind v4 + shadcn/new-york. Use this whenever the user asks for a landing page, dashboard, app screen, component, layout, pricing section, or says SaaS design, UI, frontend, modern, clean, beautiful — even if they do not say the word design explicitly.
license: MIT
---

# SaaS UI

Build production-quality SaaS interfaces that look designed by a senior product designer, not generated. Default taste is modern SaaS (Linear / Vercel / Stripe caliber): quiet surfaces, one memorable moment per view, real copy, precise spacing.

## When to trigger

Trigger on any of: new page, landing, dashboard, settings screen, auth screen, pricing, onboarding, empty/loading/error state, table, dialog, sidebar, or "make this prettier / modern / like a real SaaS".

If the brief is vague, propose one concrete subject, audience, and primary job in one sentence before building (e.g. "CRM for solo freelancers; audience is non-technical founders; job is convert trial to paid"). Do not build generic placeholder SaaS.

## Stack (do not deviate unless asked)

- React + TypeScript (strict, typed props, no `any` leakage)
- Tailwind CSS v4 (CSS-based `@theme` config, no `tailwind.config.js`)
- shadcn new-york style in `components/ui/`, `cn()` from `lib/utils` for classes
- Icons: `lucide-react` only, no emoji icons
- Fonts: `next/font` (one body + one display with character, clearly distinct). Never ship with system-default-only stack when a display face is warranted.
- No extra UI kits, no gradient-mesh libraries, no animation libraries unless the brief needs them.

File placement:

- Pages/sections: `app/<route>/page.tsx` or co-located section components
- Reusable primitives: `components/ui/<name>.tsx` (shadcn pattern)
- Feature blocks: `components/<feature>/<Block>.tsx`
- One component per file, named exports for blocks, default export only for pages.

## Plan before code (2-pass, mandatory)

Pass 1 — 10-line plan, shown briefly:
1. Subject / audience / job (1 sentence)
2. Color: 4–6 named hex values + role (bg, surface, ink, muted, accent, danger/success only if needed)
3. Type: body face + role, display face + role, scale intent
4. Layout: one-sentence concept + tiny ASCII wireframe; state alignment (left/center) and density
5. The one memorable element (what is bold, everything else quiet)

Self-check the plan: if it would look the same for any other SaaS brief, revise one axis (color, type, or layout) to be subject-specific and state what changed and why. Only then write code.

## Anti-generic rules (SaaS tells to avoid)

Never ship all of these together — they are the AI-SaaS fingerprint:
- Purple-blue gradient hero + identical rounded cards with `rgba(0,0,0,.1)` shadows
- Tracked-out ALL-CAPS eyebrow above every heading
- Accenting a single word in headline with color/italic
- `01 / 02 / 03` numbering for non-sequences; middle-dot meta strings (`A · B · C`); `WORD — fragment` labels; `→` on every button
- Near-black `#0B0B0B` standing in for black without reason; monospace micro-labels everywhere
- Fade-slide-up on every section on scroll

Instead: pick radius intentionally per hierarchy (not one radius everywhere), use borders over shadows for quiet separation, let type do the work, one orchestrated motion moment max. Motion that answers user action (open/expand/confirm) is welcome; decorative scroll choreography is not.

## Quality floor (always)

- Responsive mobile-first (360px works, no horizontal scroll), keyboard focus visible, `prefers-reduced-motion` respected, contrast AA for body text
- Dark mode only when requested: implement via CSS vars + `dark:` variant, never force it
- Real English copy from user perspective, active voice, sentence case. CTA says what happens ("Save changes" → toast "Saved"). Errors explain fix, never apologize vaguely. Empty states invite action.
- Line length < 80ch for prose; no lorem ipsum; no fake charts with random data labeled as real

## Code standards

```tsx
// Example 1 — block component shape
// Input: "pricing section for solo CRM"
// Output shape:
export function PricingSection({ tiers }: { tiers: Tier[] }) {
  return (
    <section className={cn("mx-auto max-w-6xl px-6 py-16")}>
      {/* one hierarchy: headline → proof → tiers → footnote */}
    </section>
  );
}
```

- Typed props with `type Props = {...}`, `cn()` for conditional classes, no inline `<style>` unless CSS vars
- Accessible primitives: use shadcn `Button`, `Dialog`, `DropdownMenu`, `Input`, `Label`, `Table` where they fit instead of hand-rolled divs
- Tailwind v4 tokens via `@theme` in CSS (e.g. `--color-ink`, `--font-display`); avoid arbitrary hex scattered in JSX — reference tokens

## Code review (mandatory before final answer)

Before presenting output, run this checklist and fix failures silently unless trade-off needs user call:
1. Would this be mistaken for another SaaS? If yes, name the one element to change and change it.
2. One radius / one shadow abused everywhere? Vary or remove.
3. All headings same size/weight? Establish display → section → body scale.
4. Buttons/links all with arrows or all-caps? Remove decoration, keep one primary action emphatic.
5. Mobile 360px + keyboard tab order + reduced-motion sane? Fix if not.
6. Copy generic ("Welcome to our platform", "Lorem")? Rewrite specific to brief.

Present result as: files created (paths), how to run/view, design choices (3 bullets max), and one known trade-off or next improvement. Keep prose tight; code is the deliverable.
