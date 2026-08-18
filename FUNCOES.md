# ⚡ Espião de Funil — Manual de Funções

Tudo o que a ferramenta faz, organizado por tipo de uso.
Versão **1.0.0** · Última atualização **2026-05-16**

---

## 🎯 O que é o Espião de Funil

Uma ferramenta de **engenharia reversa automática de funis de venda** que roda dentro do Claude Code. Você cola um link do Instagram, ela faz a análise completa — Instagram + landing + anúncios + estratégia — e entrega um relatório acionável com diagrama Mermaid e diagnóstico estratégico.

**Para quem é:** infoprodutores, gestores de tráfego, copywriters, mentores, consultores de marketing, agências.

**Não é:** scraper genérico, banco de leads, ferramenta de espionagem ilegal. Tudo o que ela acessa é informação pública.

---

## 📋 Comandos disponíveis

A ferramenta funciona através de **3 comandos** dentro do Claude Code:

### 1. `/spy <url-instagram>`

**Comando principal.** Dispara o pipeline completo de engenharia reversa.

**Como usar:**
```
/spy https://www.instagram.com/perfil_alvo/
```

**O que acontece (pipeline de 10 etapas, 2–4 minutos):**

1. **Validação da URL** — confirma que é um link válido do Instagram
2. **Scraping do Instagram** — bio, link na bio, posts recentes, CTAs, engajamento, autoridade
3. **Fetch da landing page** — copy, headline, sub, preços, pixels, plataforma de checkout, garantia, bônus, prova social
4. **Meta Ad Library** — anúncios ativos, criativos, datas, copy, variações
5. **Análise estratégica** — classificação do funil, identificação de gatilhos, tipo de oferta (cada uma etiquetada como confirmado ou hipótese)
6. **Diagrama Mermaid** — desenho visual do funil com nós clicáveis
7. **Diagnóstico estratégico** — análise de por que funciona + pontos fortes/fracos
8. **Comparação temporal** — se já existir espionagem anterior desse mesmo perfil, aponta o que mudou
9. **Relatório final** — salvo em `reports/<handle>-<data>.md`
10. **Resumo no chat** — 3 bullets (tipo, gatilho, ticket)

**O que você recebe:**
- Arquivo Markdown completo em `reports/`
- Resumo executivo no chat (3 bullets: tipo, gatilho, ticket)
- Link clicável do mermaid.live com diagrama interativo

---

### 2. `/dash`

**Atualiza a dashboard local.** Lê todos os relatórios em `reports/` e regenera o `dashboard.html` com tudo organizado em abas.

**Como usar:**
```
/dash
```

**O que acontece:**
1. Glob de todos os `reports/*.md`
2. Parsing de cada relatório (extrai resumo, mermaid, diagnóstico)
3. Geração do link mermaid.live para cada um
4. Injeção dos dados no template `dashboard.html`

**O que você recebe:**
- Arquivo `dashboard.html` atualizado
- Cada espionagem vira uma aba na dashboard
- Renderização visual do Mermaid (não precisa de editor especial)
- Diagnóstico estratégico formatado bonito

**Como visualizar:**
- Duplo clique em `dashboard.html`
- Ou: `start dashboard.html` (Windows) / `open dashboard.html` (Mac)

---

### 3. `/spy-setup`

**Checklist de saúde da instalação.** Verifica se tudo está conectado e pronto pra rodar.

**Como usar:**
```
/spy-setup
```

**O que ele verifica:**
- ✅ Apify MCP conectado
- ✅ Pasta `reports/` existe
- ✅ Skill `funnel-spy` presente
- ✅ Subagente `funnel-spy` presente

**Quando usar:**
- Logo após instalar, antes da primeira espionagem
- Se alguma espionagem falhar, pra diagnosticar o que está faltando

---

## 📊 O que o relatório de cada espionagem traz

Todo relatório (`reports/<handle>-<data>.md`) segue **9 seções padronizadas** (a 9ª só aparece se já existir espionagem anterior do mesmo perfil):

### Seção 1 — Resumo executivo
- Tipo de funil (PLF, perpétuo, VSL, low-ticket, etc.)
- Ticket estimado
- Gatilho dominante
- Estágio atual da operação

### Seção 2 — Instagram
- Dados do perfil (seguidores, posts, bio)
- Link na bio com UTM tags
- CTAs recorrentes nas captions
- Posts relevantes dos últimos 7 dias com engajamento
- Identificação de uso de Manychat / DM automática

### Seção 3 — Landing page
- URL e plataforma de checkout (Hotmart, Eduzz, Kiwify, etc.)
- Headline, sub-headline, oferta principal
- Estrutura de preços (de/por, parcelas, bumps, upsells)
- Bônus identificados
- Garantia oferecida (dias)
- Pixels detectados (Meta, GA, TikTok, RD Station)
- Plataforma de e-mail marketing
- Promessa central

### Seção 4 — Anúncios (Meta Ad Library)
- Total de anúncios ativos
- Tipos (vídeo, imagem, carrossel)
- Data do criativo mais antigo
- Plataformas onde rodam (Facebook, Instagram, Audience Network, Messenger, Threads)
- Top criativos identificados
- Hipótese de criativo vencedor

### Seção 5 — Diagrama Mermaid
- Diagrama visual completo do funil
- Nós clicáveis (LP, Checkout, Ads, IGs, Typeform)
- Link mermaid.live pronto pra editar

### Seção 6 — Diagnóstico estratégico ⭐
**Esta é a seção que justifica o valor do produto.**

- **🎯 O que ele está fazendo** — síntese em uma frase do "produto real" sendo vendido
- **🧠 Por que funciona** — 4–6 mecanismos psicológicos amarrados a evidência (Cialdini, ancoragem, qualificação, etc.)
- **💪 Pontos fortes** — tabela com impacto de cada um
- **⚠️ Pontos fracos exploráveis** — tabela com "como atacar/modelar"
- **🎬 Conclusão acionável** — passos numerados pra copiar + ROI estimado da operação

### Seção 7 — O que você pode copiar (modelar)
Lista numerada de aprendizados práticos pra aplicar no seu próprio funil.

### Seção 8 — Pontos fracos detectados
Lista de oportunidades que o concorrente não está aproveitando — onde você pode atacar.

### Seção 9 — O que mudou desde a última espionagem ⭐ (condicional)
Se você já espionou esse mesmo perfil antes, essa seção compara: tipo de funil, ticket, oferta principal e total de anúncios ativos entre a análise antiga e a atual. Transforma um snapshot único em monitoramento — você vê a operação evoluir (ou pivotar) ao longo do tempo.

---

## 🎨 A Dashboard (dashboard.html)

Interface visual auto-contida que roda direto no navegador, sem servidor.

**Features:**
- **Campo de input** pra colar novo link e gerar comando `/spy`
- **Abas** — cada espionagem aparece como uma aba separada
- **Cards de resumo** — Tipo, Ticket, Gatilho, Estágio em destaque
- **Mermaid renderizado** ao vivo (não precisa abrir editor)
- **Botões de ação** — abrir no mermaid.live, ver relatório completo
- **Diagnóstico estratégico** formatado com markdown renderizado
- **Identidade visual Terracota Anthropic** — tema dark warm com tipografia Cormorant + Inter

**Dependências externas:** Mermaid.js e Marked via CDN (precisa internet pra carregar a 1ª vez).

---

## 🧱 Arquitetura interna (pra quem quer customizar)

```
espiao-de-funil/
├── .claude/
│   ├── agents/
│   │   └── funnel-spy.md           # Subagente orquestrador (pipeline de 10 etapas)
│   ├── skills/
│   │   └── funnel-spy/
│   │       └── SKILL.md            # Playbook (taxonomia, gatilhos, templates)
│   ├── commands/
│   │   ├── spy.md                  # /spy <url>
│   │   ├── dash.md                 # /dash
│   │   └── spy-setup.md            # /spy-setup
│   └── settings.json               # Permissões pré-aprovadas
├── reports/                        # Saída dos relatórios .md
└── dashboard.html                  # UI auto-contida
```

### Pontos de customização

**Mudar a taxonomia de funis** (PLF, evergreen, VSL, etc.):
Edite `.claude/skills/funnel-spy/SKILL.md` → seção "1. Taxonomia de funis"

**Mudar os gatilhos rastreados**:
Edite `.claude/skills/funnel-spy/SKILL.md` → seção "2. Sete gatilhos de copy"

**Mudar o template do relatório**:
Edite `.claude/skills/funnel-spy/SKILL.md` → seção "6. Template do Relatório"

**Mudar o pipeline do subagente**:
Edite `.claude/agents/funnel-spy.md` → seções "Etapa 1" a "Etapa 8"

**Adicionar novas plataformas brasileiras** (além de Hotmart, Eduzz, Kiwify, etc.):
Edite `.claude/skills/funnel-spy/SKILL.md` → seção "4. Plataformas brasileiras comuns"

---

## 🚦 O que a ferramenta detecta automaticamente

| Categoria | O que detecta |
|---|---|
| **Plataformas de checkout** | Hotmart, Eduzz, Kiwify, PerfectPay, Monetizze, Braip, Doppus, Stripe |
| **Pixels de rastreamento** | Meta Pixel (fbq), Google Analytics/Ads (gtag), TikTok (ttq), Hotjar (hj), LinkedIn, Pinterest, RD Station, Mautic |
| **Plataformas de e-mail** | ActiveCampaign, Mailchimp, ConvertKit, LeadLovers, RD Station |
| **Tipos de funil** | PLF, Evergreen/Perpétuo, VSL, Low-ticket Tripwire, High-ticket Aplicação, Desafio, Webinar ao vivo, Lançamento relâmpago |
| **Gatilhos de copy** | Escassez, Urgência, Prova social, Autoridade, Reciprocidade, Compromisso, Transformação, Ancoragem, Inversão de risco |
| **Estratégias** | Manychat (comente palavra → DM), Linktree vs link direto, Dupla de contas (pessoa + marca), Webinar/desafio como porta de entrada |

---

## ⚠️ Limitações conhecidas

- ❌ **Não acessa Instagram privado.** Se o perfil for privado, retorna vazio.
- ❌ **Não detecta pixels server-side (CAPI puro)** — apenas pixels client-side carregados no HTML.
- ❌ **Não acessa páginas com auth wall** (Linkedin pago, Notion privado, etc.).
- ❌ **Não funciona offline** — depende de Apify (scraping) e Claude Code (análise).
- ⚠️ **Consome créditos do Apify** — cada espionagem usa ~$0.05–0.20 do seu plano grátis ($5/mês).
- ⚠️ **Não roda em background** — o Claude Code fica ocupado durante a espionagem (2–4 min).
- ⚠️ **Mermaid.live precisa internet** — sem net, o diagrama não renderiza no link compartilhável (mas funciona local na dashboard).

---

## 💡 Dicas de uso avançado

### Espionar uma marca/empresa (não só pessoa)
Use a conta principal da marca no Instagram. Se ela tem 2 contas (pessoa + marca), espione ambas separadamente — entrega 2x mais insight.

### Comparar concorrentes
Espione 5–10 perfis do mesmo nicho. Abra a dashboard e use as abas para comparar lado a lado:
- Tickets praticados
- Tipos de funil dominantes
- Gatilhos repetidos (= padrão do nicho)
- Garantias oferecidas

Identifica **o que é commodity** (todo mundo faz) vs **o que é diferenciador** (poucos fazem).

### Detectar lançamentos antes de abrir
Se você roda `/spy` num perfil e ele tem **muitos anúncios novos recentes + landing nova + UTM com data futura no link da bio**, ele está em fase de aquecimento — você está captando antes da abertura do carrinho.

### Modelar uma estratégia
Use o **Diagnóstico Estratégico** (Seção 6) como base. A subseção "Conclusão acionável" tem os passos prontos pra adaptar ao seu produto.

### Manter histórico
Cada relatório fica salvo com data no nome (`<handle>-<data>.md`). Se você espionar o mesmo perfil em momentos diferentes (antes/durante/depois de um lançamento), terá uma **série temporal** valiosa.

---

## 🛟 Quando algo dá errado

| Problema | Causa provável | Solução |
|---|---|---|
| `/spy` retorna "apify mcp not found" | MCP não conectado | Rode `claude mcp add apify -- npx -y @apify/actors-mcp-server --token SEU_TOKEN` |
| Pipeline para em "Sem créditos" | Apify esgotou | Aguarde dia 1 do mês ou adicione créditos em console.apify.com/billing |
| Instagram retorna vazio | Perfil privado/removido | Tente outro perfil |
| Landing não carrega | Site fora do ar | Pule essa etapa, o Claude segue com Ad Library |
| Dashboard não atualiza | Cache do navegador | Ctrl+F5 (Win) ou Cmd+Shift+R (Mac) |
| `/dash` retorna "nenhuma espionagem" | Pasta `reports/` vazia | Rode `/spy` pelo menos uma vez |

---

## 🔄 Roadmap — ideias pra próximas versões

Nada aqui é promessa de prazo — são ideias em aberto pra quem quiser contribuir:

- 🔜 Espionagem em lote (`/spy-batch` com lista de URLs)
- 🔜 Detecção de plataformas de afiliados
- 🔜 Comparativo automático entre perfis diferentes (hoje já compara o mesmo perfil ao longo do tempo, ver Seção 9)
- 🔜 Exportação do relatório para PDF estilizado
- 🔜 Integração com Notion/Airtable

---

## 📞 Suporte

Abra uma Issue neste repositório, ou me chama no Instagram [@cyntiaesberard](https://instagram.com/cyntiaesberard).

**Antes de pedir suporte**, rode `/spy-setup` e cole o resultado no e-mail — acelera muito o diagnóstico.

---

*Espião de Funil v1.0 — © 2026 Cyntia — Todos os direitos reservados*
