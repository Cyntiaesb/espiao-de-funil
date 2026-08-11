---
description: Análise profunda dos anúncios ativos no Meta Ad Library de um perfil do Instagram. Foco SÓ em criativos (vs. /spy que analisa funil inteiro). Uso /ads <url-instagram>
argument-hint: <url-instagram>
---

Você vai fazer a análise profunda dos anúncios ativos de: **$ARGUMENTS**

**Diferença em relação ao /spy:**
- `/spy` = funil INTEIRO (Instagram + landing + ads + estratégia)
- `/ads` = SÓ os ads, mas em PROFUNDIDADE (todos os criativos, padrões, copy, timeline, templates)

## Passos obrigatórios

1. **Valide** que `$ARGUMENTS` é uma URL do Instagram. Se não for, peça correção e pare.

2. **Invoque o subagente `ads-analyzer`** usando a tool Agent. Passe:
   - O link como objetivo
   - Instrução pra executar o pipeline completo descrito em `.claude/agents/ads-analyzer.md`
   - Salvar relatório em `reports/ads-<handle>-<data-iso>.md`

3. **Após o subagente terminar**, mostre ao usuário:
   - ✅ Relatório salvo em `reports/ads-...`
   - **Total de ads ativos** identificados
   - **Criativo vencedor** (hipótese)
   - **Padrão dominante** detectado
   - **1 recomendação acionável** principal
   - Lembrete: "Rode `/dash` pra adicionar essa análise à dashboard. Ou abra o `.md` direto pra ler completo."

## Se der erro

- **Sem créditos Apify:** "Sem créditos no Apify. Acesse console.apify.com/billing"
- **Nenhum ad encontrado:** "Esse anunciante não tem ads ativos no Meta Ad Library BR no momento. Tente outro perfil ou aguarde abrir carrinho."
- **Perfil privado:** "Perfil privado — não consigo identificar o anunciante. Use um perfil público."

Reporte sempre em **PT-BR** e com tom direto.
