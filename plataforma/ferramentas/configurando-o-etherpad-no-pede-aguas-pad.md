---
title: Como configuramos o Etherpad da plataforma ÁguasML
description: Algumas informações relevantes sobre nossa instalação do Etherpad no Pede Água Pad
published: true
date: 2020-06-27T12:15:55.800Z
tags: águas, plataforma, pad, ferramentas, nginx, nodejs, etherpad, dicas
editor: markdown
---

# Anotações úteis para o Etherpad

Veja nosso Pad antes de prosseguir: https://pad.aguas.pad


<img src="/uploads/imagens-do-pad/print-pad-pedeagua-org.png" width="550" /> {.center}



## Leia todos os issues possíveis no git principal

Quase tudo já foi discutido, principalmente em inglês. Nele você encontra também mais detalhes sobre a instalação


https://github.com/ether/etherpad-lite/wiki


Infelizmente deu muito ruim para a gente este git, não foi legal em nossa máquina.


Com você com certeza pode ser diferente, vai que é bom


Para instalar no modo oficial:



```text
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
git clone --branch master https://github.com/ether/etherpad-lite.git && cd etherpad-lite && bin/run.sh
```





## Link mais atualizado que funcionou para a gente

https://github.com/muxator/etherpad-lite

https://github.com/muxator/etherpad-lite.git

Este git funcionou para o que desejávamos, novo tema e mais funções. Então tudou rodou bem depois que fizemos a instalação dele:




```text
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
git clone --branch master https://github.com/muxator/etherpad-lite.git && cd etherpad-lite && bin/run.sh
```


## Instalação no /opt que deu certo para os franceses e ajudou aqui

http://reseaux85.fr/index.php?title=Etherpad_-_Edition_collaborative




## Skin maneira

https://framagit.org/colibris/etherpad-skin-colibris-outilslibres




# Lançamento teste durante install

```text
cd /opt/etherpad-lite/bin
./run.sh --root
```




# Para atualizar o Etherpad
```text
cd /opt/etherpad-lite
git pull origin
```


.
## Rollback para a versão 1.6.6
```
git checkout .
```
``` 
git checkout tags/1.6.6
```
``` 
rm -rf ./src/node_modules
```
``` 
rm -rf ./node_modules
```
```
rm package-lock.json
```
```
rm src/package-lock.json
```
``` 
./bin/run.sh
```


.
## Comandos úteis

**Configurar serviço na inicialização**

``` 
./bin/installDeps.sh
```


**Instalar dependências**

``` 
./bin/installDeps.sh
```


**Verificar versão de node, nodejs e npm**
``` 
node -v && nodejs -v && npm -v
```


**Reiniciar serviço**
```text
sudo systemctl restart etherpad
```

**Exemplo de instalação de plugins**
```
npm install ep_adminpads
```

.
## Erros conhecidos

Não é possível administrar/ver os pads pelo admin