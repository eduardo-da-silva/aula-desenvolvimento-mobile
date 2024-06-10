---
title: 'Listagem de produtos'
permalink: /loja-virtual/listagem-produtos
---

# Chamada da API

Inicialmente, vamos criar um arquivo `.env` na raiz do projeto com a seguinte configuração:

```env
VITE_BACKEND_BASE_URL=http://localhost:8000
```

Quanto usamos o Vite para gerenciar nossos projetos, podemos criar variáveis de ambiente prefixadas com `VITE_` e acessá-las no código usando `import.meta.env.VITE_NOME_DA_VARIAVEL`. Neste caso, estamos criando uma variável chamada `VITE_BACKEND_BASE_URL` que armazena a URL base do nosso backend.

Feito isso, vamos realizar com a configuração global do pacote `axios`. Para isso, vamos criar o arquivo `src/plugins/axios.js` com o seguinte conteúdo:

```javascript
import axios from 'axios';
const BASE_URL = import.meta.env.VITE_BACKEND_BASE_URL;

axios.defaults.baseURL = `${BASE_URL}/api/`;
```

Note que estamos configurando a URL base da API FakeStore desenvolvida em Django, como informando no arquivo `.env`. Você pode querer usar outro servidor ou baixar o projeto e rodar localmente. Para isso, você precisará alterar apenas a URL base.

Em seguida, vamos criar uma classe para consultar a API. Para isso, vamos criar o arquivo `src/services/product.js` com o seguinte conteúdo:

```javascript
import axios from 'axios';

export default class ProductService {
  async getProducts() {
    const response = await axios.get('/products/');
    return response.data.results;
  }

  async getProductByCategory(category_id) {
    const response = await axios.get(`/products/?category__id=${category_id}`);
    return response.data.results;
  }
}
```

Neste caso, estamos criando um serviço para consultar a API FakeStore. Esse serviço possui dois métodos: `getProducts` que retorna todos os produtos e `getProductByCategory` que retorna os produtos de uma categoria específica.

# Configurando o serviço de gerenciamento de estados

Nos nossos exemplos, usaremos o gerenciamento de estados, com o Pinia, para fazer a interface entre a API e os componentes. Para isso, vamos criar o arquivo `src/stores/product.js` com o seguinte conteúdo:

```javascript
import { ref } from 'vue';
import { defineStore } from 'pinia';

import ProductService from '@/services/product';
const productService = new ProductService();

export const useProductStore = defineStore('product', () => {
  const products = ref([]);

  async function getProducts() {
    products.value = await productService.getProducts();
  }

  async function getProductsByCategory(category_id) {
    products.value = await productService.getProductByCategory(category_id);
  }

  return { products, getProducts, getProductsByCategory };
});
```

Neste arquivo, estamos criando um store para gerenciar os produtos. Esse store possui um objeto reativo `products` para armazenar os produtos. Além disso, possui dois métodos (ou _actions_): `getProducts` que chama o método `getProducts` do serviço e atualiza a lista de produtos e `getProductsByCategory` que chama o método `getProductByCategory` do serviço e atualiza a lista de produtos, nesse caso filtrando por categoria.

# Criando funções para formatação dos resultados

Se mandarmos listar os produtos diretamente na tela, veremos que a descrição é muito grande e o preço não está formatado. Para resolver isso, vamos criar funções de formatação. Para isso, vamos criar o arquivo `src/helpers/format.js` com o seguinte conteúdo:

```javascript
export const formatPrice = (price) =>
  `R$ ${price.toFixed(2).replace('.', ',')}`;
export const formatTitle = (title) => title.slice(0, 15) + '...';
export const formatDescription = (description) =>
  description.slice(0, 40) + '...';
```

Nesse caso estamos criando três funções de formatação: `formatPrice` que formata o preço do produto, `formatTitle` que limita o título do produto a 15 caracteres e `formatDescription` que limita a descrição do produto a 40 caracteres.

# Configurando o componente de listagem de produtos

Vamos criar o componente de listagem de produtos. Para isso, vamos criar o arquivo `src/components/ProductList.vue` com o seguinte conteúdo:

```vue
<script setup>
import { onMounted } from 'vue';
import { useProductStore } from '@/stores/product';

import { formatDescription, formatPrice, formatTitle } from '@/helpers/format';

const productStore = useProductStore();

async function getProducts() {
  await productStore.getProducts();
}

onMounted(async () => {
  await getProducts();
});
</script>

<template>
  <div class="product-list">
    <div v-if="productStore.products.length === 0">
      <p>Produtos não encontrados!!!</p>
    </div>
    <div
      v-for="product in productStore.products"
      :key="product.id"
      class="product-card"
    >
      <div class="product-img-wrapper">
        <img :src="product.image?.url" alt="product.name" />
        <i class="mdi mdi-heart-outline" />
      </div>
      <div class="product-title-price">
        <p>{{ formatTitle(product.title) }}</p>
        <p>{{ formatPrice(product.price * 1) }}</p>
      </div>
      <div class="product-description-stars">
        <p>{{ formatDescription(product.description) }}</p>
        <div class="stars">
          <i class="mdi mdi-star" size="20" />
          <i class="mdi mdi-star" size="20" />
          <i class="mdi mdi-star" size="20" />
          <i class="mdi mdi-star" size="20" />
          <i class="mdi mdi-star" size="20" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.product-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5rem;
  padding: 1rem;
}

.product-card {
  width: 225px;
  font-family: 'Belleza', sans-serif;
}

.product-img-wrapper {
  display: flex;
  justify-content: center;
  align-items: top;
  gap: 0.5rem;
  padding-top: 20px;
  margin-bottom: 1rem;
  background-color: #eeeeee;
  height: 201px;
}

.product-img-wrapper img {
  width: 153px;
  height: 170px;
  object-fit: cover;
}

.product-title-price {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.product-title-price p {
  font-weight: bold;
  font-size: 16px;
  color: #010101;
}

.product-description-stars {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}

.product-description-stars p {
  font-size: 12px;
  color: #535050;
}
</style>
```

# Configurando o componente de HomeView

Para finalizar, vamos configurar o componente `HomeView.vue` para exibir a listagem de produtos. Para isso, vamos editar o arquivo `src/views/HomeView.vue` com o seguinte conteúdo:

```vue
<script setup>
import ProductList from '@/components/ProductList.vue';
</script>

<template>
  <product-list />
</template>
```

Neste arquivo, estamos importando o componente `ProductList` e exibindo-o na tela.

<span style="display: flex; justify-content: space-between;"><span>[&lt; A loja virtual](. 'Voltar')</span><span>[Ajustes no cabeçalho e rodapé &gt;](cabecalho-rodape.html 'Próximo')</span></span>
