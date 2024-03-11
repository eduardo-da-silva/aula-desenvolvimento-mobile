---
title: 'Editando o HomeView para integrar ao Vue Router'
description: 'Editando o HomeView para integrar ao Vue Router'
permalink: /componentes-dinamicos/editando-homeview
---

# Editando o HomeView

Vamos agora editar o arquivo `src/views/HomeView.vue` para que ele renderize o componente de Listagem de Produtos que já fizemos anteriormente. Nos exemplos que fizemos no tutorial, embora tenhamos instalado o vue-router, não estamos aplicando o seu uso. O objetivo é fazer, nesta etapa, esta integração.

Para isso, edite o arquivo `src/views/HomeView.vue` e deixe o conteúdo como segue:

```html
<script setup>
  import ListagemProdutos from '@/components/ListagemProdutos.vue';
</script>

<template>
  <ListagemProdutos />
</template>

<style scoped></style>
```

Note que estamos importando o componente `ListagemProdutos` e renderizando-o diretamente no bloco de _template_ do componente `HomeView`.

# Configurando o Vue Router

Agora, vamos configurar o Vue Router para que o componente `HomeView` seja renderizado quando acessarmos a rota raiz do aplicativo. Essa configuração já deve estar feita no arquivo `src/router/index.js`. Contudo, vamos confirmar que o conteúdo desse arquivo está como segue:

```js
import { createRouter, createWebHistory } from 'vue-router';
import HomeView from '../views/HomeView.vue';

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: 'home',
      component: HomeView,
    },
  ],
});

export default router;
```

Talvez você já tenha outros componentes de rota, portanto garanta que a sua alteração não afetará o funcionamento do seu projeto.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Criando os arquivos de menu superior](criando-arquivos-menu-superior.html 'Voltar')</span> <span>[Configurando o composable de responsividade &gt;](configurando-composable-responsividade.html 'Próximo')</span></span>
