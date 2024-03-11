---
title: 'Criando os arquivos de menu superior'
description: 'Criando os arquivos de menu superior'
permalink: /componentes-dinamicos/criando-arquivos-menu-superior
---

# Criando os arquivos modelo para o menu superior

Nesta etapa, vamos partir do arquivo `src/components/MenuSuperior.vue` e criar 5 arquivos modelo para o menu superior, apenas alterando o título, para que possamos verificar o comportamento do aplicativo em diferentes tamanhos de tela.

Então, faremos uma cópia do arquivo `src/components/MenuSuperior.vue` e renomearemos para `MenuSuperiorXl.vue`, `MenuSuperiorLg.vue`, `MenuSuperiorMd.vue`, `MenuSuperiorSm.vue` e `MenuSuperiorXs.vue`. Em seguida, faremos as alterações necessárias em cada um dos arquivos.

## Aquivo `MenuSuperiorXl.vue`

```html
<script setup>
  import { ref } from 'vue';

  import CartPlus from 'vue-material-design-icons/CartPlus.vue';
  import Account from 'vue-material-design-icons/Account.vue';
  import Menu from 'vue-material-design-icons/Menu.vue';

  const menuAberto = ref(false);
</script>

<template>
  <header>
    <div class="header--logo">
      <img src="@/assets/logoFakeStore.png" alt="Logo" />
      <h1>FakeStore - XL</h1>
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
      <menu class="menu-hamburger" @click="menuAberto = !menuAberto" />
    </div>
  </header>
</template>

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

## Aquivo `MenuSuperiorLg.vue`

```html
<script setup>
  import { ref } from 'vue';

  import CartPlus from 'vue-material-design-icons/CartPlus.vue';
  import Account from 'vue-material-design-icons/Account.vue';
  import Menu from 'vue-material-design-icons/Menu.vue';

  const menuAberto = ref(false);
</script>

<template>
  <header>
    <div class="header--logo">
      <img src="@/assets/logoFakeStore.png" alt="Logo" />
      <h1>FakeStore - LG</h1>
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
      <menu class="menu-hamburger" @click="menuAberto = !menuAberto" />
    </div>
  </header>
</template>

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

## Aquivo `MenuSuperiorMd.vue`

```html
<script setup>
  import { ref } from 'vue';

  import CartPlus from 'vue-material-design-icons/CartPlus.vue';
  import Account from 'vue-material-design-icons/Account.vue';
  import Menu from 'vue-material-design-icons/Menu.vue';

  const menuAberto = ref(false);
</script>

<template>
  <header>
    <div class="header--logo">
      <img src="@/assets/logoFakeStore.png" alt="Logo" />
      <h1>FakeStore - MD</h1>
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
      <menu class="menu-hamburger" @click="menuAberto = !menuAberto" />
    </div>
  </header>
</template>

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

## Aquivo `MenuSuperiorSm.vue`

```html
<script setup>
  import { ref } from 'vue';

  import CartPlus from 'vue-material-design-icons/CartPlus.vue';
  import Account from 'vue-material-design-icons/Account.vue';
  import Menu from 'vue-material-design-icons/Menu.vue';

  const menuAberto = ref(false);
</script>

<template>
  <header>
    <div class="header--logo">
      <img src="@/assets/logoFakeStore.png" alt="Logo" />
      <h1>FakeStore - SM</h1>
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
      <menu class="menu-hamburger" @click="menuAberto = !menuAberto" />
    </div>
  </header>
</template>

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

## Aquivo `MenuSuperiorXs.vue`

```html
<script setup>
  import { ref } from 'vue';

  import CartPlus from 'vue-material-design-icons/CartPlus.vue';
  import Account from 'vue-material-design-icons/Account.vue';
  import Menu from 'vue-material-design-icons/Menu.vue';

  const menuAberto = ref(false);
</script>

<template>
  <header>
    <div class="header--logo">
      <img src="@/assets/logoFakeStore.png" alt="Logo" />
      <h1>FakeStore - XS</h1>
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
      <menu class="menu-hamburger" @click="menuAberto = !menuAberto" />
    </div>
  </header>
</template>

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

Agora que temos os arquivos modelo para o menu superior, podemos utilizá-los para verificar o comportamento do aplicativo em diferentes tamanhos de tela.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. 'Início')</span> <span>[Editando o HomeView &gt;](editando-homeview.html 'Próximo')</span></span>
