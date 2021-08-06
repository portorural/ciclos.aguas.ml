---
title: Anotações de versões anteriores do EtherpadLite
description: Anotações de updatea até a versão 1.6.6
published: true
date: 2021-08-06T04:10:17.312Z
tags: pad, nodejs, etherpad, ubuntu, etherpad-lite
editor: markdown
dateCreated: 2021-08-06T03:33:09.773Z
---

# Anotações úteis para o Etherpad anterior 1.6.6

**Versão mais atual**: https://ciclos.aguas.ml/plataforma/ferramentas/configurando-o-etherpad-no-pede-aguas-pad

Leia todos os issues possíveis no git principal. Quase tudo já foi discutido, principalmente em inglês. Nele você encontra também mais detalhes sobre a instalação


https://github.com/ether/etherpad-lite/wiki


Infelizmente deu muito ruim para a gente este git, não foi legal em nossa máquina.


Com você com certeza pode ser diferente, vai que é bom


Para instalar no modo oficial:



```
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
## Lançamento teste durante install

```text
cd /opt/etherpad-lite/bin
./run.sh --root
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

.
### Se você executar o MySQL, mude seu banco de dados para usar MyISAM em vez de InnoDB
**Solução:** https://github.com/ether/etherpad-lite/wiki/Converting-from-InnoDB-to-MyISAM