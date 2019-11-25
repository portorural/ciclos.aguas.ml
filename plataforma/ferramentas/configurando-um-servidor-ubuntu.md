<!-- TITLE: Configurando Um Servidor Ubuntu -->
<!-- SUBTITLE: Um resumo prático para configurar um servidor Ubuntu -->


Alguns passos comuns em muitas instalações de um servidor Ubuntu, nem sempre igual em todas as máquinas

# Configurando o básico
Instale ferramentas que serão úteis durante o processo

```text
sudo apt-get install mc unp zip unzip sudo curl nano wget git build-essential libssl-dev openssh-server
```

Acreditamos que foi tudo tranquilo

## Atualize os repositórios

Você saberá escolher a melhor opção para você se algo der errado


### Edite o arquivo /etc/apt/sources.list com estas linhas:

Adicione novas linhas. A seguir estão as linhas para o Ubuntu 18.04 e caso você deseja para o Ubuntu 16 Xenial, veja ao final da página nas referências


```text
sudo nano /etc/apt/sources.list


# Novos repositorios
deb http://archive.ubuntu.com/ubuntu bionic main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-updates main multiverse restricted universe
```

Control + X  para salvar usando o nano, não se esqueça ;)


## Atualize o firewall SEMPRE
Atualize seu sistema com os novos repositórios, instale e configure o ufw

```text
# Primeiro atualiza

sudo apt update
sudo apt-get upgrade

# Depois instala ufw

sudo apt-get install ufw
sudo ufw allow "OpenSSH"
sudo ufw allow "ApacheFull"
sudo ufw enable

# Atualiza de novo e reboota

sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
sudo reboot
```

Maneiro né?

## Criando novo usuário
Troque biluga pelo nomme de usuário desejável

```text
sudo adduser biluga
sudo usermod -aG sudo biluga
sudo su - biluga
```

Realizar os próximos passos com o novo usuário criado. Guarde bem a senha que você utilizou.


# Possíveis itens de suporte
Itens que foram úteis durante este trabalho

## Alterando a hora
Caso seja preciso, no Ubuntu 18.04 use:

```text
date
sudo timedatectl set-timezone America/Sao_Paulo
timedatectl
```

Super simples.


## Ufw não ativo ao iniciar

Veja se funciona para você


```text
sudo apt remove iptables-persistent
sudo apt autoremove
```

Reinicie e verifique no navegador


## Instalar PHP
Se for preciso, você saberá

```text
sudo apt-get install php
sudo apt-get install php-{bcmath,bz2,intl,gd,mbstring,mysql,zip,fpm}
```

Instalará a versão mais estável, confirme os repositórios.

## Permissões de uso

Após criar pastas para cada site [ /var/www/seudominio.org/public_html ] altere as permissões destas pastas

```text
sudo chown -R www-data:www-data /var/www/seudominio.org/public_html
```

Simples

## Permissões dos arquivos

Alterando permissões para rolar bem na web


```text
# Para arquivos use
sudo find /your/location -type f -exec chmod 644 {} \; 

# Para pastas use
sudo find /your/location -type d -exec chmod 755 {} \;
```


Isso se não precisar de algo especial, consulte a sua documentação

## Comprimir e extrair coisas

Comprimir

```text
tar -zcvf archive-name.tar.gz directory-name
```


Extrair


```text
tar -zxvf archive-name.tar.gz
```

Simplão de tudo

## Editando [ /etc/hosts ]
Para adicionar novo site

```text
sudo nano /etc/hosts

#Adicione

IP.AQUI.XXX.XXX  www.mysite.se mysite.se test.mysite.se

```


Editando o arquivo /etc/hosts





# Referências


https://github.com/LibreTime/libretime/wiki/Installing-LibreTime-from-Git-on-a-stand-alone-VPS
https://devanswers.co/ubuntu-18-04-initial-server-setup/
https://soka.gitlab.io/RadioLibre/man/libretime_y_virtualbox/
https://www.p-node.org/documentation/hardwares/serveur-2

https://wordpress.org/plugins/radio-station/


## Source list Ubuntu 16 Xenial


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