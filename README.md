# Espião de Funil

Engenharia reversa automática de funis a partir de um link do Instagram, usando Claude Code.

## O que ele faz

Você cola um link do Instagram. Em ~3 minutos você recebe:

1. **Bio + Link na bio mapeados** — destino real, redirecionamentos, pixels instalados (Meta, GA, TikTok, Hotjar)
2. **Landing/checkout decifrado** — headline, sub, prova social, oferta, preço, order bump, upsells
3. **Biblioteca de anúncios** — todos os criativos ativos no Meta Ad Library, copies, datas de início, regiões
4. **Estratégia do lançamento** — classificação do funil (PLF, perpétuo, VSL, low-ticket, high-ticket), gatilhos de copy, linha do tempo
5. **Diagrama Mermaid** — o funil inteiro desenhado em [reports/](reports/) pronto pra você adaptar

## Como usar

1. Leia [INSTALL.md](INSTALL.md) — instalação de ~5 minutos
2. Configure a API key do Apify: `/spy-setup`
3. Espione: `/spy https://instagram.com/perfil_alvo`
4. Abra o relatório em [reports/](reports/)

## Custo de operação

- **Claude Code**: sua assinatura
- **Apify**: free tier dá ~50 espionagens/mês. Depois custa ~$0.05–0.20 por espionagem completa.

## Suporte

- Bugs e atualizações: abra uma Issue neste repositório, ou me chama no Instagram [@cyntiaesberard](https://instagram.com/cyntiaesberard)
- Versão: 1.0.0
