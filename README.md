# SKILL_IA

Coleção de skills autorais para Claude Code e OpenCode — design system, scaffolding, landing pages e SaaS UI sem cara de template.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Claude Code](https://img.shields.io/badge/Claude_Code-.skill-blue)
![OpenCode](https://img.shields.io/badge/OpenCode-SKILL.md-green)

## Skills

| Skill | Formato | O que faz | Quando usar |
|---|---|---|---|
| `saas-ui` | pasta `SKILL.md` | SaaS UI moderna com React + TS + Tailwind v4 + shadcn/new-york, com plan 2-pass, anti-padrões genéricos e code review obrigatório | landing, dashboard, settings, auth, pricing, onboarding, tabela, dialog, sidebar, "deixa mais bonito / moderno" |
| `angular-design-system` | `.skill` | Tokens (cor, espaçamento, tipografia) via CSS vars/SCSS, convenções standalone, estrutura smart/presentational, a11y e responsivo no Angular | componente/página/dashboard Angular, "design system", "style guide", refactor de UI inconsistente |
| `project-bootstrap` | `.skill` | Scaffolding padrão-ouro: Dockerfile por serviço, `docker-compose.yml`, envs, monorepo, CI básico e README inicial, adaptado à stack real | "criar dockerfile", "escrever docker-compose", "estruturar o projeto", subir stack com docker |
| `react-saas-landing-page` | `.skill` | Landing pages React distintas e voltadas a conversão — hero, features, pricing, prova social, FAQ, CTA — anti "AI-generated" | landing/marketing page de SaaS/app, redesign de home, "página pra divulgar meu app" |

## Estrutura

```text
SKILL_IA/
├── LICENSE
├── README.md
├── saas-ui/
│   ├── SKILL.md    # formato OpenCode / Claude Code (pasta)
│   └── README.md
├── angular-design-system.skill
├── project-bootstrap.skill
└── react-saas-landing-page.skill
```

`.skill` = zip com `SKILL.md` + `references/`. Pasta `saas-ui/` já está no formato aberto (mesmo conteúdo, sem zip).

## Como usar

### Claude Code / Claude.ai (arquivo `.skill`)

1. Baixe o `.skill` desejado aqui do repo.
2. Instale via `python -m scripts.package_skill` / upload de skills, ou descompacte e aponte o `skill-path` para a pasta interna (ex.: `angular-design-system/`).
3. Chame pela intenção descrita no frontmatter `description` — ex.: "crie uma landing pro meu app", "estrutura o projeto com docker".

### OpenCode (pasta `SKILL.md`)

```bash
# exemplo: instalar saas-ui no OpenCode
cp -r SKILL_IA/saas-ui ~/.config/opencode/skills/saas-ui
```

Ou aponte o OpenCode direto para `SKILL_IA/saas-ui/SKILL.md`. Para os `.skill`, descompacte primeiro:

```bash
unzip react-saas-landing-page.skill -d /tmp/skills/
cp -r /tmp/skills/react-saas-landing-page ~/.config/opencode/skills/
```

## Convenções das skills

- 1 entregável por resposta, sem placeholder genérico (`lorem`, "Streamline your workflow").
- Plano curto antes do código quando a skill exigir (ex.: `saas-ui` pede plano de 10 linhas + self-check).
- Mobile-first 360px, foco visível no teclado, `prefers-reduced-motion` e contraste AA como piso mínimo.
- Uma ousadia por tela — o resto quieto e disciplinado.

## Licença

MIT — ver [LICENSE](LICENSE).
