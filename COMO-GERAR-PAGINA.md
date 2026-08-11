# Como criar o Espião de Funil — guia pra quem nunca programou

Você vai montar uma ferramenta que descobre como qualquer concorrente vende — só com o link do Instagram dele.

Não precisa saber código. Só seguir 7 passinhos. Tempo: **40 minutos** (sendo 30 min de espera enquanto o computador faz o trabalho).

---

## 📖 Glossário rápido (leia uma vez e esqueça)

Antes de começar, 4 palavras que vão aparecer:

| Palavra | O que é, em uma frase |
|---|---|
| **Claude Code** | Um programa de inteligência artificial que mora no seu computador e faz o que você pedir por escrito. |
| **Apify** | Um serviço da internet que "lê" páginas pra gente — tipo um leitor de placas. A gente precisa dele pra ler Instagram e Facebook. |
| **Token** | Uma senha grande e estranha, tipo `apify_api_abc123xyz...`. Você copia e cola, nunca digita. |
| **Prompt** | É só uma mensagem que você manda pro Claude. Igual mandar mensagem no WhatsApp. |

Pronto. Bora.

---

## ✅ Passo 1 — Instalar o Claude Code (5 min)

1. Abra o navegador (Chrome, Edge, qualquer um)
2. Vá em: **https://claude.com/claude-code**
3. Clique no botão grande que diz **"Download"** ou **"Get started"**
4. Baixe a versão pro seu computador (Windows ou Mac — ele detecta sozinho)
5. Abre o arquivo baixado e instala normalmente (próximo, próximo, concluir)

**✔ Como saber se deu certo:** Aparece um ícone novo no menu iniciar (Windows) ou no Launchpad (Mac) chamado **Claude**. Abre ele uma vez e fecha.

---

## ✅ Passo 2 — Pegar o Token do Apify (5 min)

1. Vá em: **https://console.apify.com/sign-up**
2. Crie conta grátis (pode usar Google, é mais rápido)
3. Confirme o e-mail que eles mandam
4. Depois de logado, no menu da esquerda clique em **"Settings"** (ou Configurações)
5. Clique em **"Integrations"** (Integrações)
6. Você vai ver um campo chamado **"Personal API token"**
7. Clique no botãozinho de **copiar** (📋) do lado do token
8. **Cola num bloco de notas** — você vai usar daqui a pouco. Não perde!

**✔ Como saber se deu certo:** Você tem um texto colado no bloco de notas que começa com `apify_api_` e tem umas 40 letras aleatórias depois.

---

## ✅ Passo 3 — Criar a pasta do projeto (1 min)

1. Vá pro **Desktop** (área de trabalho)
2. Clique com **botão direito** → **Novo** → **Pasta**
3. Nomeie como: **Espiao-de-Funil**

Pronto. Só isso.

---

## ✅ Passo 4 — Abrir o Claude dentro da pasta (1 min)

1. Abra a pasta `Espiao-de-Funil` que você acabou de criar
2. Clique na **barra de endereço** (onde aparece o caminho da pasta)
3. Apague o que tiver lá e digite: **cmd** (no Windows) ou **terminal** (no Mac)
4. Aperte **Enter**
5. Vai abrir uma janela preta com letrinhas brancas. Não se assuste — é normal.
6. Nessa janela preta, digite: **claude** e aperte **Enter**

**✔ Como saber se deu certo:** Aparece uma mensagem do Claude tipo *"Welcome to Claude Code"* e um cursor piscando esperando você digitar.

---

## ✅ Passo 5 — O Prompt Mágico (cole e espera) (20-30 min)

Agora é a parte boa. Você vai colar **UMA mensagem** no Claude e ele vai construir o produto inteiro sozinho.

**1.** Pega o token do Apify que você guardou no bloco de notas

**2.** Substitui `COLE_SEU_TOKEN_AQUI` no prompt abaixo pelo seu token de verdade

**3.** Copia o prompt INTEIRO (do `--- INÍCIO ---` até o `--- FIM ---`)

**4.** Cola no Claude e aperta Enter

```
--- INÍCIO DO PROMPT ---

Olá! Você vai construir um produto chamado "Espião de Funil" neste projeto. Eu não sei programar, então faça TUDO sozinho. Só me avise quando terminar.

MEU TOKEN APIFY: COLE_SEU_TOKEN_AQUI

O produto é uma ferramenta que faz engenharia reversa de funis de venda a partir de um link do Instagram. Quando o usuário rodar /spy <link-instagram>, deve:
1. Pegar dados do Instagram via Apify
2. Visitar o link da bio (landing page)
3. Procurar anúncios no Meta Ad Library via Apify
4. Analisar tudo e classificar o tipo de funil
5. Gerar um relatório em reports/<nome>-<data>.md com diagrama Mermaid

Por favor, faça em ordem:

PARTE 1 — Configure o Apify MCP em .claude/settings.json (ou no arquivo certo do sistema) usando meu token acima.

PARTE 2 — Crie um arquivo CLAUDE.md na raiz explicando o produto, o pipeline de 5 etapas e as convenções:
- Saída em português brasileiro
- Relatórios em reports/<handle>-<YYYY-MM-DD>.md
- Diagrama Mermaid sempre flowchart TD
- Nunca inventar dados — marcar (não disponível) quando faltar

PARTE 3 — Crie a skill em .claude/skills/funnel-spy/SKILL.md com:
- Taxonomia de 8 tipos de funil (PLF, Evergreen, VSL, Low-ticket Tripwire, High-ticket Aplicação, Desafio, Webinar, Lançamento Relâmpago)
- 7 gatilhos clássicos de copy (Escassez, Urgência, Prova social, Autoridade, Reciprocidade, Compromisso, Transformação)
- Checklist de pixels (Meta, Google Analytics, TikTok, Hotjar, RD Station)
- Plataformas de checkout BR (Hotmart, Eduzz, Kiwify, PerfectPay, Monetizze, Braip, Doppus)
- Template Mermaid base
- Template do relatório final

PARTE 4 — Crie o subagente em .claude/agents/funnel-spy.md que orquestra o pipeline completo e salva o relatório em reports/.

PARTE 5 — Crie 3 comandos:
- .claude/commands/spy.md (comando /spy <url> — valida URL, chama o subagente, mostra resumo)
- .claude/commands/spy-setup.md (comando /spy-setup — verifica se Apify está configurado, pasta reports existe, skills estão no lugar)
- .claude/commands/dash.md (comando /dash — lê todos os .md em reports/ e gera dashboard.html com identidade visual terracota: clay #CC785C sobre fundo warm black #0F0E0C, tipografia Cormorant Garamond para títulos e Inter para texto, renderiza Mermaid via CDN, abre o HTML no navegador)

PARTE 6 — Crie a pasta reports/ vazia.

PARTE 7 — Ao terminar tudo, rode /spy-setup pra eu ver se passou em todos os checks.

IMPORTANTE: tudo em português brasileiro. Não me pergunte nada — decida sozinho e faça. Só me avise quando os 7 passos estiverem prontos.

--- FIM DO PROMPT ---
```

**Agora é só esperar.** O Claude vai trabalhar uns 20-30 minutos criando arquivo por arquivo. Você verá ele escrevendo coisas na tela. Não mexa.

**✔ Como saber se deu certo:** Ele vai te mandar uma mensagem final tipo: *"Pronto! Todos os 7 passos concluídos. O /spy-setup passou em todos os checks. Pra testar, rode /spy <link>."*

---

## ✅ Passo 6 — Testar com um perfil real (3 min)

No mesmo terminal do Claude, digite:

```
/spy https://www.instagram.com/eltoneuler/
```

Aperte **Enter** e espere uns 3-4 minutos.

**✔ Como saber se deu certo:** Aparece uma mensagem dizendo *"Relatório salvo em reports/eltoneuler-2026-XX-XX.md"*.

---

## ✅ Passo 7 — Ver bonitinho no navegador (1 min)

Digite no Claude:

```
/dash
```

**✔ Como saber se deu certo:** Abre automaticamente uma página linda no seu navegador, fundo escuro com letras laranjas, mostrando o relatório com um diagrama do funil do concorrente. **Pronto, você tem o produto rodando.**

---

## 😱 Se algo der errado

**"Apareceu uma tela vermelha com erro"**
→ Tira print da tela e manda pro Claude com a mensagem: *"Deu esse erro. Conserta."* Ele resolve.

**"O Claude me pergunta uma coisa que eu não sei responder"**
→ Manda: *"Decide você. Não sei programar. Escolhe o caminho mais simples."*

**"O Apify diz que estou sem créditos"**
→ Plano grátis dá ~50 espionagens por mês. Se acabou, espera o próximo mês ou paga US$10 lá no console.apify.com/billing.

**"Não achei o token do Apify"**
→ console.apify.com → entra → Settings (engrenagem) → Integrations → "Personal API token" → botão de copiar.

**"O Claude travou no meio"**
→ Aperta **Esc** e digita: *"Continua de onde parou."*

---

## 🎁 O que você acabou de ganhar

Você agora tem uma ferramenta que:
- Descobre o funil de qualquer concorrente em 3 minutos
- Lê o Instagram dele
- Lê a página de vendas dele
- Lê os anúncios dele no Facebook
- Te entrega um relatório completo com diagrama
- Tudo num painel bonitinho no navegador

Pra usar daqui pra frente, **só abrir o Claude na pasta e digitar /spy <link>**. Mais nada.

---

*Guia escrito pra quem nunca programou · v1.0 · 2026-05-17*
