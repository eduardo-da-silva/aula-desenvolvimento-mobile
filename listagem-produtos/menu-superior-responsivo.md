---
title: 'Menu superior responsivo'
description: 'Cabeçalho com menu responsivo'
permalink: /listagem-produtos/menu-superior-responsivo
---

# Instalando dependências de ícones

Ao longo do tutorial, usaremos uma biblioteca de ícones. Nos nossos exemplos usaremos a `vue-material-design-icons`. A listagem de ícones disponíveis pode ser encontrada [aqui](https://pictogrammers.com/library/mdi/).

Para instalar a biblioteca, execute o comando a seguir:

```bash
npm install vue-material-design-icons
```

Agora, podemos importar os ícones individualmente a cada uso. Faremos alguns exemplos no decorrer do tutorial.

# Menu superior responsivo

Vamos, nesta etapa, criar um cabeçalho com um menu responsivo. Para isso, vamos criar um novo componente chamado `MenuSuperior.vue` na pasta `src/components` e adicionar o seguinte conteúdo:

Para facilitar a explicação, faremos a apresentação do código em partes: a primeira parte é o script, a segunda parte é o template e a terceira parte é o estilo.

## Script

A parte do script é responsável por importar os ícones e criar a lógica do menu responsivo. O código abaixo faz isso:

```vue
<script setup>
import { ref } from 'vue';

import CartPlus from 'vue-material-design-icons/CartPlus.vue';
import Account from 'vue-material-design-icons/Account.vue';
import Menu from 'vue-material-design-icons/Menu.vue';

const menuAberto = ref(false);
</script>
```

Note que importamos os ícones `CartPlus`, `Account` e `Menu` da biblioteca `vue-material-design-icons`. Além disso, criamos uma variável reativa chamada `menuAberto` que será responsável por controlar a abertura e o fechamento do menu tipo "hambúrguer", quando a aplicação estiver em um dispositivo móvel com tela pequena.

## Template

```vue
<template>
  <header>
    <div class="header--logo">
      <img src="@/assets/logoFakeStore.png" alt="Logo" />
      <h1>FakeStore</h1>
    </div>
    <nav>
      <ul :class="menuAberto ? 'menu' : ''">
        <li>Home</li>
        <li>Eletrônicos</li>
        <li>Jóias</li>
        <li>Masculino</li>
        <li>Feminino</li>
      </ul>
    </nav>
    <div class="header--icons">
      <Account />
      <CartPlus />
      <Menu class="menu-hamburger" @click="menuAberto = !menuAberto" />
    </div>
  </header>
</template>
```

No template, temos um cabeçalho com um logotipo, um menu e alguns ícones. O logotipo é uma imagem que está na pasta `src/assets`. Você já deve ter criado em outro momento. Caso ainda não o tenha, crie um arquivo chamado `logoFakeStore.png` na pasta `src/assets` e adicione uma imagem de sua preferência. O arquivo também pode ter outro nome, mas lembre-se de alterar o nome no código acima.

O menu é uma lista não ordenada com alguns itens. Os ícones são importados e utilizados diretamente no template.

Também criamos um bloco com ícones. O primeiro ícone é o de conta, o segundo é o de carrinho e o terceiro é o menu tipo "hambúrguer". O menu tipo "hambúrguer" é o que será responsável por abrir e fechar o menu quando a aplicação estiver em um dispositivo móvel com tela pequena. Também, ele ficará visível apenas nesses dispositivos.

## Estilo

```css
<style scoped>
header {
  background: #fff;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
  padding: 0.2rem 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header--logo {
  display: flex;
  align-items: center;
}
.header--logo img {
  width: 3rem;
  height: 3rem;
  margin-right: 0.5rem;
}
nav ul {
  display: flex;
  gap: 1rem;
}
nav li {
  list-style: none;
}

.header--icons {
  display: flex;
  gap: 1rem;
}
.menu-hamburger {
  display: none;
}

@media (max-width: 768px) {
  nav ul {
    display: none;
  }
  .menu-hamburger {
    display: block;
  }

  nav .menu {
    display: flex;
    flex-direction: column;
    position: absolute;
    background-color: rgba(255, 255, 255, 0.9);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
    border-radius: 10px;
    right: 0;
    text-align: right;
    padding: 10px 16px;
  }
  nav .menu li {
    display: block;
    margin-top: 12px;
  }
}
</style>
```

No estilo, temos a estilização do cabeçalho, do logotipo, do menu e dos ícones. Também temos a estilização do menu tipo "hambúrguer" para dispositivos móveis com tela pequena.

Note que usamos _media queries_ para estilizar o menu tipo "hambúrguer" apenas em dispositivos móveis com tela pequena.

Sugiro que você estude o código com calma e faça as alterações que achar necessárias para o seu projeto.

Agora que temos o cabeçalho com um menu responsivo, vamos alterar a view principal para exibir o cabeçalho. Abra o arquivo `src/App.vue` e altere o conteúdo para o seguinte:

```vue
<script setup>
import ListagemProdutos from '@/components/ListagemProdutos.vue';
import MenuSuperior from '@/components/MenuSuperior.vue';
</script>

<template>
  <MenuSuperior />
  <ListagemProdutos />
</template>
```

Incluímos o componente `MenuSuperior` antes do componente `ListagemProdutos`. Isso fará com que o cabeçalho seja exibido antes da listagem de produtos.

Agora que fizemos todas as alterações, vamos testar a aplicação. Execute o comando `npm run dev` e acesse a URL `http://localhost:5173/` ou o endereço que você está rodando o seu ambiente de desenvolvimento. Você deverá ver o cabeçalho com o menu responsivo e a listagem de produtos da API Fake Store.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Estilização Básica](estilizacao-basica.html 'Início')</span> <span>[Sumário &gt;](../ 'Próximo')</span></span>

```

```
