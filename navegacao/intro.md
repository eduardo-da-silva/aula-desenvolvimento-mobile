---
title: "Navegação e Routeamento"
description: Princípios de navegação e roteamento
permalink: /navegacao
---
# Índice da aula
3.1. [Stack Navigation ](react-navigation/stack.md)  
<!-- 2.2. [Uso no projeto Times-Jogadores](axios/uso-times-jogadores.md)  -->

# Princípios de navegação e roteamento


Neste tópico vamos conhecer os conceitos de navegação e roteamento, incluindo o uso de Stack Navigation, Drawer Navigation e Bottom Tab Navigation.

Em linhas gerais, podemos resumir da seguinte forma:
* `Stack Navigation`: usado para navegar entre telas de um aplicativo.
* `Drawer Navigation`: usado para navegar entre telas de um aplicativo, com um menu lateral.
* `Bottom Tab Navigation`: usado para navegar entre telas de um aplicativo, com um menu inferior.

A navegação é um dos principais recursos de um aplicativo móvel. Ela permite que o usuário navegue entre as telas do aplicativo, de forma que ele possa acessar as funcionalidades do aplicativo.

Para utilizar a navegação, precisamos instalar o pacote `@react-navigation/native`:
```bash
npm install @react-navigation/native
```

Além disso, como usamos o Expo, precisamos instalar os pacotes `react-native-screens` e `react-native-safe-area-context`:
```bash
npx expo install react-native-screens react-native-safe-area-context
```

Por fim, toda a aplicação precisa ser renderizada dentro de um componente `NavigationContainer`:
```js
import { NavigationContainer } from '@react-navigation/native';

export default function App() {
  return (
    <NavigationContainer>
      { /* Conteúdo da aplicação */}
    </NavigationContainer>
  );
}
```

Note que essa alteração acima deve ser feita no arquivo `App.js`.

Nas demais seções, vamos ver como utilizar cada tipo de navegação.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](./ "Início")</span> <span>[Stack Navigation &gt;](navegacao/stack.html "Próximo")</span></span>
