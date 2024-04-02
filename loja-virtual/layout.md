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

<span style="display: flex; justify-content: space-between;"><span>[&lt; A loja virtual](. 'Voltar')</span><span>[??? &gt;](??? 'Próximo')</span></span>
