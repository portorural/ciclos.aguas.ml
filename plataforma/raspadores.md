---
title: Raspadores
description: 
published: true
date: 2019-11-30T01:50:27.486Z
tags: tecnologias, raspadores
---

# Raspador Porto ÁguasML

Alimenta as notícias dinâmicas na página principal da plataforma Notícias ÁguasML


## Tecnologias empregadas
Softwares utilizados: FreshRSS, RSS-Bridge e Telegram

> URL do FreshRSS: https://freshrss.org
> URL do RSS-Bridge: https://github.com/rss-bridge/rss-bridge
> URL do Telegram: https://telegram.org
{.is-info}

## Links de acesso
Links do Raspador Porto ÁguasML

> ~~URL de aplicação 01: http://swarm.aguas.ml~~
> URL de aplicação 02: https://porto.aguas.ml
{.is-info}

## Configuração
Nossa configuração conta com o FreshRSS, além de ler e coletar notícias via RSS, trabalha em conjunto com outro software que cria um novo link RSS, geral ou personalizado por categorias.

Assim ele pode alimentar qualquer outro site que trabalhe como RSS.

## Fontes de dados
Informações sobre as fontes de dados deste raspador

> Número de fontes atualmente no feed: 32 endereços
> Total de notícias recebidas: 7430 notícias
{.is-warning}

# Raspador ÁguasBot Brasil
Fizemos um *bot* em um canal de notícias no comunicador Telegram, que nomeamos como ÁguasBot Brasil.

Diríamos que aqui o *bot* é um programa escrito (ou configurado) para repetir padrões que alguns humanos porventura estejam fazendo manualmente.

## Tecnologias utilizadas
O bot é simples e segue a lógica do serviço IFTTT (If This Than That)

> URL das Notícias: https://porto.aguas.ml
> URL do IFTTT: https://ifttt.com/
> URL do Telegram: https://telegram.org
{.is-info}

Então se algo for agregado por nosso raspador então vamos mandar uma publicação para um canal de notícias do software Telegram.

## Configurando o IFTTT
A programação a ser feita na plataforma IFTTT é bem simples e o resultado pode ser visualizado na figura 50:

```text
(ஃ) Gotas Aguas.ML (ஃ)<br>
< br>
< gota: >> {{EntryTitle}}<br>
< br>
< link >> {{EntryUrl}}
```

Onde *EntryTitle* será o título da notícia e *EntryUrl* o link para que a pessoa possa acessar o conteúdo, tudo isso coletado automaticamente segundo os padrões em comum com o FreshRSS.

O restante é uma forma de configurar como suas intenções desejam. O IFTTT trata isso como ingredientes a serem adicionados em sua receita, são milhares de programações semelhantes disponíveis nesta e outras plataformas com a mesma função.

.
## Observações
São seis as pessoas reais inscritas, mais dois perfis para o bot. 

Cinco destas pessoas reais visualizam as mensagens postadas assiduamente.

O link foi divulgado somente uma vez no grupo de WhastApp do ProfÁgua Brasil, com intenções motivacionais de uso da ferramenta. A não divulgação do serviço em teste é fundamental para evitar que a bolha estoure.

Tivemos uma pessoa que saiu do canal logo após um alto fluxo de notícias, incontrolável por erro de programação.
