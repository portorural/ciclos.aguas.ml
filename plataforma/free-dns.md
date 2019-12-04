---
title: Dicas de uso do FreeDNS
description: Dicas de uso com o FreeDNS
published: true
date: 2019-12-04T04:53:43.292Z
tags: plataforma, dns, free, pi
---

# Usando o FreeDNS
Em nosso caso foi necessário o uso do FreeDNS para [a instalação de um NextCloud no RaspberryPi] (/plataforma/nextcloudpi), o NextcloudPI

A seguir, algumas anotações que com certeza serão úteis

# Crie sua conta
Faça com calma, pode haver erros, como a impossibilidade de registrar o domínio que você escolheu

- Acesse https://freedns.afraid.org/signup/
- Preencha os campos com seu nome, ID, senha e email

# Portas no roteador
Se estiver criando coisas, confirme sempre que as portas 80 e 443 estão liberadas em seu roteador

# Senha HASH no FreeDNS
Faça login

- Acesse `Dynamic DNS >` o link direto pode ser https://freedns.afraid.org/dynamic/
- Ao lado do seu domínio na tabela de opções, haverá um link chamado Direct Link
- Com o botão direito copicole este link, ele se parecerá com este:

> https://freedns.afraid.org/dynamic/update.php?`XXXXXXXXXX`

- Use somente o que estiver após o ponto de interrogação, é este seu hash