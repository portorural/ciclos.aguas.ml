---
title: Criando Rotinas no WikiJS da ÁguasML
description: Links e anotações importantes para cria Rotinas no Ciclos ÁguasML
published: true
date: 2022-08-02T01:31:42.528Z
tags: nginx, wiki
editor: markdown
dateCreated: 2019-11-29T17:23:25.846Z
---

# Links importantes wikijs
Dicas para a criação e manutenção de uma instalação do WIKIJS nas versões 1.0 ou 2.0


- [Instalando ou revisando o git no wikijs](https://docs-legacy.requarks.io/wiki/install/git)
- [Usando o wikijs  2.0 e o Github](https://docs.requarks.io/en/storage/git)
- [Para fazer o upgrade do Wiki.JS](https://docs.requarks.io/install/upgrade)
- [O sistema sincroniza com o git a cada 5 minutos, não há como mudar.](https://github.com/Requarks/wiki/issues/627)
- [Modelo nginx de websites](https://linuxize.com/post/how-to-install-wordpress-with-nginx-on-ubuntu-18-04/)
- [Instalar rapidamente Ubuntu 18.04 LEMP](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-ubuntu-18-04)

.
## Wikijs com BD postgresql
Para usar o WikiJS com o banco de dados postgresql, talvez esta dica seja útil caso não tenha familiaridade com este BD

```text
sudo -u postgres psql
postgres=# create database mydb;
postgres=# create user myuser with encrypted password 'mypass';
postgres=# grant all privileges on database mydb to myuser;
```

Veja mais em [Criando usuário de banco de dados com o postgresql](https://medium.com/coding-blocks/creating-user-database-and-adding-access-on-postgresql-8bfcd2f4a91e)