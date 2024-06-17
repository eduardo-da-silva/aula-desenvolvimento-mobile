---
title: 'Tutorial da loja virtual - adicionar produtos'
description: 'Adicionando produtos e categorias'
permalink: /loja-virtual-adicionar-produtos/
---

# Índice da aula

1. [Camada de serviço](camada-servico.html)
2. [Camada de armazenamento](camada-armazenamento.html)
3. [Modal de criação de categorias](modal-criacao-categorias.html)
4. [Formulário de criação de produtos](formulario-criacao-produtos.html)
5. [Ajustes na listagem de produtos](ajustes-listagem-produtos.html)

# O que faremos agora?

Até então, criamos a estrutura do projeto e organizamos o layout da aplicação. Também, nossa aplicação já está fazendo uma listagem de produtos e realizando a autenticação do usuário.

Agora, vamos adicionar produtos e categorias à nossa loja virtual. Para isso, vamos criar um formulário para adicionar produtos e categorias e exibir esses dados na listagem de produtos.

No _backend_ que estamos utilizando, já temos a API pronta para adicionar produtos e categorias. Vamos então criar um formulário para adicionar esses dados. Também a API considera que usuários não autenticados não podem adicionar produtos e categorias, mas podem visualizar os produtos.

# Preparando um backend

Para validar o funcionamento do que faremos nas aulas seguintes, é importante que você tenha um backend que forneça os dados para a aplicação. Você mesmo pode desenvolver o seu backend ou usar um já pronto.

Para que possamos criar o projeto, vamos considerar ainda o uso de um backend feito em Django com Django Rest Framework. Para facilitar o desenvolvimento, vamos utilizar o Docker para criar o ambiente de desenvolvimento. O código fonte do backend está disponível neste [repositório] (https://github.com/eduardo-da-silva/fakestore-backend-drf/). Você pode rodar o repositório localmente ou utilizar uma imagem Docker, que já deixei pronta para você. As orientações para uso do projeto estão disponíveis no README do repositório.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](../ 'Início')</span> <span>[Criando a camada de serviço &gt;](camada-servico.html 'Próximo')</span></span>
