# SKILL_IA

Coleção autoral de skills para agentes de código: você instala como pasta com `SKILL.md` e o agente assume a especialidade.

[![Live site](https://img.shields.io/badge/site-ao_vivo-brightgreen)](https://kaueroch.github.io/SKILL_IA/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **Instalação visual:** escolha a skill, escolha a sua IA e copie o comando em
> [kaueroch.github.io/SKILL_IA](https://kaueroch.github.io/SKILL_IA/).
> A página também mostra o passo a passo manual num terminal animado, ferramenta por ferramenta.

## Skills

| Skill | O que faz | Uso |
|---|---|---|
| `saas-ui` | Você monta SaaS UI com React + TS + Tailwind v4 + shadcn/new-york. A skill exige plano de 10 linhas e code review antes da resposta | landing, dashboard, settings, auth, pricing, onboarding, tabela, dialog, sidebar |
| `doc-ai` | Você documenta um projeto a partir do código: visão geral, módulos, diagramas e dívidas técnicas, com melhorias só como sugestão | documentar projeto, gerar docs, README, arquitetura, features futuras |

## Estrutura

```text
SKILL_IA/
├── LICENSE
├── README.md
├── docs/            # site estático (GitHub Pages): index.html único, sem build
├── saas-ui/
│   ├── SKILL.md
│   └── README.md
└── doc-ai/
    ├── SKILL.md
    └── README.md
```

## Instalação

Nos exemplos abaixo, troque `saas-ui` pelo nome da skill que você quer (`saas-ui`, `doc-ai`).
Rode a partir da pasta ao lado do repo clonado. Depois de instalar, reinicie o terminal da sua IA.

<details>
<summary><strong>Claude Code</strong> — <code>~/.claude/skills/</code></summary>

```bash
cp -r SKILL_IA/saas-ui ~/.claude/skills/saas-ui
```

Você confere com `/skills` no chat. Você escreve o pedido como no `description` da skill.

</details>

<details>
<summary><strong>Cursor</strong> — <code>.cursor/skills/</code> na raiz do projeto</summary>

```bash
mkdir -p .cursor/skills
cp -r SKILL_IA/saas-ui .cursor/skills/saas-ui
```

Você abre o chat do Cursor e chama pela intenção da skill.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <code>~/.codex/skills/</code></summary>

```bash
mkdir -p ~/.codex/skills
cp -r SKILL_IA/saas-ui ~/.codex/skills/saas-ui
```

Você roda o Codex no projeto e pede como no `description`.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <code>~/.copilot/skills/</code></summary>

```bash
mkdir -p ~/.copilot/skills
cp -r SKILL_IA/saas-ui ~/.copilot/skills/saas-ui
```

Você chama `copilot` e descreve a tarefa com as palavras do `Uso` na tabela acima.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <code>~/.gemini/skills/</code></summary>

```bash
mkdir -p ~/.gemini/skills
cp -r SKILL_IA/saas-ui ~/.gemini/skills/saas-ui
```

Você abre `gemini` no projeto e pede como no `description`.

</details>

<details>
<summary><strong>OpenCode</strong> — <code>~/.config/opencode/skills/</code></summary>

```bash
mkdir -p ~/.config/opencode/skills
cp -r SKILL_IA/saas-ui ~/.config/opencode/skills/saas-ui
```

Você usa o nome da skill no prompt. Funciona com "crie um dashboard" ou "deixa essa tela mais moderna".

</details>

## Site (GitHub Pages)

O site vive em `docs/index.html`: um arquivo estático, sem dependências nem build.
Para publicar: Settings → Pages → Deploy from branch → branch `main`, pasta `docs`.

## Convenções

- Você entrega um resultado por resposta sem lorem.
- Você escreve o plano curto quando a skill pede. `saas-ui` pede 10 linhas e self-check.
- Você testa 360px sem scroll horizontal, mantém foco visível no teclado, respeita `prefers-reduced-motion` e cobra contraste AA no corpo.
- Você escolhe um elemento memorável por tela e mantém o entorno contido.

## Licença

MIT. Você lê os termos em [LICENSE](LICENSE).
