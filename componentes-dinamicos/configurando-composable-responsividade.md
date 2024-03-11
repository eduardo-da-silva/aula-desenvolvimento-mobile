---
title: 'Configurando composable de responsividade'
description: 'Configurando o composable de responsividade'
permalink: /componentes-dinamicos/configurando-composable-responsividade
---

# Criando um composable de responsividade

Embora já tenhamos o composable `useScreen`, faremos um novo para não interferir no que já foi feito. O objetivo é que você entenda como criar um composable e como ele pode ser usado em diferentes situações.

Então, criaremos um arquivo chamado `monitor.js` na pasta `src/composables` e o conteúdo desse arquivo será:

```js
import {
  defineAsyncComponent,
  onMounted,
  onUnmounted,
  ref,
  shallowRef,
} from 'vue';

export function useMonitor() {
  const breakpoint = ref('sm');
  const menu = shallowRef(
    defineAsyncComponent(() => import('../components/MenuSuperiorXs.vue')),
  );

  const updateBreakpoint = () => {
    const width = window.innerWidth;
    if (width < 576) {
      breakpoint.value = 'xs';
      menu.value = defineAsyncComponent(() =>
        import('../components/MenuSuperiorXs.vue'),
      );
    } else if (width < 768) {
      breakpoint.value = 'sm';
      menu.value = defineAsyncComponent(() =>
        import('../components/MenuSuperiorSm.vue'),
      );
    } else if (width < 992) {
      breakpoint.value = 'md';
      menu.value = defineAsyncComponent(() =>
        import('../components/MenuSuperiorMd.vue'),
      );
    } else if (width < 1200) {
      breakpoint.value = 'lg';
      menu.value = defineAsyncComponent(() =>
        import('../components/MenuSuperiorLg.vue'),
      );
    } else {
      breakpoint.value = 'xl';
      menu.value = defineAsyncComponent(() =>
        import('../components/MenuSuperiorXl.vue'),
      );
    }
  };

  onMounted(() => {
    updateBreakpoint();
    window.addEventListener('resize', updateBreakpoint);
  });

  onUnmounted(() => {
    window.removeEventListener('resize', updateBreakpoint);
  });

  return {
    breakpoint,
    menu,
  };
}
```

Neste arquivo, criamos um composable chamado `useMonitor` que tem como objetivo monitorar o tamanho da tela e atualizar o componente do menu superior de acordo com o tamanho da tela. Para isso, usamos o `window.innerWidth` para obter a largura da tela e, com base nesse valor, atualizamos o componente do menu superior.

Contudo, é importante ressaltar que inserimos alguns conceitos novos nesse arquivo, que vamos entender a seguir.

## Função defineAsyncComponent

A função `defineAsyncComponent` é uma função do Vue que permite carregar um componente de forma assíncrona. Isso é útil para carregar componentes apenas quando eles são necessários, o que pode melhorar o desempenho do aplicativo. Esse é um conceito relacionado ao _lazy loading_ que mencionamos anteriormente.

## Função ShallowRef

A função `shallowRef` é uma função do Vue que cria uma referência reativa a um valor. A diferença entre `ref` e `shallowRef` é que `shallowRef` não cria uma reatividade profunda. Isso significa que, se o valor passado para `shallowRef` for um objeto ou um array, as alterações internas desse objeto ou array não serão reativas. Isso é útil para evitar problemas de desempenho em situações em que a reatividade profunda não é necessária. Quando usamos o conceito de componentes dinâmicos, o uso do `shallowRef` é indicado pela documentação da linguagem.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Editando o HomeView](editando-homeview.html 'Voltar')</span> <span>[Finalizando o uso dos componentes dinâmicos &gt;](finalizando-uso-componentes-dinamicos.html 'Próximo')</span></span>
