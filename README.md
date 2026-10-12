# SKILL_IA

Coleção autoral de skills para agentes de código. Você instala como pasta com `SKILL.md` e o agente assume a especialidade.

[![Site](https://img.shields.io/badge/site-ao_vivo-brightgreen)](https://kaueroch.github.io/SKILL_IA/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> Prefere clicar? Escolha a skill e a ferramenta no [site](https://kaueroch.github.io/SKILL_IA/) e copie o comando.
> O site mostra o passo manual num terminal animado, ferramenta por ferramenta.

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
├── docs/            # site estático: index.html único, sem build
├── saas-ui/
│   ├── SKILL.md
│   └── README.md
└── doc-ai/
    ├── SKILL.md
    └── README.md
```

## Instalação

Troque `saas-ui` pelo nome da skill (`saas-ui`, `doc-ai`).
Rode da pasta ao lado do repo clonado. Reinicie o terminal da IA depois de instalar.

<details>
<summary><strong>Claude Code</strong> <code>~/.claude/skills/</code></summary>

```bash
cp -r SKILL_IA/saas-ui ~/.claude/skills/saas-ui
```

Confira com `/skills` no chat e peça com as palavras do `description`.

</details>

<details>
<summary><strong>Cursor</strong> <code>.cursor/skills/</code> na raiz do projeto</summary>

```bash
mkdir -p .cursor/skills
cp -r SKILL_IA/saas-ui .cursor/skills/saas-ui
```

Abra o chat do Cursor no projeto e chame pela intenção da skill.

</details>

<details>
<summary><strong>OpenAI Codex</strong> <code>~/.codex/skills/</code></summary>

```bash
mkdir -p ~/.codex/skills
cp -r SKILL_IA/saas-ui ~/.codex/skills/saas-ui
```

Rode o Codex no projeto e peça com as palavras do `description`.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> <code>~/.copilot/skills/</code></summary>

```bash
mkdir -p ~/.copilot/skills
cp -r SKILL_IA/saas-ui ~/.copilot/skills/saas-ui
```

Chame `copilot` e descreva a tarefa com as palavras do `Uso` na tabela acima.

</details>

<details>
<summary><strong>Gemini CLI</strong> <code>~/.gemini/skills/</code></summary>

```bash
mkdir -p ~/.gemini/skills
cp -r SKILL_IA/saas-ui ~/.gemini/skills/saas-ui
```

Abra `gemini` no projeto e peça com as palavras do `description`.

</details>

<details>
<summary><strong>OpenCode</strong> <code>~/.config/opencode/skills/</code></summary>

```bash
mkdir -p ~/.config/opencode/skills
cp -r SKILL_IA/saas-ui ~/.config/opencode/skills/saas-ui
```

Use o nome da skill no prompt. Vale "crie um dashboard" ou "deixa essa tela mais moderna".

</details>

## Convenções

- Entregue um resultado por resposta, sem lorem.
- `saas-ui` pede plano de 10 linhas com self-check. Escreva o plano antes de codar.
- Teste 360px sem rolagem lateral. Mantenha foco visível no teclado, respeite `prefers-reduced-motion` e garanta contraste AA no texto.
- Escolha um momento memorável por tela. Contenha o entorno.

## Licença

MIT. Leia os termos em [LICENSE](LICENSE).
