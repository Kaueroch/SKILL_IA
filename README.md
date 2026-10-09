# SKILL_IA

Skill autoral para Cursor, Claude Code, Codex, Copilot CLI, Gemini CLI e OpenCode. Você constrói SaaS UI com identidade própria.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Skill

| Skill | Formato | O que faz | Uso |
|---|---|---|---|
| `saas-ui` | pasta `SKILL.md` | Você monta SaaS UI com React + TS + Tailwind v4 + shadcn/new-york. A skill exige plano de 10 linhas e code review antes da resposta | landing, dashboard, settings, auth, pricing, onboarding, tabela, dialog, sidebar |

## Estrutura

```text
SKILL_IA/
├── LICENSE
├── README.md
└── saas-ui/
    ├── SKILL.md
    └── README.md
```

## Instalação por IA

Você instala a skill como pasta com `SKILL.md`.

### Claude Code

Você copia a pasta para as skills do Claude:

```bash
cp -r SKILL_IA/saas-ui ~/.claude/skills/saas-ui
```

Você confere com `/skills` no chat. Você escreve o pedido como no `description` da skill.

### Cursor

Você copia para `.cursor/skills/` na raiz do projeto:

```bash
mkdir -p .cursor/skills
cp -r SKILL_IA/saas-ui .cursor/skills/saas-ui
```

Você abre o chat do Cursor e chama pela intenção da skill.

### OpenAI Codex

Você copia para as skills do Codex:

```bash
mkdir -p ~/.codex/skills
cp -r SKILL_IA/saas-ui ~/.codex/skills/saas-ui
```

Você roda o Codex no projeto e pede como no `description`.

### GitHub Copilot CLI

Você copia para as skills do Copilot:

```bash
mkdir -p ~/.copilot/skills
cp -r SKILL_IA/saas-ui ~/.copilot/skills/saas-ui
```

Você chama `copilot` e descreve a tarefa com as palavras do `Uso` na tabela acima.

### Gemini CLI

Você copia para as skills do Gemini:

```bash
mkdir -p ~/.gemini/skills
cp -r SKILL_IA/saas-ui ~/.gemini/skills/saas-ui
```

Você abre `gemini` no projeto e pede como no `description`.

### OpenCode

Você copia para as skills do OpenCode:

```bash
cp -r SKILL_IA/saas-ui ~/.config/opencode/skills/saas-ui
```

Você usa o nome da skill no prompt. Funciona com "crie um dashboard" ou "deixa essa tela mais moderna".

## Convenções

- Você entrega um resultado por resposta sem lorem.
- Você escreve o plano curto quando a skill pede. `saas-ui` pede 10 linhas e self-check.
- Você testa 360px sem scroll horizontal, mantém foco visível no teclado, respeita `prefers-reduced-motion` e cobra contraste AA no corpo.
- Você escolhe um elemento memorável por tela e mantém o entorno contido.

## Licença

MIT. Você lê os termos em [LICENSE](LICENSE).
