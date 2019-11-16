<!-- TITLE: Nova Web Rádio -->
<!-- SUBTITLE: Uma nova web rádio -->


# Novidades da Rádio Bilu.ga

Vamos atualizar nossa rádio, melhorando os serviços!

Software escolhido é um fork do Airtime atual, atualizando em http://libretime.org/install/

# Notas de instalação

* Instalando Puttygen
* Pareando chaves e criando VPS
* Login ssh root@

## Criar novo usuário


```text
sudo adduser biluga
sudo usermod -aG sudo biluga
sudo su - biluga
```

Realizar os próximos passos com o novo usuário criado. Guarde bem a senha que você utilizou.

### Adicionando o básico


```text
sudo apt-get install mc unp zip unzip sudo unp git ufw nano sudo git build-essential libssl-dev openssh-server
```

ou

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


### Atualize e verifique firewall:

```text
sudo apt update
sudo apt-get upgrade
sudo apt-get install ufw
sudo ufw allow OpenSSH
sudo ufw enable
date
sudo timedatectl set-timezone America/Sao_Paulo
timedatectl
sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
sudo reboot
```


### Instalar o Libretime


```text
git clone https://github.com/LibreTime/libretime.git
cd /libretime
sudo ./install
```



### Instalar PHP

```text
sudo apt-get install php
sudo apt-get install php-{bcmath,bz2,intl,gd,mbstring,mysql,zip,fpm}
```


## Referências


https://github.com/LibreTime/libretime/wiki/Installing-LibreTime-from-Git-on-a-stand-alone-VPS
https://devanswers.co/ubuntu-18-04-initial-server-setup/
https://soka.gitlab.io/RadioLibre/man/libretime_y_virtualbox/
https://www.p-node.org/documentation/hardwares/serveur-2