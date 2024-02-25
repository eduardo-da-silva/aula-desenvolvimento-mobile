---
title: 'Estilização básica'
description: 'Estilização básica e responsividade na Listagem de produtos'
permalink: /listagem-produtos/estilizacao-basica
---

# Alterações no bloco de template

Vamos adicionar um estilo básico na listagem de produtos. Para isso, vamos fazer uma pequena alteração no bloco de `template` do arquivo `ListagemProdutos.vue` e adicionar classes nas tags HTML. Abra o arquivo `src/components/ListagemProdutos.vue` e altere o conteúdo para o seguinte:

```vue
<template>
  <div>
    <h1>Produtos</h1>
    <div class="container">
      <div class="card" v-for="produto in produtos" :key="produto.id">
        <h1 class="card--title">{% raw %}{{ produto.title }}{% endraw %}</h1>
        <p>{% raw %}{{ produto.description }}{% endraw %}</p>
        <p>{% raw %}{{ formatPrice(produto.price) }}{% endraw %}</p>
        <img class="card--avatar" :src="produto.image" :alt="produto.title" />
      </div>
    </div>
  </div>
</template>
```

Note que adicionamos a classe `container` na `div` que envolve a listagem de produtos, e a classe `card` na `div` que envolve cada produto. Também adicionamos as classes `card--title` e `card--avatar` nas tags `h1` e `img`, respectivamente.

Além disso também adicionamos um método `formatPrice` que será utilizado para formatar o preço dos produtos. Vamos adicionar esse método no bloco de `script setup` do arquivo `ListagemProdutos.vue`.

# Alterações no bloco de script

Precisamos adicionar o método `formatPrice` no bloco de `script setup` do arquivo `ListagemProdutos.vue`. Abra o arquivo `src/components/ListagemProdutos.vue` e altere o conteúdo para o seguinte:

```vue
<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
const produtos = ref([]);

onMounted(async () => {
  const response = await axios.get('https://fakestoreapi.com/products');
  produtos.value = response.data;
});

const formatPrice = (price) => `R$ ${price.toFixed(2).replace('.', ',')}`;
</script>
```

Note que adicionamos o método `formatPrice` no bloco de `script setup`. Esse método recebe um parâmetro `price` e retorna uma string formatada com o preço do produto.

# Alterações no bloco de estilo

Por fim, vamos adicionar um estilo básico no bloco de `style` do arquivo `ListagemProdutos.vue`. Abra o arquivo `src/components/ListagemProdutos.vue` e adicione o seguinte conteúdo:

```css
<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  align-items: center;
  margin: auto;
  padding: 1rem 0;
}
.card {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: column;
  width: 15rem;
  height: 25rem;
  background: #fff;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
  border-radius: 10px;
  margin: auto;
  overflow: hidden;
}
.card--avatar {
  width: 100%;
  height: 17rem;
  object-fit: cover;
  margin-bottom: 0.5rem;
}
.card--title {
  color: #222;
  font-weight: 700;
  text-transform: capitalize;
  font-size: 1.1rem;
  margin-top: 0.5rem;
}
</style>
```

# Testando a aplicação

Agora, podemos novamente testar a aplicação na web e em dispositivos móveis. Eu sugiro que você sempre faça testes em diferentes dispositivos para garantir que a aplicação está funcionando corretamente.

Você pode fazer isso usando as ferramentas de desenvolvedor do navegador, ou utilizando um dispositivo físico, acessando a URL da aplicação publicada na web. Nas nossas aulas, estamos publicando a aplicação na Vercel, mas você pode utilizar outras plataformas.

Note que a listagem de produtos não está otimizada para dispositivos móveis. Isso será feito a seguir.

# Adicionando uma responsividade básica

Para adicionar uma responsividade básica, vamos fazer uma pequena alteração no bloco de estilo do arquivo `ListagemProdutos.vue`. Abra o arquivo `src/components/ListagemProdutos.vue`, procure o bloco de `style` e adicione o seguinte conteúdo (além do que já existe):

```css
<style scoped > @media (max-width: 768px) {
  .container {
    gap: 0.5rem;
  }
  .card {
    width: 92%;
  }
}

@media (min-width: 768px) and (max-width: 1024px) {
  .card {
    width: 22rem;
  }
}
```

Nesse caso, estamos utilizando _media queries_ para definir o espaçamento entre os produtos e o tamanho dos cards em diferentes tamanhos de tela. Note que estamos utilizando valores arbitrários, mas você pode ajustar de acordo com a necessidade da sua aplicação.

Criamos dois _breakpoints_: um para telas menores que 768px e outro para telas entre 768px e 1024px. Note que estamos utilizando o valor de 768px como _breakpoint_ para telas menores, representando dispositivos como smartphones, e o valor de 1024px como _breakpoint_ para telas intermediárias, representando dispositivos como tablets. Você pode ajustar esses valores de acordo com a necessidade da sua aplicação.

# Testando a aplicação

Sugiro que você teste a aplicação novamente, agora em diferentes dispositivos, para garantir que a responsividade está funcionando corretamente.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Listagem de produtos](listagem-de-produtos.html 'Início')</span> <span>[Menu superior responsivo &gt;](menu-superior-responsivo.html 'Próximo')</span></span>
