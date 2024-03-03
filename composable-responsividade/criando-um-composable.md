---
title: 'Criando o primeiro composable'
description: 'Criando o primeiro composable para responsividade'
permalink: /composables-responsividade/criando-um-composable
---

# Criando o primeiro composable

Vamos começar criando um _composable_ que encapsula a lógica de verificação do tamanho da tela e a aplicação de estilos condicionais. Esse _composable_ será responsável por adicionar um _eventListener_ sempre que a tela for redimensionada, permitindo que possamos reagir a mudanças no tamanho da tela e aplicar estilos condicionais de forma mais eficiente.

Inicialmente, crie a pasta `composables` dentro da pasta `src` do projeto. Em seguida, crie um arquivo chamado `screen.js` dentro da pasta `composables` e adicione o seguinte conteúdo:

```js
import { onMounted, onUnmounted, ref } from 'vue';

export function useScreen() {
  const browserWidth = ref(window.innerWidth);
  const deviceWidth = ref(screen.width);
  const isMobile = ref(false);

  const onBrowserResize = () => {
    browserWidth.value = window.innerWidth;
    deviceWidth.value = screen.width;
    isMobile.value = window.innerWidth < 768;
  };

  onMounted(() => {
    window.addEventListener('resize', onBrowserResize);
  });

  onUnmounted(() => {
    window.removeEventListener('resize', onBrowserResize);
  });

  return { browserWidth, deviceWidth, isMobile };
}
```

Neste arquivo, criamos um _composable_ chamado `useScreen` que encapsula a lógica de verificação do tamanho da tela. Para isso, utilizamos os _hooks_ `onMounted` e `onUnmounted` para adicionar e remover um _eventListener_ sempre que a tela for redimensionada. Além disso, utilizamos a função `ref` para criar reativamente as variáveis `browserWidth`, `deviceWidth` e `isMobile`, que armazenam o tamanho da janela do navegador, o tamanho do dispositivo e um _boolean_ que indica se a tela é um dispositivo móvel, respectivamente.

Note que este é apenas um exemplo de _composable_ para responsividade. Você pode adaptar e expandir este _composable_ de acordo com as necessidades do seu projeto, incluindo a definição de _breakpoints_, a aplicação de estilos condicionais e outras lógicas relacionadas à responsividade.

Ainda, note que a função `onBrowserResize` é responsável por atualizar as variáveis `browserWidth`, `deviceWidth` e `isMobile` sempre que a tela for redimensionada. Essa função é chamada sempre que o _eventListener_ é acionado, garantindo que as variáveis sejam atualizadas de forma reativa.

Agora que temos esse _composable_ criado, podemos utilizá-lo em diferentes partes da aplicação para lidar com a responsividade de forma mais eficiente e organizada. No próximo passo, vamos utilizá-lo para mostrar o tamanho da tela em tempo real e também renderizar um componente condicionalmente de acordo com o tamanho da tela.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. 'Início')</span> <span>[Uso nos componentes Vue &gt;](uso-nos-componentes.html 'Próximo')</span></span>
