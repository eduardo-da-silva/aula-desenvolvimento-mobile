---
title: 'Organização do Layout'
permalink: /loja-virtual/layout
---

# Limpando o projeto

Vamos começar limpando o projeto, removendo os arquivos e pastas que não são mais necessários.

1. Remova todo o conteúdo da pasta `src/components`.
2. Edite o arquivo `src/assets/main.css` e substitua o conteúdo, deixando apenas o seguinte:

```css
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

3. Edite o arquivo `src/App.vue` e substitua o conteúdo, deixando apenas o seguinte:

```html
<script setup></script>

<template>
  <h1>Loja Virtual</h1>
</template>
```

4. Teste a aplicação para verificar se está tudo funcionando corretamente.

Lembre que para testar a aplicação, você deve executar o comando `npm run dev` no terminal.

<span style="display: flex; justify-content: space-between;"

> <span>[&lt; A loja virtual](. 'Voltar')</span>
> <span>[??? &gt;](??? 'Próximo')</span></span

```

```
