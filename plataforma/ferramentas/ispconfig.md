---
title: Usando o ISPConfig 
description: Como usamos o ISPConfig em situações específicas
published: true
date: 2020-07-14T20:31:53.125Z
tags: software, ubuntu, gestão, gnu
editor: markdown
---

# Como usamos o ISPConfig
Em alguns momentos é útil contar com uma distribuição capaz de configurar, automaticamente, sites, emails, banco de dados com um script de instalação simples e fácil manutenção, principalmente pelo belo ambiente visual de gestão

Com o ISPConfig em algo próximo de 2h (ou menos) você já está com um site provido do necessário.


Site: https://www.ispconfig.org
Documentação oficial: https://www.ispconfig.org/documentation/
Fórum:  https://www.howtoforge.com/community/#ispconfig-3.23


.
## Dicas de uso
Seguem algumas anotações úteis no dia a dia

.
### Para atualizar
Esperamos que você não use o usuário *root* costumeiramente, então utilize o `sudo`

Digite `yes` para *Reconfigure Services* 

```
sudo ispconfig_update.sh
```

.
### Para reinstalar o php do ISPConfig
Digite `yes` para *Reconfigure Services* 

```
cd /tmp
wget https://ispconfig.org/downloads/ISPConfig-3.1.15p2.tar.gz
tar xvfz ISPConfig-3.1.15p2.tar.gz
cd ispconfig3_install/install
php -q update.php
```

Após isso, verifique todas as suas entradas do php no ambiente visual do ISPConfig, nas `Configurações de Servidor`


.
### Comandos relacionados
Possíveis comandos para reiniciar serviços em ambientes Debian/Ubuntu

```
service bastille-firewall restart
service apache2 restart
service postfix restart
service pure-ftpd-mysql restart
service mailman restart
service jailkit restart
service dovecot restart
service spamassassin restart
service bind9 restart
```
