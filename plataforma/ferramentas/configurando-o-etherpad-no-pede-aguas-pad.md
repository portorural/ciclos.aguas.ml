---
title: Como configuramos o Etherpad do Pad ÁguasML
description: Algumas informações relevantes sobre o etherpad-lite nv1.6.6 no Pad Águas Pad
published: true
date: 2022-08-31T15:08:19.769Z
tags: águas, plataforma, pad, ferramentas, nginx, nodejs, etherpad, dicas
editor: markdown
dateCreated: 2019-11-29T17:23:12.516Z
---

Veja nosso pad se desejar:


> **Versão ativa**
Etherpad-lite versão **v.1.8.18**
Link: https://pad.aguas.ml
{.is-success}


<p align="center">
  <img width="800" src="/uploads/imagens-do-pad/print-padaguas.png">
</p>


# Para instalar o Etherpad
Acompanhe, SEMPRE, o software no github: https://github.com/ether/etherpad-lite/

Link da wiki: https://github.com/ether/etherpad-lite/wiki
.
# Para atualizar o Etherpad
Pesquise de acordo com a forma que instalou e documentação das alterações realizadas, mas talvez o fluxo abaixo ajude:

```text
su - etherpad -s /bin/bash
cd etherpad-lite
systemctl stop etherpad
git pull origin
bin/run.sh
systemctl start etherpad
exit
```

.
## Atualizando da 1.8.9 para 1.8.14
Em nosso update da versão 1.8.9 para a 1.8.14 foi necessário a atualização do node e do das dependências

**Atualizando etherpad modo antigo**
```text
cd /opt/etherpad-lite
sudo systemctl stop etherpad
git stash push --include-untracked
git pull origin
./bin/run.sh
```

**Atualizando o Node**

```
sudo apt-get purge nodejs
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash - 
sudo apt-get install -y nodejs 
```

**Atualizar NodeJS**
Se você usa o **npm** veja como atualizar no Ubuntu

```
sudo npm cache clean -f
sudo npm install -g n
sudo n 12.22.4
```


**Verificar versão de node, nodejs e npm**
``` 
node -v && nodejs -v && npm -v
```


**Instalar dependências node do etherpad**

``` 
src/bin/installDeps.sh
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
> **Versão relevante ainda ativa**
Etherpad versão **v.1.6.6** 
Link: https://perola.aguas.ml
Desativada em **22/02/2021**
{.is-warning}

Leia dicas aqui: https://ciclos.aguas.ml/pt-br/plataforma/ferramentas/versao-antiga-etherpad-lite
.