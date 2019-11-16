<!-- TITLE: Nova Web Rádio -->
<!-- SUBTITLE: Uma nova web rádio -->


# Novidades da Rádio Bilu.ga

Vamos atualizar nossa rádio, melhorando os serviços!

Software escolhido é um fork do Airtime atual, atualizando em http://libretime.org/install/

# Notas de instalação

* Instalando Puttygen
* Pareando chaves e criando VPS
* Login ssh root@


### Adicionando novos repositórios

```text
sudo apt-get install git
sudo apt-get install curl
sudo apt-get install wget
sudo apt-get install nano
```


### Edite o arquivo /etc/apt/sources.list com estas linhas:


```text
sudo nano /etc/apt/sources.list


# Novos repositórios
deb http://archive.ubuntu.com/ubuntu bionic main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-updates main multiverse restricted universe
```


### Atualize e instale:

```text
sudo apt update
sudo apt-get upgrade
sudo apt-get install ufw
sudo ufw allow OpenSSH
sudo ufw enable
date
sudo timedatectl set-timezone America/Sao_Paulo
sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
sudo reboot
```




### Instalar PHP

```text
sudo apt-get install php
sudo apt-get install php-{bcmath,bz2,intl,gd,mbstring,mysql,zip,fpm}
```


https://soka.gitlab.io/RadioLibre/man/libretime_y_virtualbox/
https://www.p-node.org/documentation/hardwares/serveur-2