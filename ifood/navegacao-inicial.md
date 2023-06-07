---
title: "Navegação Inicial"
permalink: /ifood/navegacao-inicial
---

# As primeiras rotas usando BottomTabNavigator

Para criar as primeiras rotas do nosso projeto, vamos utilizar o componente `BottomTabNavigator`. Para isso, vamos criar um arquivo `src/routes.js` com o seguinte conteúdo:

```jsx
import React from 'react';

import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import { MaterialIcons } from '@expo/vector-icons';

import Home from './screens/Home';
import Busca from './screens/Busca';
import Perfil from './screens/Perfil';
import Pedidos from './screens/Pedidos';

const BottomTab = createBottomTabNavigator();

export default function Routes() {
  return (
    <NavigationContainer>
      <BottomTab.Navigator 
        screenOptions={{
          tabBarActiveTintColor: 'red',
          tabBarInactiveTintColor: 'black',
        }}
      >
        <BottomTab.Screen
          name="Home"
          component={Home}
          options={{
            tabBarLabel: 'Home',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="home" color={color} size={26} />
            ),
          }}
        />
        <BottomTab.Screen
          name="Busca"
          component={Busca}
          options={{
            tabBarLabel: 'Busca',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="search" color={color} size={26} />
            ),
          }}
        />
        <BottomTab.Screen
          name="Pedidos"
          component={Pedidos}
          options={{
            tabBarLabel: 'Pedidos',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="assignment" color={color} size={26} />
            ),
          }}
        />
        <BottomTab.Screen
          name="Perfil"
          component={Perfil}
          options={{
            tabBarLabel: 'Perfil',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="person" color={color} size={26} />
            ),
          }}
        />
      </BottomTab.Navigator>
    </NavigationContainer>
  );
}
```

## O que é o BottomTabNavigator?

O `BottomTabNavigator` é um componente que cria uma navegação por abas na parte inferior da tela. Ele é muito utilizado em aplicativos que possuem poucas telas e que não precisam de uma navegação mais complexa.

O componente recebe a propriedade `screenOptions`, que define as opções de estilo das abas. No exemplo, foram definidas as cores das abas ativas e inativas.

As abas são criadas através do componente `BottomTab.Screen`, que recebe o nome da tela e o componente que será renderizado quando a aba for selecionada. No exemplo, foram criadas as telas Home, Busca, Pedidos e Perfil.

Cada aba também recebe as opções `tabBarLabel` e `tabBarIcon`. A primeira define o texto que será exibido abaixo do ícone da aba e a segunda define o ícone que será exibido na aba. No exemplo, foram utilizados ícones da biblioteca `@expo/vector-icons`, mas você pode utilizar qualquer biblioteca de ícones ou até mesmo imagens.

## O que é o NavigationContainer?

O `NavigationContainer` é um componente que deve ser utilizado como o componente pai de todas as rotas do aplicativo. Ele é responsável por gerenciar o estado de navegação do aplicativo.

# Os ajustes no App.js

No arquivo `App.js`, vamos importar o componente `Routes` e renderizá-lo, como mostrado abaixo:

```jsx
import { Fragment } from 'react';
import { StatusBar } from 'expo-status-bar';
import { StyleSheet } from 'react-native';

import Routes from './src/routes';

export default function App() {
  return (
    <Fragment>
      <StatusBar style="auto" />
      <Routes />
    </Fragment>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```


## O que é o StatusBar?

O `StatusBar` é um componente que permite alterar a cor da barra de status do aplicativo. No exemplo, foi utilizada a cor padrão do Expo, mas você pode alterar para a cor que preferir.

## O que é o Fragment?

O `Fragment` é um componente que permite renderizar vários componentes sem a necessidade de criar um componente pai. No exemplo, o `Fragment` foi utilizado para renderizar o `StatusBar` e o `Routes` sem a necessidade de criar um componente pai.



<span style="display: flex; justify-content: space-between;"><span>>[&lt; Introdução](intro.html "Voltar")</span> <span>[Exercícios &gt;](exercicios.html "Próximo")</span></span>