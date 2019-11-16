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


## Adicionando o básico
Instale ferramentas que serão úteis durante o processo

```text
sudo apt-get install mc unp zip unzip sudo curl git ufw nano wget git build-essential libssl-dev openssh-server
```

ou

```text
sudo apt-get install git
sudo apt-get install curl
sudo apt-get install wget
sudo apt-get install nano
```

Acreditamos que foi tudo tranquilo e você souber escolher a melhor opção para você


### Edite o arquivo /etc/apt/sources.list com estas linhas:

Adicione novas linhas. A seguir estão as linhas para o Ubuntu 18.04 e caso você deseja para o Ubuntu 16 Xenial, veja ao final da página nas referências


```text
sudo nano /etc/apt/sources.list


# Novos repositórios
deb http://archive.ubuntu.com/ubuntu bionic main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-updates main multiverse restricted universe
```

Control + X  para salvar usando o nano, não se esqueça ;)

### Atualize e verifique firewall:
Atualizei seu sistema com os novos repositórios e instale e configure o ufw

```text
sudo apt update
sudo apt-get upgrade
sudo apt-get install ufw
sudo ufw allow OpenSSH
sudo ufw enable
sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
sudo reboot
```

Maneiro né?

### Data no Ubuntu 18.04
Caso seja preciso

```text
date
sudo timedatectl set-timezone America/Sao_Paulo
timedatectl
```

Super simples.

## Instalar o Libretime


```text
git clone https://github.com/LibreTime/libretime.git
cd /libretime
sudo ./install
```


Digite Y e aperte  ENTER quando preciso.

E aguarde

### Instalar PHP
Se for preciso, você saberá

```text
sudo apt-get install php
sudo apt-get install php-{bcmath,bz2,intl,gd,mbstring,mysql,zip,fpm}
```

A seguir outros possíveis "erros"


```text
sudo a2dismod mpm_event
sudo a2enmod mpm_prefork
```


Pasta de armazenamento do Libretime


```text
/srv/airtime/stor
```

Fuce

## Referências


https://github.com/LibreTime/libretime/wiki/Installing-LibreTime-from-Git-on-a-stand-alone-VPS
https://devanswers.co/ubuntu-18-04-initial-server-setup/
https://soka.gitlab.io/RadioLibre/man/libretime_y_virtualbox/
https://www.p-node.org/documentation/hardwares/serveur-2



### Source list Ubuntu 16 Xenial


```text
#deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted

deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe

deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse

deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

#deb http://archive.canonical.com/ubuntu xenial partner
#deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
#deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted

deb http://security.ubuntu.com/ubuntu xenial-security universe
#deb-src http://security.ubuntu.com/ubuntu xenial-security universe

deb http://security.ubuntu.com/ubuntu xenial-security multiverse
#deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```
