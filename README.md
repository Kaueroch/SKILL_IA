# SKILL_IA

Você copia uma pasta para o agente e ele segue a rotina. Você usa 4 skills: UI de SaaS, documentação técnica, criador de subagentes e gerador de AGENTS.md.

[![Site](https://img.shields.io/badge/site-ao_vivo-brightgreen)](https://kaueroch.github.io/SKILL_IA/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Prefere clicar? Escolha skill e ferramenta no [site](https://kaueroch.github.io/SKILL_IA/) e copie o comando.

## Pedido e entrega por skill

| Skill | Você pede | Você recebe |
|---|---|---|
| `saas-ui` | `crie um pricing para CRM de freelancer solo` | Blocos React + TS + Tailwind v4 + shadcn/new-york. Você aprova um plano de 10 linhas antes do código. Você usa em projeto React com Tailwind v4. |
| `doc-ai` | `documente este repo em docs/overview.md` | `docs/overview.md` + `docs/<modulo>.md` com fluxos, paths reais `path:line` e diagramas mermaid. Você rastreia cada afirmação até o arquivo lido. |
| `sub-agent-builder` | `crie um subagente code-reviewer para este repo` | Um arquivo `<nome>.md` com gatilhos, workflow, guardrails e permissões `edit`/`bash`. Você chama com `@nome`. |
| `agents-md` | `gere o AGENTS.md standard para este repo` | `AGENTS.md` na raiz com setup, estilo, comandos de teste e guardrails lidos de manifests e CI. Níveis `minimal`, `standard`, `complete`. |

Você lê os detalhes na pasta da skill: `saas-ui/SKILL.md`, `doc-ai/SKILL.md`, `sub-agent-builder/SKILL.md`, `agents-md/SKILL.md`.

## Instalação em 2 passos

1. Clone o repo ao lado do seu projeto:
```bash
git clone https://github.com/Kaueroch/SKILL_IA.git
```

2. Copie a skill para a pasta da sua ferramenta. Troque `saas-ui` pelo nome da skill que você quer:

| Ferramenta | Destino |
|---|---|
| Claude Code | `~/.claude/skills/` |
| Cursor | `.cursor/skills/` na raiz do projeto |
| Codex | `~/.codex/skills/` |
| Copilot CLI | `~/.copilot/skills/` |
| Gemini CLI | `~/.gemini/skills/` |
| OpenCode | `~/.config/opencode/skills/` |

Exemplo para Claude Code:
```bash
cp -r SKILL_IA/saas-ui ~/.claude/skills/saas-ui
```

Reinicie o terminal da IA após copiar.

## Confirmação

Rode `/skills` no Claude Code e veja `saas-ui` na lista. Nas outras ferramentas, abra o chat no projeto e peça com a frase da tabela acima. Você sabe que funcionou quando o agente responde no formato da skill: plano antes do código em `saas-ui`, perguntas de escopo antes de escrever em `doc-ai`.

## Pastas

```text
SKILL_IA/
├── saas-ui/SKILL.md
├── doc-ai/SKILL.md
├── sub-agent-builder/SKILL.md
├── agents-md/SKILL.md
└── docs/index.html
```

Você edita o site em `docs/index.html`. Você lê a rotina completa no `SKILL.md` dentro de cada pasta.

## Licença

MIT. Leia os termos em [LICENSE](LICENSE).
