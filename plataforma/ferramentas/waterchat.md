---
title: ChatOps com o Mattermost
description: Recriando o chat.aguas.ml em 2020
published: true
date: 2020-09-30T21:26:13.669Z
tags: águas, plataforma, chat, ubuntu, mattermost
editor: markdown
---

# ChatOps usando o Mattermost
O https://chat.aguas.ml conta com com aplicativo para celulares, notebooks e desktops, podendo também ser utilizado via navegadores, muito útil caso queiramos sair dos servidores das grandes empresas de internet.

Com adoção, se a dinâmica e as pessoas curtirem, podemos usar com tranquilidade chats privados, grupos livres, etc. Ainda conta com uma gama interessante de integrações com outros aplicativos e sistemas.

Veja nosso manual de uso: https://aguas.win/manual-de-uso/

.
## Links para utilização
A seguir, uma lista com possibilidades de acesso ao chat

- Pelo navegador: https://chat.aguas.ml
- Com aparelhos Android: https://play.google.com/store/apps/details?id=com.mattermost.rn
- Com aparelhos Apple: https://apps.apple.com/us/app/mattermost/id1257222717
- Programas para computadores Windows, MAC e Linux: https://mattermost.com/download/

.
## Sobre a instalação
Para instalar escolha um guia em https://docs.mattermost.com/guides/administrator.html#installing-mattermost

.
### Dicas úteis

Renovando SSL
A cada 3 meses é preciso renovar o SSL, caso receba erros na renovação automática

Para tanto, atualize o sistema, instale ou atualize o git, baixe o let´s encrypt mais recente do github, pare o nginx, instale ou atualize o let´s encrypt e rode-o. Tentamos renovar somente, com erros. Até descobrirmos que se você usar o comando de instalação, ele identificará que já existe um certificado e vai renovâ-lo para você.

```text
sudo apt-get update

sudo apt-get install git

git clone https://github.com/letsencrypt/letsencrypt

cd letsencrypt

sudo systemctl stop nginx

./letsencrypt-auto certonly --standalone

sudo systemctl start nginx
```

Depois reinicie o servidor, para garantir
```text
reboot
```