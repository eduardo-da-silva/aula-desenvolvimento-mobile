---
title: 'Finalizando o uso de componentes dinâmicos'
description: 'Finalizando o uso de componentes dinâmicos'
permalink: /componentes-dinamicos/finalizando-uso-componentes-dinamicos
---

# Editando o arquivo App.vue

Para finalizar esta etapa de uso de componentes dinâmicos, faremos uma alteração no arquivo `src/App.vue` e deixaremos o seu conteúdo como segue:

```html
<script setup>
  import { useMonitor } from '@/composables/monitor';

  const { menu } = useMonitor();
</script>

<template>
  <div>
    <component :is="menu" />
    <main>
      <router-view />
    </main>
    <footer>
      <p>Copyright &copy; 2024</p>
    </footer>
  </div>
</template>
```

Aqui, também usamos um conceito novo, que é o uso da _tag_ `component`, que é utilizado para renderizar componentes dinâmicos, sendo que o componente a ser renderizado será associado ao atributo `is`.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Configurando o composable de responsividade](configurando-composable-responsividade.html 'Voltar')</span><span>[Desafio &gt;](desafio.html 'Próximo')</span></span>
