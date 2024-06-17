---
title: 'Ajustes na listagem de produtos'
permalink: /loja-virtual-adicionar-produtos/ajustes-listagem-produtos
---

# Ajustes na listagem de produtos

Com todas as etapas já desenvolvidas, precisamos agora adicionar um botão na tela de listagem de produtos para que o usuário possa adicionar um novo produto. Para isso, vamos adicionar um botão no cabeçalho da página de listagem de produtos.

Inicialmente, vamos editar o arquivo `src/components/ProductList.vue` e adicionar o botão de adicionar produto. Subtitua o código para o seguinte conteúdo:

```vue
<script setup>
import { onMounted, watch } from 'vue';
import { useProductStore } from '@/stores/product';

import HeartOutline from 'vue-material-design-icons/HeartOutline.vue';
import Star from 'vue-material-design-icons/Star.vue';
import { formatDescription, formatPrice, formatTitle } from '@/helpers/format';

const props = defineProps(['category_id']);
const productStore = useProductStore();

async function getProducts() {
  if (props.category_id) {
    await productStore.getProductsByCategory(props.category_id);
  } else {
    await productStore.getProducts();
  }
}

watch(
  () => props.category_id,
  async () => {
    await getProducts();
  },
);

onMounted(async () => {
  await getProducts();
});
</script>

<template>
  <div class="product-list">
    <router-link :to="{ name: 'ProductAdd' }">
      <button class="icon ">
        <i class="mdi mdi-plus" />
      </button>
    </router-link>
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
        <heart-outline />
      </div>
      <div class="product-title-price">
        <p>{{ formatTitle(product.title) }}</p>
        <p>{{ formatPrice(product.price * 1) }}</p>
      </div>
      <div class="product-description-stars">
        <p>{{ formatDescription(product.description) }}</p>
        <div class="stars">
          <star size="20" />
          <star size="20" />
          <star size="20" />
          <star size="20" />
          <star size="20" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.icon {
  background-color: #0a2668;
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;

  position: fixed;
  bottom: 12rem;
  right: 20px;
}

.icon:hover {
  background-color: #bac9e8;
  color: #0a2668;
}

.icon i {
  font-size: 2rem;
}

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

Note que fizemos poucas alterações. Apenas adicionamos um `RouterLink` para a rota de adicionar produtos e um botão com o ícone de adição. Além disso, ajustamos o estilo do botão e do ícone, para que fiquem posicionados no canto inferior direito da tela.

# Ajustes na rota

Para finalizar, precisamos adicionar a rota para a tela de adição de produtos. Para isso, edite o arquivo `src/router/index.js` e adicione a rota para a tela de adição de produtos. Substitua o código para o seguinte conteúdo:

```javascript
import { createRouter, createWebHistory } from 'vue-router';
import HomeView from '../views/HomeView.vue';
import LayoutLarge from '@/layouts/LayoutLarge.vue';

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: '',
      component: LayoutLarge,
      children: [
        {
          path: '',
          name: 'Home',
          component: HomeView,
        },
        {
          path: '/produtos/adicionar',
          name: 'ProductAdd',
          component: () => import('@/views/ProductAdd.vue'),
        },
        {
          path: '/produtos/categoria/:category_id',
          name: 'Category',
          component: () => import('@/views/CategoryView.vue'),
          props: true,
        },
        {
          path: '/login',
          name: 'Login',
          component: () => import('@/views/LoginView.vue'),
        },
      ],
    },
  ],
});

export default router;
```

Note que apenas adicionamos a rota com nome `ProductAdd`. Agora, ao clicar no botão de adicionar produto, o usuário será redirecionado para a tela de adição de produtos.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Formulário para criação de produtos](formulario-criacao-produtos.html 'Voltar')</span><span>[Sumário &gt;](.. 'Próximo')</span></span>
