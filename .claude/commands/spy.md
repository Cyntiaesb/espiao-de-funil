---
description: Faz engenharia reversa do funil de um perfil do Instagram. Uso /spy <url-instagram>
argument-hint: <url-instagram>
---

Você vai espionar o funil do perfil: **$ARGUMENTS**

**Passos obrigatórios:**

1. Valide que `$ARGUMENTS` é uma URL do Instagram (instagram.com/...). Se não for, peça a URL correta e pare.

2. Invoque o subagente `funnel-spy` usando a tool Agent, passando o link como objetivo. Diga ao subagente:
   - Execute o pipeline completo descrito em `.claude/agents/funnel-spy.md`
   - Gere o relatório em `reports/<handle>-<data-iso>.md`
   - Retorne ao final apenas: caminho do relatório + 3 bullets-resumo (tipo de funil, principal gatilho, ticket estimado)

3. Após o subagente terminar, mostre ao usuário:
   - ✅ Relatório salvo em `reports/...`
   - Os 3 bullets-resumo
   - Lembrete: "Abra o arquivo pra ver o diagrama Mermaid completo"

Se o subagente falhar em alguma etapa (sem créditos Apify, perfil privado, etc.), reporte o erro claramente em PT-BR e sugira a correção.
