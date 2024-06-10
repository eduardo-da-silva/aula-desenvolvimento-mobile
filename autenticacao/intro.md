---
title: 'Autenticação em PWA'
description: 'Autenticação em PWA - Fake Store'
permalink: /autenticacao/
---

# Autenticação em PWA

Agora, vamos adicionar a funcionalidade de autenticação ao nosso PWA. A autenticação pode ser feita de várias maneiras, como por exemplo, com e-mail e senha, com redes sociais, com biometria, entre outras. Neste exemplo, vamos utilizar a autenticação usando uma plataforma chamada Passage.

A Passage é uma plataforma de autenticação que permite que você adicione autenticação em sua aplicação de forma simples e rápida. Ela oferece uma série de recursos, como autenticação com redes sociais, autenticação com biometria, entre outros. Nos exemplos que iremos desenvolver, vamos considerar que a integração do Passage já foi realizada com a camada de backend, no nosso caso, o Django com o Django Rest Framework.

Um recurso interessante da Passage é a possibilidade de se autenticar com biometria. Para isso, é necessário que o dispositivo do usuário tenha suporte a biometria.

Para que possamos criar o projeto, vamos considerar ainda o uso de um backend feito em Django com Django Rest Framework. Para facilitar o desenvolvimento, vamos utilizar o Docker para criar o ambiente de desenvolvimento. O código fonte do backend está disponível neste [repositório] (https://github.com/eduardo-da-silva/fakestore-backend-drf/). Você pode rodar o repositório localmente ou utilizar uma imagem Docker, que já deixei pronta para você. As orientações para uso do projeto estão disponíveis no README do repositório.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](../ 'Início')</span> <span>[Configuração do Passage &gt;](configuracao-passage.html 'Próximo')</span></span>
