---
title: 'Listagem de produtos'
description: 'Listagem de produtos usando a API Fake Store'
permalink: /listagem-produtos/
---

# Entendendo a API Fake Store

A API Fake Store é uma API que simula uma loja virtual. Ela possui endpoints para listar produtos, categorias, carrinho de compras, usuários, entre outros. Para este tutorial, vamos utilizar o endpoint de listagem de produtos.

# Instalando o Axios

Para fazer requisições HTTP, vamos utilizar o Axios. Para instalá-lo, execute o comando a seguir:

```bash
npm install axios
```

# Listagem de produtos

Agora que temos o Axios instalado, vamos criar uma listagem de produtos. Para isso, crie um novo arquivo chamado `ListagemProdutos.vue` na pasta `src/components` e adicione o seguinte conteúdo:

```vue
<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const produtos = ref([]);

onMounted(async () => {
  const response = await axios.get('https://fakestoreapi.com/products');
  produtos.value = response.data;
});
</script>

<template>
  <div>
    <h1>Produtos</h1>
    <div v-for="produto in produtos" :key="produto.id">
      <h2>{{ produto.title }}</h2>
      <p>{{ produto.description }}</p>
      <p>{{ produto.price }}</p>
      <img :src="produto.image" :alt="produto.title" />
    </div>
  </div>
</template>
```

# Alterando a view principal

Agora que temos a listagem de produtos, vamos alterar a view principal para exibir a listagem. Abra o arquivo `src/views/HomeView.vue` e altere o conteúdo para o seguinte:

```vue
<script setup>
import ListagemProdutos from '@/components/ListagemProdutos.vue';
</script>

<template>
  <div>
    <ListagemProdutos />
  </div>
</template>
```

# Limpando o projeto

Agora que temos a listagem de produtos, podemos remover os componentes `HelloWorld.vue`, `TheWelcome.vue` e `WelcomeItem.vue` que estão na pasta `src/components/`. Também pode ser removida a pasta `src/components/icons`.

# Criando

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](../ 'Início')</span> <span>[??? &gt;](???.html 'Próximo')</span></span>
