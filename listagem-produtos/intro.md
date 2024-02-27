---
title: 'Introdução à API Fake Store'
description: 'Conhecendo API Fake Store e instalando o Axios'
permalink: /listagem-produtos/
---

# Índice da aula

1. [Entendendo a API Fake Store](#entendendo-a-api-fake-store)
2. [Listagem de produtos](listagem-de-produtos.html)
3. [Estilização básica](estilizacao-basica.html)
4. [Menu Superior Responsivo](menu-superior-responsivo.html)

# Entendendo a API Fake Store

A API Fake Store é uma API que simula uma loja virtual. Ela possui endpoints para listar produtos, categorias, carrinho de compras, usuários, entre outros. Para este tutorial, vamos utilizar o endpoint de listagem de produtos.

A documentação da API Fake Store pode ser encontrada [aqui](https://fakestoreapi.com/docs). Note que no menu lateral, os endpoints estão divididos em grupos: `Products`, `Cart`, `User` e `Login`. Cada grupo possui um conjunto de endpoints que podem ser utilizados. Para cada endpoint é possível ver a URL, o método HTTP, os parâmetros e o corpo da requisição, e um modelo de resposta.

Sugiro que você dê uma olhada na documentação para entender melhor como a API funciona e, consequentemente, desenvolver outros recursos para a sua aplicação, diferente do que será feito neste tutorial.

# Instalando o Axios

Para fazer requisições HTTP, vamos utilizar o Axios. Para instalá-lo, execute o comando a seguir:

```bash
npm install axios
```

É importante ressaltar que o Axios é uma biblioteca que permite fazer requisições HTTP de forma fácil e eficiente. Ela é muito utilizada em projetos Vue.js, mas também pode ser utilizada em projetos React, Angular, entre outros.

Em vez de utilizar o Axios, você pode utilizar o Fetch API, que é nativa do JavaScript, mas o Axios é amplamente utilizado e possui, de forma geral, uma API mais simples e fácil de usar.

# Limpando o projeto e configuração de CSS

Antes de iniciarmos a listagem de produtos, vamos limpar o projeto. Para tal, vamos remover os componentes que não serão utilizados e fazer uma configuração básica do CSS. Inicialmente, podemos remover os componentes `HelloWorld.vue`, `TheWelcome.vue` e `WelcomeItem.vue` que estão na pasta `src/components/`. Também pode ser removida a pasta `src/components/icons`.

Vamos também editar o arquivo `App.vue` para que ele fique da seguinte forma:

```vue
<template>
  <span>Em breve</span>
</template>
```

Note que removemos os componentes que estavam sendo importados e utilizados no arquivo `App.vue`. Também removemos o conteúdo do `template` e adicionamos um texto simples, bem como removemos os blocos `script` e o `style`.

Em seguida, vamos fazer uma configuração básica do CSS. Para isso, abra o arquivo `src/assets/main.css` e substitua o conteúdo pelo seguinte:

```css
@import url('https://fonts.googleapis.com/css?family=Nunito:400,700&display=swap');
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background: #fdfdfd;
  font-family: 'Nunito', sans-serif;
  font-size: 1rem;
}
h1 {
  color: #e74c3c;
  margin-bottom: 0.5rem;
}
```

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](../ 'Início')</span> <span>[Listagem de produtos &gt;](listagem-de-produtos.html 'Próximo')</span></span>
