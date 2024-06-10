---
title: 'Preparando a tela de Login'
permalink: /loja-virtual/preparando-login
---

# Criando uma tela de Login

Inicialmente vamos criar uma tela para que futuramente a gente possa fazer o login na aplicação. Para isso, vamos criar um componente chamado `LoginView.vue` dentro da pasta `src/views`.

```vue
<script setup></script>
<template>
  <h1>Login</h1>
</template>
```

Em seguida, vamos editar o arquivo `src/router/index.js` para adicionar a rota da tela de login. O conteúdo do arquivo deve ficar:

```javascript
import { createRouter, createWebHistory } from 'vue-router';
import HomeView from '../views/HomeView.vue';
import LayoutFull from '@/layouts/LayoutFull.vue';

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: '',
      component: LayoutFull,
      children: [
        {
          path: '',
          name: 'Home',
          component: HomeView,
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

# Adicionando um link para a tela de Login em telas pequenas

Agora que a tela de login está pronta e nas rotas, vamos adicionar um link para ela nos menus da aplicação. Vamos iniciar com as telas pequenas. A chamada para o login em telas pequenas ficará no menu do rodapé. Para isso, vamos editar o arquivo `src/componentes/templates/small/SmallFooter.vue`. Nesse caso, faremos algumas alterações. Primeiramente, vamos alterar o bloco template para o conteúdo abaixo::

```vue
<template>
  <div id="footerMenu" :style="{ display: showMenu ? 'block' : 'none' }">
    <RouterLink to="/">
      <HomeOutline size="25" fillColor="#282828" />
      Home
    </RouterLink>
    <RouterLink to="/login">
      <Account size="25" fillColor="#282828" />
      Login
    </RouterLink>
  </div>
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

    <div class="hamburger" @click="showMenu = !showMenu">
      <Menu size="25" fillColor="#282828" />
      Menu
    </div>
  </div>
</template>
```

Note que adicionamos uma `div` com o id `footerMenu` que será exibida quando o menu estiver aberto. Nela, adicionamos um link para a tela de `Login` e outro para tela `Home`. Também, fizemos uma alteração no ícone do menu, colocando-o dentro de uma `div` com a classe `hamburger`. Nesse caso, foi adicionado um evento de click para alternar a exibição do submenu.

Para isso, precisamos fazer uma alteração no bloco `script` e deixá-lo como seguinte conteúdo:

```vue
<script setup>
import { ref } from 'vue';
import { onBeforeRouteUpdate } from 'vue-router';

import AccountCircleOutline from 'vue-material-design-icons/AccountCircleOutline.vue';
import CartOutline from 'vue-material-design-icons/CartOutline.vue';
import HomeOutline from 'vue-material-design-icons/HomeOutline.vue';
import Account from 'vue-material-design-icons/Account.vue';
import Menu from 'vue-material-design-icons/Menu.vue';

const showMenu = ref(false);

onBeforeRouteUpdate(() => {
  showMenu.value = false;
});
</script>
```

Note que adicionamos uma variável `showMenu` que é um `ref` e que será utilizada para controlar a exibição do menu. Também, adicionamos um evento `onBeforeRouteUpdate` que será chamado sempre que a rota for alterada. Nesse evento, setamos o valor de `showMenu` para `false`. Isso é importante para que o menu seja fechado sempre que a rota for alterada.

Por fim, faremos uma alteração no bloco `style` para adicionar o estilo da classe `hamburger`. O conteúdo deve ficar da seguinte forma:

```css
<style scoped>
#footerMenu {
    position: fixed;
    bottom: 15%;
    right: 0;

    width: 20%;
    border-top: #EEEEEE 1px solid;
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

.icons a,
.icons .hamburger {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-decoration: none;
    color: #282828;
    font-size: 1rem;
    transition: color 0.3s;
}

.hamburger:hover {
    cursor: pointer;
}
</style>
```

# Adicionando um link para a tela de Login em telas médias

No caso das telas médias, vamos adicionar o link para a tela de `Login` no menu lateral. Para isso, vamos editar o arquivo `src/componentes/templates/medium/MediumAside.vue`. Nesse caso, faremos algumas alterações. Primeiramente, vamos alterar o bloco template para o conteúdo abaixo:

```vue
<script setup>
import LogoTitle from '@/components/templates/LogoTitle.vue';
</script>
<template>
  <div class="logo_and_menu">
    <logo-title class="mb-2" />
    <div class="divider" />
    <div class="menu">
      <router-link to="/">
        <i class="icon mdi mdi-home-outline" /> Home
      </router-link>
    </div>
    <div class="divider" />
    <div class="menu">
      <router-link to="/">
        <i class="icon mdi mdi-account-circle-outline" /> Perfil
      </router-link>
      <router-link to="/">
        <i class="icon mdi mdi-cart-outline" /> Carrinho
      </router-link>
      <router-link to="/login">
        <i class="icon mdi mdi-account" /> Login
      </router-link>
    </div>
  </div>
  <logo-title />
</template>
<style scoped>
.mb-2 {
  margin-bottom: 1.5rem;
}

.icon {
  font-size: 2rem;
  align-self: center;
}

.divider {
  margin-top: 1rem;
  border-top: 1px solid #eeeeee;
}

.menu {
  padding: 3rem;
}

.menu a {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #000000;
  gap: 1rem;
  font-size: 1.3rem;
  margin-top: 2.2rem;
}
</style>
```

Note que adicionamos um link para a tela de `Login` no menu lateral. Também, já deixamos links para as telas `Carrinho` e `Perfil` que ainda não foram desenvolvidas. Por isso, ao clicar nesses links, a rota será a mesma da tela `Home`.

# Adicionando um link para a tela de Login em telas grandes

A mesma alteração pode ser feita no menu lateral das telas grandes. Para isso, basta editar o arquivo `src/componentes/templates/large/LargeAside.vue` e adicionar o link para a tela de `Login` no menu lateral. O arquivo deve ficar com o seguinte conteúdo:

```vue
<script setup>
import LogoTitle from '@/components/templates/LogoTitle.vue';
</script>
<template>
  <div class="logo_and_menu">
    <logo-title class="mb-2" />
    <div class="divider" />
    <div class="menu">
      <router-link to="/">
        <i class="icon mdi mdi-home-outline" /> Home
      </router-link>
    </div>
    <div class="divider" />
    <div class="menu">
      <router-link to="/">
        <i class="icon mdi mdi-account-circle-outline" /> Perfil
      </router-link>
      <router-link to="/">
        <i class="icon mdi mdi-cart-outline" /> Carrinho
      </router-link>
      <router-link to="/login">
        <i class="icon mdi mdi-account" /> Login
      </router-link>
    </div>
  </div>
  <logo-title />
</template>
<style scoped>
.mb-2 {
  margin-bottom: 1.5rem;
}

.icon {
  font-size: 2rem;
  align-self: center;
}

.divider {
  margin-top: 1rem;
  border-top: 1px solid #eeeeee;
}

.menu {
  padding: 3rem;
}

.menu a {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #000000;
  gap: 1rem;
  font-size: 1.3rem;
  margin-top: 2.2rem;
}
</style>
```

No caso das telas grandes não mantivemos os links para o carrinho e perfil pois estes ficarão no menu superior.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Configurando o cabeçalho e rodapé](cabecalho-rodape.html 'Voltar')</span><span>[Sumário &gt;](../ 'Próximo')</span></span>
