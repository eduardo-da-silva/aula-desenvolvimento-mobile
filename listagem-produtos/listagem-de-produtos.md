---
title: 'Listagem de produtos'
description: 'Listagem de produtos usando a API Fake Store'
permalink: /listagem-produtos/listagem-de-produtos
---

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
      <h2>{% raw %}{{ produto.title }}{% endraw %}</h2>
      <p>{% raw %}{{ produto.description }}{% endraw %}</p>
      <p>{% raw %}{{ produto.price }}{% endraw %}</p>
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
  <ListagemProdutos />
</template>
```

# Testando a aplicação

Agora que fizemos todas as alterações, vamos testar a aplicação. Execute o comando `npm run dev` e acesse a URL `http://localhost:5173/` ou o endereço que você está rodando o seu ambiente de desenvolvimento. Você deverá ver a listagem de produtos da API Fake Store.

Você também pode visualizar em um dispositivo móvel, ou fazer o deploy para a web, para ver como a aplicação se comporta em diferentes dispositivos. Para fazer o deploy, você pode seguir os passos já estudados nas aulas anteriores.

Note que a listagem de produtos é bem simples e não possui nenhuma estilização. Isso é proposital, pois o foco desta etapa é mostrar como fazer requisições HTTP e exibir os dados na tela. A estilização e a responsividade da aplicação serão feitas a seguir.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. 'Início')</span> <span>[Estilização básica &gt;](estilizacao-basica.html 'Próximo')</span></span>
