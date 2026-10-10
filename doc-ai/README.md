# doc-ai

Skill autoral para ler um projeto e documentar com base no código: propósito,
módulos, arquitetura, diagramas e dívidas técnicas, com melhorias como sugestão.

## Quando usar

Use quando pedir para documentar projeto ou código, gerar docs ou README,
mapear arquitetura, explicar o que um repo faz, ou registrar features futuras.

## Regras

- Toda afirmação nasce de arquivo lido; sem placeholders.
- A skill sempre pergunta destino (`docs/`, README ou ambos) e profundidade
  (visão geral, por módulo ou completa) antes de escrever.
- Melhorias vão no documento e nunca entram no código sem confirmação.

## Estrutura

```text
doc-ai/
├── SKILL.md   # instrução da skill (inglês)
├── README.md  # este arquivo
└── LICENSE    # MIT (raiz do repo)
```

## Licença

MIT — ver `LICENSE` na raiz do repo.
