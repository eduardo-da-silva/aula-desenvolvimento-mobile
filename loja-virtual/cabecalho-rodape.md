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

# Ajuste no cabeçalho e rodapé de telas médias

Para telas médias, vamos fazer ajustes no cabeçalho e rodapé da aplicação. Para isso, vamos editar o arquivo `src/componentes/templates/medium/MediumHeader.vue`, com o seguinte conteúdo:

```vue
<script setup>
import Magnify from 'vue-material-design-icons/Magnify.vue';
</script>

<template>
  <div class="icons">
    <Magnify />
  </div>
</template>

<style scoped>
.icons {
  display: flex;
  gap: 1rem;
  align-items: center;
}
</style>
```

Note que estamos importando o ícone de busca da biblioteca Material Design Icons e exibindo-o na tela. O tamanho do ícone é definido no CSS, bem como o espaçamento entre eles e o alinhamento horizontal.

Em seguida, vamos editar o arquivo `src/componentes/templates/medium/MediumFooter.vue`, com o seguinte conteúdo:

```vue
<script setup>
import Facebook from 'vue-material-design-icons/Facebook.vue';
import Twitter from 'vue-material-design-icons/Twitter.vue';
import Instagram from 'vue-material-design-icons/Instagram.vue';
</script>
<template>
  <div class="links">
    <RouterLink to="/">Help</RouterLink>
    <RouterLink to="/">Contact Us</RouterLink>
    <RouterLink to="/">Privacy & Terms</RouterLink>
  </div>
  <div class="icons">
    <Facebook size="30" />
    <Twitter size="30" />
    <Instagram size="30" />
  </div>
</template>
<style scoped>
.links {
  width: 100%;
  justify-content: center;
  display: flex;
  gap: 4rem;
  font-size: 1.2rem;
}

.links a {
  color: #000;
  text-decoration: none;
  transition: color 0.3s;
}

.icons {
  padding-right: 3rem;
  display: flex;
  gap: 4rem;
  align-items: center;
}
</style>
```

Neste arquivo, estamos importando os ícones das redes sociais da biblioteca Material Design Icons e exibindo-os na tela. O tamanho dos ícones é definido no CSS, bem como o espaçamento entre eles e o alinhamento horizontal.

# Ajuste no cabeçalho e rodapé de telas pequenas

Por fim, vamos fazer ajustes no cabeçalho e rodapé da aplicação para telas pequenas. Para isso, vamos editar o arquivo `src/componentes/templates/small/SmallHeader.vue`, com o seguinte conteúdo:

```vue
<script setup>
import Magnify from 'vue-material-design-icons/Magnify.vue';
import LogoTitle from '@/components/templates/LogoTitle.vue';
</script>

<template>
  <logo-title class="pl-0" />
  <div class="icons">
    <Magnify />
  </div>
</template>

<style scoped>
.pl-0 {
  padding-left: 0rem;
}

.icons {
  display: flex;
  gap: 1rem;
  align-items: center;
}
</style>
```

Da mesma forma, estamos importando o ícone de busca da biblioteca Material Design Icons e exibindo-o na tela. O tamanho do ícone é definido no CSS, bem como o espaçamento entre eles e o alinhamento horizontal.

E, para o rodapé, vamos editar o arquivo `src/componentes/templates/small/SmallFooter.vue`, com o seguinte conteúdo:

```vue
<script setup>
import AccountCircleOutline from 'vue-material-design-icons/AccountCircleOutline.vue';
import CartOutline from 'vue-material-design-icons/CartOutline.vue';
import HomeOutline from 'vue-material-design-icons/HomeOutline.vue';
import Menu from 'vue-material-design-icons/Menu.vue';
</script>
<template>
  <div class="icons">
    <RouterLink to="/">
      <HomeOutline size="25" fillColor="#282828" />
      Home
    </RouterLink>
    <RouterLink to="/">
      <AccountCircleOutline size="25" fillColor="#282828" />
      Perfil
    </RouterLink>
    <RouterLink to="/">
      <CartOutline size="25" fillColor="#282828" />
      Carrinho
    </RouterLink>
    <RouterLink to="/">
      <Menu size="25" fillColor="#282828" />
      Menu
    </RouterLink>
  </div>
</template>
<style scoped>
#footerMenu {
  position: fixed;
  bottom: 15%;
  right: 0;

  width: 20%;
  border-top: #eeeeee 1px solid;
  background-color: white;

  display: block;
  padding: 1rem;
}

#footerMenu a {
  display: flex;
  width: 100%;
  justify-content: space-between;
  text-decoration: none;
  color: #282828;
  font-size: 1rem;
  transition: color 0.3s;
}

.icons {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: space-between;
}

.icons a {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-decoration: none;
  color: #282828;
  font-size: 1rem;
  transition: color 0.3s;
}
</style>
```

Neste arquivo, estamos importando os ícones de perfil, carrinho, home e menu da biblioteca Material Design Icons e exibindo-os na tela. O tamanho dos ícones é definido no CSS, bem como o espaçamento entre eles e o alinhamento horizontal.

Nas próximas aulas, vamos configurar a navegação para as páginas de ajuda, contato e termos de privacidade, bem como adicionar funcionalidades aos ícones do cabeçalho. Por isso, faremos alterações nos arquivos de cabeçalho e rodapé, quando necessário.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Listagem de produtos](listagem-produtos.html 'Voltar')</span><span>[Preparando a tela de Login &gt;](preparando-login.html 'Próximo')</span></span>
