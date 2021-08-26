---
title: Configurando um servidor hídrico com Ubuntu
description: Um resumo prático para configurar um servidor Ubuntu, contendo dicas 
published: true
date: 2021-08-26T17:45:28.374Z
tags: plataforma, ubuntu, servidor
editor: markdown
dateCreated: 2019-11-29T17:23:17.187Z
---

Alguns passos comuns em muitas instalações de um servidor Ubuntu, nem sempre igual em todas as máquinas

## Instalando o Ubuntu para seu trabalho na nuvem
Sempre que puder acompanhe as novidades no [site oficial do Ubuntu](https://ubuntu.com/download)

A DigitalOcean tem um guia bacana para instalar rapidamente [ Ubuntu 18.04 LEMP](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-ubuntu-18-04), caso você ainda tenha dúvidas do que estamos falando.

Aqui sugerimos utilizar a versão 18.04 para sua plataforma, mas você pode pesquisar por tutoriais da versão 20.04 estável também. Consulte seu fornecedor para saber detalhes sobre a distro que eles oferecem para você.

Quase sempre o processo de instalação do Ubuntu em si é automatizado, cabe à você personalizar o sistema para seu uso.

Boa sorte!


# Configurando o básico
Primeiro, acesse sua máquina com os os dados SSH adequados.
A seguir algumas dicas de instalação de ferramentas que serão úteis durante o processo.

Antes de tudo, sincronize e atualize.

```
sudo apt update
sudo apt upgrade
dpkg-reconfigure tzdata
```

.
## Atualizando pacotes básicos necessários
Indicamos uma série de pacotes essenciais após a criação de sua instância Ubuntu

```
sudo apt-get install -y vim socat bash-completion apt-transport-https mc unp zip unzip sudo curl nano wget git build-essential libssl-dev openssh-server
```

Acreditamos que foi tudo tranquilo

.
## Atualize os repositórios

Edite o arquivo `/etc/apt/sources.list` e adicione novas linhas.

A seguir estão as linhas para o Ubuntu 18.04 e caso você deseja para o Ubuntu 16 Xenial, veja ao final da página nas referências

Você deverá saberá escolher a melhor opção para você se algo der errado

```text
sudo nano /etc/apt/sources.list
```
```text
# Novos repositorios
deb http://archive.ubuntu.com/ubuntu bionic main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-updates main multiverse restricted universe
```

Control + X  para salvar usando o nano, não se esqueça ;)

.
## Atualize o firewall SEMPRE
Atualize seu sistema com os novos repositórios, instale e configure o ufw

Primeiro atualiza
```text
sudo apt update
sudo apt-get upgrade
```

Depois instala ufw
```text
sudo apt-get install ufw
sudo ufw allow "OpenSSH"
sudo ufw allow "ApacheFull"
sudo ufw allow proto tcp from any to any port 80,443
sudo ufw status
sudo ufw enable
```

Atualiza de novo e reboota
```text

sudo apt update && sudo apt upgrade && sudo apt dist-upgrade
sudo reboot
```

Maneiro né?

.
## Ufw não ativo ao iniciar

Veja se funciona para você


```text
sudo apt remove iptables-persistent
sudo apt autoremove
```

Reinicie e verifique no navegador

.

# Dicas de ações comuns
Itens que são úteis durante este trabalho

.
## Novos sites em um servidor NGinx
Este modelo de websites pode ser útil se você usou o Nginx para seu servidor 

- [Modelo nginx de websites](https://linuxize.com/post/how-to-install-wordpress-with-nginx-on-ubuntu-18-04/)

.
## Criando novo usuário
Troque biluga pelo seu nome de usuário(a) desejável

```text
sudo adduser biluga
sudo usermod -aG sudo biluga
sudo su - biluga
```

Realizar os próximos passos com o(a) novo(a) usuário(a) criado(a). Guarde bem a senha que você utilizou.


.
## Limpando o HD
Você precisa analisar seu disco e limpar seus arquivos para liberar espaço no HD. Começaremos pelo `journal` e `logs`

```text
df -h
journalctl --disk-usage
journalctl --vacuum-size=100M
```
Para poder saber detalhes de onde estão outros arquivos, busque suas pastas mais usadas e utilize o comando `ncdu`

```text
cd /
sudo apt install ncdu
```

.
## Limpando o MongoDB
Você quer limpar os logs do `mongo` para liberar espaço no HD. Começaremos pelo `journal`

```text
service mongodb stop
rm -rf /var/lib/mongodb/journal/*
service mongodb start
```


.
## Alterando a hora
Caso seja preciso, no Ubuntu 18.04 use:

```text
date
sudo timedatectl set-timezone America/Sao_Paulo
timedatectl
```

Super simples.


.
## Instalar PHP
Se for preciso, você saberá

```text
sudo apt-get install php
sudo apt-get install php-{bcmath,bz2,intl,gd,mbstring,mysql,zip,fpm}
```

Instalará a versão mais estável, confirme os repositórios.

.
## Permissões de uso

Após criar pastas para cada site  `/var/www/seudominio.org/public_html` 

```text
cd /var/www
sudo mkdir seudominio.org/public_html
```
altere as permissões destas pastas
```text
sudo chown -R www-data:www-data /var/www/seudominio.org/public_html
```

Simples. Ou use:
```text
sudo chown -R $(whoami).$(whoami) /sua/pasta
```

.
## Permissões dos arquivos

Alterando permissões para rolar bem na web

Para arquivos use
```text
sudo find /your/location -type f -exec chmod 644 {} \; 
```
Para pastas use
```text
sudo find /your/location -type d -exec chmod 755 {} \;
```


Isso se não precisar de algo especial, consulte a sua documentação

.
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

.
## Editando /etc/hosts
Para adicionar novo site, edite o arquivo `hosts`

```text
sudo nano /etc/hosts
```

E adicione
```text
IP.AQUI.XXX.XXX  www.mysite.se mysite.se test.mysite.se
```

Reinicie seu servidor.


.
## Programas úteis de monitoramento

Instale e utilize programas para algumas atividades de manutenção cotidianas

```text
htop
ncdu
```

.
# Referências


https://github.com/LibreTime/libretime/wiki/Installing-LibreTime-from-Git-on-a-stand-alone-VPS
https://devanswers.co/ubuntu-18-04-initial-server-setup/
https://soka.gitlab.io/RadioLibre/man/libretime_y_virtualbox/
https://www.p-node.org/documentation/hardwares/serveur-2

https://wordpress.org/plugins/radio-station/


## Source Ubuntu 16 Xenial
Adicione as seguintes linhas em seu arquivo `/etc/apt/sources.list`

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

.
## Source Ubuntu 18.04 Bionic

Link: https://gist.github.com/h0bbel/4b28ede18d65c3527b11b12fa36aa8d1

.
## Instalando SSL no admin

Instalação alternativa, veja se funciona para você

Link Perfect Server: https://www.howtoforge.com/tutorial/perfect-server-ubuntu-18.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/
Link securing ISPConfig: https://www.howtoforge.com/tutorial/securing-ispconfig-3-with-a-free-lets-encrypt-ssl-certificate/

Reinicie e verifique no navegador

.