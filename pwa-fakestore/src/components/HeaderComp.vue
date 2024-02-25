<script setup>
import { ref } from 'vue';

import CartPlus from 'vue-material-design-icons/CartPlus.vue';
import Account from 'vue-material-design-icons/Account.vue';
import Menu from 'vue-material-design-icons/Menu.vue';

const menuAberto = ref(false);
</script>

<template>
  <header>
    <div class="header--container">
      <div class="header--logo">
        <img src="@/assets/logoFakeStore.png" alt="Logo" />
        <h1>FakeStore</h1>
      </div>
      <nav class="header--nav">
        <ul :class="menuAberto ? 'menu' : ''">
          <li><a href="#">Home</a></li>
          <li><a href="#">Eletrônicos</a></li>
          <li><a href="#">Jóias</a></li>
          <li><a href="#">Masculino</a></li>
          <li><a href="#">Feminino</a></li>
        </ul>
      </nav>
      <div class="header--icons">
        <Account />
        <CartPlus />
        <Menu @click="menuAberto = !menuAberto" class="menu-hamburguer" />
      </div>
    </div>
  </header>
</template>

<style scoped>
header {
  background: #fff;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
  padding: 1rem 0;
}
.header--container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 1rem;
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
.header--nav ul {
  display: flex;
  gap: 1rem;
}
.header--nav li {
  list-style: none;
}

.header--icons {
  display: flex;
  gap: 1rem;
}
.header--user img {
  width: 2rem;
  height: 2rem;
}
.header--cart img {
  width: 2rem;
  height: 2rem;
}

.menu-hamburguer {
  display: none;
}

@media (max-width: 768px) {
  .header--nav ul {
    display: none;
  }
  .header--container {
    justify-content: space-between;
  }
  .header--container > div {
    display: flex;
    align-items: center;
  }
  .header--container > div img {
    width: 2rem;
    height: 2rem;
  }

  .menu-hamburguer {
    display: block;
  }

  .header--nav .menu {
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
  .header--nav .menu li {
    display: block;
    margin-top: 12px;
    color: #000;
    font-family: inherit;
    font-size: 1.5rem;
    text-decoration: none;
  }

  .header--nav .menu li a {
    color: #000;
    text-decoration: none;
  }
}
</style>
