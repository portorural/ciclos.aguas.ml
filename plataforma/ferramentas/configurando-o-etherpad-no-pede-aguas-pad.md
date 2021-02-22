---
title: Como configuramos o Etherpad da plataforma ÁguasML
description: Algumas informações relevantes sobre nossa instalação do Etherpad  v1.6.6 no Pede Água Pad
published: true
date: 2021-02-22T20:56:28.275Z
tags: águas, plataforma, pad, ferramentas, nginx, nodejs, etherpad, dicas
editor: markdown
dateCreated: 2019-11-29T17:23:12.516Z
---

Veja nosso pad se desejar:


> **Versão ativa**
Etherpad versão **v.1.8.9**
Link: https://pad.aguas.ml
{.is-success}


<img src="/uploads/imagens-do-pad/print-pad-pedeagua-org.png" width="550" /> {.center}

> **Versão desativada**
Etherpad versão **v.1.6.6** 
Link: ~~https://pad.pedeagua.org~~
Desativada em **22/02/2021**
{.is-warning}

.
# Para instalar o Etherpad
Acompanhe, SEMPRE, o software no github
https://github.com/ether/etherpad-lite/blob/master/README.md

.
# Para atualizar o Etherpad
Pesquise de acordo com a forma que instalou e documentação das alterações realizadas, mas talvez o fluxo abaixo ajude:

```text
cd /opt/etherpad-lite
sudo systemctl stop etherpad
git stash push --include-untracked
git pull origin
./bin/run.sh
```
```text
su - etherpad -s /bin/bash
cd etherpad-lite
git pull origin
bin/run.sh
exit
```

.
## Lançamento teste durante install

```text
cd /opt/etherpad-lite/bin
./run.sh --root
```

.
# Anotações úteis para o Etherpad anterior 1.6.6

Leia todos os issues possíveis no git principal. Quase tudo já foi discutido, principalmente em inglês. Nele você encontra também mais detalhes sobre a instalação


https://github.com/ether/etherpad-lite/wiki


Infelizmente deu muito ruim para a gente este git, não foi legal em nossa máquina.


Com você com certeza pode ser diferente, vai que é bom


Para instalar no modo oficial:



```text
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
git clone --branch master https://github.com/ether/etherpad-lite.git && cd etherpad-lite && bin/run.sh
```

.
## Link mais atualizado da 1.6.6 que funcionou para a gente

https://github.com/muxator/etherpad-lite

https://github.com/muxator/etherpad-lite.git

Este git funcionou para o que desejávamos, novo tema e mais funções. Então tudou rodou bem depois que fizemos a instalação dele:


.
```text
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
git clone --branch master https://github.com/muxator/etherpad-lite.git && cd etherpad-lite && bin/run.sh
```

.
## Dicas de instalação no /opt que deu certo para os franceses e ajudou aqui

Link: http://reseaux85.fr/index.php?title=Etherpad_-_Edition_collaborative

**Importante**
```
node -v && nodejs -v && npm -v
```

.
## Skin maneira

Link: https://framagit.org/colibris/etherpad-skin-colibris-outilslibres


.
## Rollback para a versão 1.6.6
Caso precise fazer rollback par a versão 1.6.6 ou qualquer outro release

```
git checkout .
git checkout tags/1.6.6
rm -rf ./src/node_modules
rm -rf ./node_modules
rm package-lock.json
rm src/package-lock.json
./bin/run.sh
```

.
# Comandos úteis

**Configurar serviço na inicialização**

``` 
sudo nano /etc/systemd/system/etherpad.service
```


**Adicionar serviço no boot**

Inspirar no programa a seguir (alterar `/pasta_do_app` para a pasta onde você instalou o etherpad )

```
[Unit]
Description=Etherpad Collaborative Editor

[Service]
Type=simple
User=etherpad
Group=etherpad
WorkingDirectory=/pasta_do_app
ExecStart=/pasta_do_app/bin/run.sh
User=etherpad
Environment=NODE_ENV=production
Restart=always # use mysql plus a complete settings.json to avoid Service hold-$

[Install]
WantedBy=multi-user.target

```

Após as alterações reinicie o daemon

```
sudo systemctl daemon-reload
```

```
sudo systemctl enable etherpad
```

**Verificar versão de node, nodejs e npm**
``` 
node -v && nodejs -v && npm -v
```


**Instalar dependências node do etherpad**

``` 
./bin/installDeps.sh
```

**Iniciar, parar e reiniciar serviço**
```text
sudo systemctl start etherpad
sudo systemctl stop etherpad
sudo systemctl restart etherpad
```

**Exemplo de instalação de plugins**
```
npm install ep_adminpads
```

.
## Erros conhecidos

Não é possível administrar/ver os pads pelo admin até a v1.8.6

.
### Problemas apenas com MySQL e utf8mb4
**Solução:** https://github.com/ether/etherpad-lite/issues/3959