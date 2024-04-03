---
title: 'Organização do Layout'
permalink: /loja-virtual/layout
---

# Limpando o projeto

Vamos começar limpando o projeto, removendo os arquivos e pastas que não são mais necessários.

Primeiramente, remova todo o conteúdo da pasta `src/components`. Em seguida, edite o arquivo `src/assets/main.css` e substitua o conteúdo, deixando apenas o seguinte:

```css
@import '@mdi/font/css/materialdesignicons.css';
@import url('https://fonts.googleapis.com/css2?family=Belleza&family=Quicksand:wght@300..700&display=swap');

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  font-weight: normal;
}

body {
  margin: 0;
  min-height: 100vh;
  line-height: 1.6;
  font-family: 'Quicksand', sans-serif;
  font-size: 15px;
  font-optical-sizing: auto;
  font-style: normal;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

Feito isso, edite o arquivo `src/App.vue` e substitua o conteúdo, deixando apenas o seguinte:

```html
<script setup></script>

<template>
  <RouterView />
</template>

<style scoped></style>
```

Agora, edite o arquivo `src/views/HomeView.vue` e substitua o conteúdo, deixando apenas o seguinte:

```html
<script setup></script>

<template>
  <h1>Loja Virtual</h1>
</template>
```

Por fim, teste a aplicação para verificar se está tudo funcionando corretamente. Lembre que para testar a aplicação, você deve executar o comando `npm run dev` no terminal.

# Criando os componentes base para o layout

Vamos criar uma estrutura base para os componentes de layout. Para isso vamos criar as seguintes pastas e arquivos:

```
├── components
│   └── templates
│       ├── large
│       │   ├── LargeAside.vue
│       │   ├── LargeFooter.vue
│       │   └── LargeHeader.vue
│       ├── medium
│       │   ├── MediumAside.vue
│       │   ├── MediumFooter.vue
│       │   └── MediumHeader.vue
│       └── small
│           ├── SmallFooter.vue
│           └── SmallHeader.vue
```

Como conteúdo desses arquivos, colocaremos o seguinte:

```html
<!-- LargeAside.vue -->
<template>
  <h2>Large Aside</h2>
</template>

<!-- LargeFooter.vue -->
<template>
  <h2>Large Footer</h2>
</template>

<!-- LargeHeader.vue -->
<template>
  <h2>Large Header</h2>
</template>

<!-- MediumAside.vue -->
<template>
  <h2>Medium Aside</h2>
</template>

<!-- MediumFooter.vue -->
<template>
  <h2>Medium Footer</h2>
</template>

<!-- MediumHeader.vue -->
<template>
  <h2>Medium Header</h2>
</template>

<!-- SmallFooter.vue -->
<template>
  <h2>Small Footer</h2>
</template>

<!-- SmallHeader.vue -->
<template>
  <h2>Small Header</h2>
</template>
```

# Criando os arquivos de layout para diferentes tamanhos de tela

Vamos criar os arquivos de layout para diferentes tamanhos de tela. Para isso, vamos criar as seguintes pastas e arquivos:

```
├── layouts
│   ├── LayoutLarge.vue
│   ├── LayoutMedium.vue
│   └── LayoutSmall.vue
```

Vamos editar esses arquivos com o seguinte conteúdo:

```html
<!-- LayoutLarge.vue -->
<script setup>
  import LargeHeader from '@/components/templates/large/LargeHeader.vue';
  import LargeAside from '@/components/templates/large/LargeAside.vue';
  import LargeFooter from '@/components/templates/large/LargeFooter.vue';
</script>
<template>
  <div id="layout-large">
    <header>
      <large-header />
    </header>
    <aside>
      <large-aside />
    </aside>
    <main>
      <router-view />
    </main>
    <footer>
      <large-footer />
    </footer>
  </div>
</template>

<!-- LayoutMedium.vue -->
<script setup>
  import MediumHeader from '@/components/templates/medium/MediumHeader.vue';
  import MediumAside from '@/components/templates/medium/MediumAside.vue';
  import MediumFooter from '@/components/templates/medium/MediumFooter.vue';
</script>

<template>
  <div id="layout-medium">
    <header>
      <medium-header />
    </header>
    <aside>
      <medium-aside />
    </aside>
    <main>
      <router-view />
    </main>
    <footer>
      <medium-footer />
    </footer>
  </div>
</template>

<!-- LayoutSmall.vue -->
<script setup>
  import SmallHeader from '@/components/templates/small/SmallHeader.vue';
  import SmallFooter from '@/components/templates/small/SmallFooter.vue';
</script>

<template>
  <div id="layout-small">
    <header>
      <small-header />
    </header>
    <main>
      <router-view />
    </main>
    <footer>
      <small-footer />
    </footer>
  </div>
</template>
```

# Configurando o composable de responsividade e o layout

Vamos criar um composable para gerenciar a responsividade da aplicação. Para isso, vamos criar o arquivo `src/composables/layout.js` com o seguinte conteúdo:

```javascript
import { defineAsyncComponent, onMounted, onUnmounted, shallowRef } from 'vue';

export function useLayout() {
  const layout = shallowRef();

  const updateLayout = () => {
    const width = window.innerWidth;
    if (width < 768) {
      layout.value = defineAsyncComponent(() =>
        import('@/layouts/LayoutSmall.vue'),
      );
    } else if (width < 1200) {
      layout.value = defineAsyncComponent(() =>
        import('@/layouts/LayoutMedium.vue'),
      );
    } else {
      layout.value = defineAsyncComponent(() =>
        import('@/layouts/LayoutLarge.vue'),
      );
    }
  };

  onMounted(() => {
    updateLayout();
    window.addEventListener('resize', updateLayout);
  });

  onUnmounted(() => {
    window.removeEventListener('resize', updateLayout);
  });

  return { layout };
}
```

Feito isso, vamos configurar o layout da aplicação, criando o arquivo `src/layouts/LayoutFull.vue` com o seguinte conteúdo:

```html
<script setup>
  import { useLayout } from '@/composables/layout';
  const { layout } = useLayout();
</script>
<template>
  <component :is="layout" />
</template>
```

# Configurando o roteamento

Vamos configurar o roteamento da aplicação. Para isso, vamos editar o arquivo `src/router/index.js` com o seguinte conteúdo:

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
      ],
    },
  ],
});

export default router;
```

Feito isso, teste a aplicação para verificar se está tudo funcionando corretamente. Lembre que para testar a aplicação, você deve executar o comando `npm run dev` no terminal.

<span style="display: flex; justify-content: space-between;"><span>[&lt; A loja virtual](. 'Voltar')</span><span>[??? &gt;](??? 'Próximo')</span></span>

```

```
