---
title: Opções do RSS Bridge
description: Algumas dicas para utilizar o RSS Bridge 
published: true
date: 2021-02-22T23:02:57.027Z
tags: rss, bridge, open source
editor: markdown
dateCreated: 2021-02-22T23:02:57.027Z
---

# Dicas de Uso
Do RSS Bridge

## O que é RSS?

RSS é um formato de distribuição de informações em tempo real pela internet, no qual uma fonte de informação publica alguma novidade que pode ser automaticamente recebida por um leitor, coletor, agregador e/ou replicador.

.
### O que é RSS Bridge?
RSS-Bridge é um projeto PHP capaz de gerar feeds RSS e Atom para sites que não os possuem. 

Importante: RSS-Bridge não é um leitor de feed ou agregador de feed, mas uma ferramenta para gerar feeds que são consumidos por leitores e agregadores de feed.

.

### Tipos de saída
Após selecionar o software que usaremos como agregador ou replicador, nós utilizamos o RSS Bridge para extrair informações que de algum modo não acontecem facilmente. Assim podemos obter informações nos seguintes formatos:

- Atom: feed Atom, para uso em leitores de feed
- Html: página HTML simples
- Json: JSON, para consumo por outros aplicativos
- Mrss: feed MRSS, para uso em leitores de feed
- Texto simples: texto bruto, para consumo por outros aplicativos

.
## Opções para whitelist
Todas as opções para sua *whitelist.txt* estão aqui: https://github.com/RSS-Bridge/rss-bridge/tree/master/bridges

As nossas são:

```texto
BandcampBridge
CryptomeBridge
DuckDuckGoBridge
FacebookBridge
FlickrExploreBridge
FolhaDeSaoPauloBridge
GoogleSearchBridge
InstagramBridge
TrelloBridge
PinterestBridge
TwitterBridge
WikipediaBridge
YoutubeBridge
Arte7
FDroid
WikiLeaks
WordPressBridge
TheHackerNews
SoundcloudBridge
TelegramBridge
```