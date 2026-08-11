# Espião de Funil — Projeto Claude Code

Este projeto faz engenharia reversa de funis de venda a partir de um link do Instagram. Skill de Claude Code open-source.

## Como o produto funciona

Quando o usuário roda `/spy <url-instagram>`, o subagente `funnel-spy` executa este pipeline:

1. **Scraping do Instagram** (via Apify MCP) → bio, posts recentes, link na bio
2. **Fetch da landing/checkout** (via WebFetch + ctx_fetch_and_index) → copy, pixels, oferta
3. **Meta Ad Library** (via Apify) → anúncios ativos do perfil/domínio
4. **Análise + classificação** → tipo de funil, gatilhos, estratégia
5. **Geração do relatório** → `reports/<perfil>-<YYYY-MM-DD>.md` com diagrama Mermaid

## Estrutura do produto

- `.claude/skills/funnel-spy/SKILL.md` — playbook (taxonomia, gatilhos, template Mermaid)
- `.claude/agents/funnel-spy.md` — subagente orquestrador
- `.claude/commands/spy.md` — comando `/spy <url>`
- `.claude/commands/spy-setup.md` — comando `/spy-setup`
- `reports/` — saída dos relatórios

## Convenções

- Toda saída pro usuário em **português brasileiro**
- Relatórios sempre em `reports/<handle>-<YYYY-MM-DD>.md`
- Diagrama Mermaid sempre `flowchart TD`
- Nunca inventar dados que não vieram do scraping — se faltou, marcar como `(não disponível)`
