---
title: 'Uso nos componentes'
description: 'Aplicando o composable de responsividade nos componentes Vue'
permalink: /composables-responsividade/uso-nos-componentes
---

# Uso nos componentes

Vamos agora editar o arquivo `ListagemProdutos.vue` para aplicar o composable de responsividade. Primeiro, vamos importar o composable `useScreen` e usá-lo para verificar o tamanho da tela.

Primeiro, vamos editar o bloco de _script_ do componente `ListagemProdutos.vue` para importar o composable `useScreen` e extrair as variáveis retornadas por ele. Note que manteremos as informações atuais no arquivo e iremos adicionar o código a seguir:

```js
import { useScreen } from '@/composables/screen';

const { browserWidth, deviceWidth, isMobile } = useScreen();
```

Sugiro que você mantenha o código organizado, então adicione as variáveis retornadas pelo composable `useScreen` logo após as variáveis de estado do componente.

Agora, vamos usar as variáveis `isMobile` e `browserWidth` para aplicar estilos condicionais no componente. Vamos adicionar uma classe condicional ao elemento `ul` que contém a lista de produtos. Se a tela for menor que 768 pixels, vamos adicionar a classe `mobile` ao elemento `ul`. Caso contrário, vamos adicionar a classe `desktop`.

Vamos agora, editar o bloco de _template_ do componente `ListagemProdutos.vue` para mostrar as informações reativas dentro do bloco `h1` com a frase Produtos. Esse é apenas um exemplo, que será excluído depois. O objetivo é mostrar como podemos usar as variáveis reativas retornadas pelo composable `useScreen`.

```html
<template>
  <div>
    <h1>
      {% raw %} Produtos - {{ browserWidth }} - {{ deviceWidth }} - {{
      isMobile}} {% endraw %}
      <span v-if="isMobile">É móvel</span>
    </h1>
    ...
  </div>
</template>
```

Note que estamos usando as variáveis `browserWidth`, `deviceWidth` e `isMobile` diretamente no bloco de _template_ do componente. Isso é possível porque essas variáveis são reativas e serão atualizadas sempre que o tamanho da tela for alterado.

Além disso, estamos mostrando a frase "É móvel" apenas se a variável `isMobile` for verdadeira. Isso é possível graças à diretiva `v-if` do Vue.

Poderíamos ter um componente diferente para cada tipo de dispositivo, mas isso não é necessário. Com o composable `useScreen`, podemos aplicar estilos condicionais diretamente no bloco de _template_ do componente, tornando o código mais limpo e fácil de manter.

No entanto, também é possível ter algum componente específico para dispositivos móveis, por exemplo, e usar o composable `useScreen` para verificar o tamanho da tela e decidir qual componente mostrar.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Criando um composable](criando-um-composable.html 'Voltar')</span> <span>[Desafio &gt;](desafio.html 'Próximo')</span></span>
