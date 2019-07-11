<!-- TITLE: Configurando O Etherpad No Pede Aguas Pad -->
<!-- SUBTITLE: Algumas informações relevantes sobre nossa instalação do Etherpad no Pede Águas Pad -->

# Anotações úteis para o Etherpad

Veja noss Pad antes de prosseguir: https://pad.aguas.pad

## Git principal, ler todos os issues possíveis

https://github.com/ether/etherpad-lite/wiki

Para instalar:

```text
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
git clone --branch master https://github.com/ether/etherpad-lite.git && cd etherpad-lite && bin/run.sh
```

https://github.com/muxator/etherpad-lite.git

## Link GitHub atualizado que funcionou para a gente

https://github.com/muxator/etherpad-lite

Este git funcionou para o que desejávamos, novo tema e mais funções


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

sudo systemctl restart etherpad

## Erros conhecidos

Não é possível administrar/ver os pads pelo admin