---
title: Uma alternativa em Docker para Mediawiki 1.26
description: Registro de operações
published: true
date: 2022-08-18T17:01:54.040Z
tags: wiki, docker, compose, mediawiki, mysql
editor: markdown
dateCreated: 2022-08-18T17:01:20.488Z
---

# Compartilhando composiç
Dicas para uso da MW em versão antiga

```
version: '3'

networks:
  suarede:
    
volumes:
  data_mw:
  dados_mw:
  
services:
  mwiki_db:
    image: mysql:5.7
    volumes:
      - data_mw:/var/lib/mysql:rw
    ports:
      - 13306:3306
    environment:
      MYSQL_DATABASE: wiki_db
      MYSQL_ROOT_PASSWORD: rootSENHA
      MYSQL_USER: wikimediaUSER
      MYSQL_PASSWORD: wikimediaSENHA
    networks:
      - suarede
    restart: always

  mwiki:    
    image: bitnami/mediawiki:1.26.3-r1
    ports:
      - 8080:80
    depends_on:
      - mwiki_db
    volumes:
      - dados_mw:/var/www/html/
    environment:
      - MEDIAWIKI_DB_HOST=mwiki_db
      - MEDIAWIKI_DB_TYPE=mysql
      - MEDIAWIKI_DB_NAME=wiki_db
      - MEDIAWIKI_DB_USER=wikimediaUSER
      - MEDIAWIKI_DB_PASSWORD=wikimediaSENHA
      - MEDIAWIKI_SITE_SERVER=//localhost
      - MEDIAWIKI_SITE_NAME=MediaWiki
      - MEDIAWIKI_SITE_LANG=pt_BR
      - MEDIAWIKI_ADMIN_USER=adminUSER
      - MEDIAWIKI_ADMIN_PASS=passwordSENHA
      - MEDIAWIKI_UPDATE=true
    restart: always
    networks:
      - suarede
````

Após a configuração inicial, baixe LocalSettings.php para o mesmo diretório que usou para executar este yaml e adicione a linha a seguir no volume do mwiki. Use compose para reiniciar o serviço mediawiki#

      - ./LocalSettings.php:/var/www/html/LocalSettings.php



### Fontes

Bitnami: https://hub.docker.com/r/bitnami/mediawiki
Wikimedia: https://github.com/wikimedia/mediawiki-containers/blob/master/docker-compose.yml