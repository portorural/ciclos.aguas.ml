---
title: Dicas de uso do FreeDNS
description: Dicas de uso com o FreeDNS
published: true
date: 2019-12-04T03:47:25.907Z
tags: plataforma, dns, free
---

# Usando o FreeDNS
Em nosso caso foi necessário o uso do FreeDNS para a instalação de um NextCloud no RaspberryPi, NextcloudPI

A seguir, algumas anotações que com certeza serão úteis

# Crie sua conta
Faça com calma, pode haver erros, como a impossibilidade de registrar o domínio que você escolheu

- Acesse https://freedns.afraid.org/signup/
- Preencha os campos com seu nome, ID, senha e email


# Senha HASH no FreeDNS
Faça login

- Acesse `Dynamic DNS >` o link direto pode ser https://freedns.afraid.org/dynamic/
- Ao lado do seu domínio na tabela de opções, haverá um link chamado Direct Link
- Com o botão direito copicole este link: `https://freedns.afraid.org/dynamic/update.php?XXXXXX`
- Use somente o que estiver após ponto de interrogação, é este seu hash