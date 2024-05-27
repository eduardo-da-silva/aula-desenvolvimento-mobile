---
title: 'Ajustes no cabeçalho e rodapé'
permalink: /loja-virtual/cabecalho-rodape
---

# Criando um componente para o logo

Faremos um componente para mostrar a logotipo e o nome da loja. Este componente poderá ser reutilizado em várias partes da aplicação e também em vários tamanhos de tela e layouts. Para isso, vamos criar o arquivo `src/components/templates/LogoTitle.vue` com o seguinte conteúdo:

```vue
<script setup></script>
<template>
  <div class="logo">
    <img src="@/assets/logo.png" alt="FakeStore Logo" />
    <h2>FakeStore</h2>
  </div>
</template>

<style scoped>
.logo {
  display: flex;
  padding-left: 3rem;
  gap: 1rem;
  align-items: center;
}

.logo img {
  width: 3rem;
  height: 3rem;
  border-radius: 50%;
  object-fit: cover;
}

.logo h2 {
  font-family: 'Belleza', sans-serif;
  font-weight: 400;
  font-style: normal;
}
</style>
```

Neste arquivo, estamos criando um componente para exibir o logotipo e o nome da loja. Estamos usando a tag `img` para exibir o logotipo e a tag `h2` para exibir o nome da loja.

Nos ajustes de CSS estamos alinhando os elementos horizontalmente, definindo um espaçamento entre eles e estilizando o texto.

# Ajuste no cabeçalho de telas grandes

Vamos agora configurar o cabeçalho da aplicação para telas grandes. Para isso, vamos editar o arquivo `src/componentes/templates/large/LargeHeader.vue`, com o seguinte conteúdo:

```vue
<script setup></script>

<template>
  <div class="icons">
    <i class="mdi mdi-magnify" />
    <i class="mdi mdi-account-circle-outline" />
    <i class="mdi mdi-cart-outline" />
  </div>
</template>

<style scoped>
.icons {
  display: flex;
  gap: 1rem;
  align-items: center;
  font-size: 1.7rem;
}
</style>
```

Neste arquivo, estamos criando um componente para exibir os ícones de busca, perfil e carrinho no cabeçalho da aplicação. Estamos usando a tag `i` para exibir os ícones da biblioteca Material Design Icons. O tamanho dos ícones é definido no CSS, bem como o espaçamento entre eles e o alinhamento horizontal.

Note que ainda não adicionamos funcionalidade aos ícones, apenas os exibimos na tela.

# Ajuste no rodapé de telas grandes

Agora vamos configurar o rodapé da aplicação para telas grandes. Para isso, vamos editar o arquivo `src/componentes/templates/large/LargeFooter.vue`, com o seguinte conteúdo:

```vue
<script setup></script>
<template>
  <div class="links">
    <RouterLink to="/">Help</RouterLink>
    <RouterLink to="/">Contact Us</RouterLink>
    <RouterLink to="/">Privacy & Terms</RouterLink>
  </div>
  <div class="icons">
    <i class="mdi mdi-facebook" />
    <i class="mdi mdi-twitter" />
    <i class="mdi mdi-instagram" />
  </div>
</template>
<style scoped>
.links {
  display: flex;
  justify-content: center;
  width: 100%;
  gap: 4rem;
  font-size: 1.2rem;
  color: #000;
}

.links a {
  text-decoration: none;
}

.icons {
  padding-right: 3rem;
  display: flex;
  gap: 4rem;
  font-size: 2.2rem;
}
</style>
```

Neste arquivo, estamos criando um componente para exibir os links de ajuda, contato e termos de privacidade e os ícones das redes sociais no rodapé da aplicação. Estamos usando a tag `RouterLink` para criar os links de navegação e a tag `i` para exibir os ícones da biblioteca Material Design Icons. O tamanho dos ícones é definido no CSS, bem como o espaçamento entre eles e o alinhamento horizontal.

Da mesma forma, fizemos ajustes na apresentação dos links de navegação, definindo um espaçamento entre eles e o alinhamento horizontal. Ainda não configuramos a navegação para as páginas de ajuda, contato e termos de privacidade, sendo que todos os links apontam para a página inicial.

# Ajuste no cabeçalho e rodapé de telas pequenas

<span style="display: flex; justify-content: space-between;"><span>[&lt; Listagem de produtos](listagem-produtos.html 'Voltar')</span><span>[Ajustes no cabeçalho e rodapé &gt;](cabecalho-rodape.html 'Próximo')</span></span>
