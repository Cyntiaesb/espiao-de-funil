---
description: Gera/atualiza a dashboard.html lendo todos os relatórios de reports/ e abre no navegador
---

Você vai gerar a dashboard local do Espião de Funil. Siga em ordem:

## 1. Listar relatórios
Use Glob `reports/*.md` (ignore `.gitkeep`). Se vazio, escreva no chat:
> "Nenhuma espionagem ainda. Rode `/spy <link-instagram>` primeiro."
> e pare.

## 2. Para cada relatório, extraia (via Read + parsing):

- `handle`: do nome do arquivo (`reports/<handle>-<data>.md`)
- `date`: do nome do arquivo
- `reportFile`: o caminho relativo `reports/<arquivo>.md`
- `tipo`: linha após "Tipo de funil:" no resumo executivo
- `ticket`: linha após "Ticket estimado:"
- `gatilho`: linha após "Gatilho dominante:"
- `estagio`: linha após "Estágio atual:" (ou similar)
- `mermaid`: TODO o conteúdo dentro do bloco ```` ```mermaid ... ``` ```` da seção "5. Diagrama do funil"
- `mermaidLink`: gere via Python no sandbox compactando o mermaid com zlib+base64 → `https://mermaid.live/edit#pako:<b64>`
- `diagnostico`: TODO o conteúdo markdown da seção "## 6. Diagnóstico estratégico" até a próxima seção `## 7.`

## 3. Gerar o link Mermaid via Python sandbox

```python
import json, base64, zlib
state = {"code": mermaid_code, "mermaid": '{"theme":"default","securityLevel":"loose"}', "autoSync": True, "updateDiagram": True}
b64 = base64.urlsafe_b64encode(zlib.compress(json.dumps(state).encode(), 9)).decode().rstrip("=")
link = "https://mermaid.live/edit#pako:" + b64
```

## 4. Construir o JSON e injetar no template

Leia o `dashboard.html` da raiz. Faça um Edit substituindo o token `REPORTS_DATA_PLACEHOLDER` por um array JSON dos relatórios mais recentes primeiro:

```js
[
  {handle, date, reportFile, tipo, ticket, gatilho, estagio, mermaid, mermaidLink, diagnostico},
  ...
]
```

Cuidados:
- Escape aspas e quebras de linha no campo `mermaid` e `diagnostico` (use `JSON.stringify` lógico)
- Ordem: relatórios mais recentes primeiro (sort por data desc)

## 5. Reportar ao usuário

```
✅ Dashboard atualizada com N espionagens.

📂 Abra: dashboard.html (clique duplo, abre no navegador padrão)
```

Se possível e no Windows, sugira: `start dashboard.html` no terminal.
