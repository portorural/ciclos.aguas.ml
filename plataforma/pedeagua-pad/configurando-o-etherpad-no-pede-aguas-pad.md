<!-- TITLE: Como configuramos o Etherpad da plataforma ÁguasML -->
<!-- SUBTITLE: Algumas informações relevantes sobre nossa instalação do Etherpad no Pede Água Pad -->

# Anotações úteis para o Etherpad

Veja nosso Pad antes de prosseguir: https://pad.aguas.pad


<img style="float: center" src="/uploads/imagens-do-pad/print-pad-pedeagua-org.png" width="550" /> {.center}



## Git principal, ler todos os issues possíveis

https://github.com/ether/etherpad-lite/wiki

Infelizmente deu muito ruim para a gente este git, não foi legal em nossa máquina.

Com você com certeza pode ser diferente, vai que é bom

Para instalar no modo oficial:


```text
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
git clone --branch master https://github.com/ether/etherpad-lite.git && cd etherpad-lite && bin/run.sh
```

https://github.com/muxator/etherpad-lite.git



## Link mais atualizado que funcionou para a gente

https://github.com/muxator/etherpad-lite

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

cd /opt/etherpad-lite/bin
./run.sh --root




# Para atualizar o Etherpad
cd /opt/etherpad-lite
git pull origin




## Comandos úteis

**Reiniciar serviço**

sudo systemctl restart etherpad



## Erros conhecidos

Não é possível administrar/ver os pads pelo admin