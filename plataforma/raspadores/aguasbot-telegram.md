---
title: Raspador ÁguasBot Brasil
description: 
published: true
date: 2019-11-30T01:54:44.335Z
tags: 
---

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
