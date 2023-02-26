---
title: "Componentes React"
permalink: /intro/componentes
---

# Componentes React

No React Native, usaremos o mesmo paradigma de componentes que é usado no React. Um componente é uma função ou classe que retorna um elemento React. Um elemento React é uma descrição de como um componente deve ser renderizado. Um elemento React é um objeto JavaScript que contém propriedades e filhos.

Ainda não iremos aprofundar muito nos exemplos. Criaremos um componente simples, que será utilizado para mostrar o cabeçalho da aplicação. O componente será chamado de `Header`, e será definido no arquivo `src/components/Header.js`:

```javascript
import { Text, View, StyleSheet } from 'react-native';
export default function Header() {
  return (
    <View style={styles.header}>
      <Text style={styles.headerText}>Lista de Tarefas</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  header: {
    backgroundColor: 'coral',
    padding: 20,
    width: '100%',
    alignContent: 'center',
    alignItems: 'center',
  },
  headerText: {
    color: 'white',
    fontSize: 20,
  },
});
```

Este código importa o Text, View e StyleSheet do React Native. Usando esse código você pode criar uma função chamada Header() que retorna um elemento View com alguns estilos definidos usando o StyleSheet.

O estilo header define o background da View com a cor coral, adiciona 20 de padding e preenche a largura total, alinhando o conteúdo e os items dentro da View.

O estilo headerText define a cor como branca e o tamanho de fonte como 20.

Ao chamar essa função, uma View com o texto 'Lista de Tarefas' é renderizada com os estilos definidos.

Para utilizar esse componente, você deve importá-lo no arquivo App.js:

```javascript
import { StyleSheet, Text, View } from 'react-native';
import Header from './src/components/Header';
export default function App() {
  return (
    <View style={styles.container}>
      <Header />
      <Text>Open up App.js to start working on your app!</Text>
    </View>
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

No exemplo acima, o componente Header é importado e utilizado dentro da função App. O componente Header é renderizado dentro da View principal da aplicação.


# Componentes de classe vs. Funções

Existem duas maneiras de criar um componente no React Native: usando uma função ou uma classe. A diferença entre os dois é que uma função retorna um elemento React, enquanto uma classe retorna um elemento React e pode ter um estado interno. A principal diferença entre Componentes de Classe e Componentes de Função no React é a forma como os componentes são definidos e implementados.

Componentes de Classe são definidos usando a sintaxe de classes do ES6 e herdam da classe Component do React. Eles possuem um método render() que retorna o que deve ser renderizado na tela. Eles também possuem um estado interno (state) e podem acessar os ciclos de vida do componente (lifecycle methods) do React.

Componentes de Função são definidos usando a sintaxe de função do ES6. Eles não têm um estado interno (state) e não podem acessar os ciclos de vida do componente. Eles são mais simples de escrever e podem ser usados em casos em que não há necessidade de um estado ou ciclo de vida complexos.

No entanto, a partir do React 16.8, foi introduzido o conceito de Hooks, que permitem que os Componentes de Função tenham um estado interno e acessem os ciclos de vida do componente de maneira mais simples e intuitiva, tornando-os uma opção atraente para muitos desenvolvedores.

O uso de componentes de função já foi apresentado anteriormente. Agora, vamos implementar os mesmos componentes usando classes. O componente `Header` pode ser implementado da seguinte forma:

```javascript
import React, { Component } from 'react';
import { Text, View, StyleSheet } from 'react-native';

export default class Header extends Component {
  render() {
    return (
      <View style={styles.header}>
        <Text style={styles.headerText}>Lista de Tarefas</Text>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  header: {
    backgroundColor: 'coral',
    padding: 20,
    width: '100%',
    alignContent: 'center',
    alignItems: 'center',
  },
  headerText: {
    color: 'white',
    fontSize: 20,
  },
});
```

Já o App.js pode ser implementado da seguinte forma:

```javascript
import React, { Component } from 'react';
import { StyleSheet, Text, View } from 'react-native';
import Header from './src/components/Header';

export default class App extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Header />
        <Text>Open up App.js to start working on your app!</Text>
      </View>
    );
  }
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

Note que, é possível utilizar componentes de classe e de função no mesmo projeto, dependendo da necessidade de cada um.


<span style="display: flex; justify-content: space-between;"><span>[&lt; Instalação e criação de um aplicação](criar-aplicacao-react-native.html "Voltar")</span> <span>[Interpolação de uma lista &gt;](interpolacao-lista.html "Próximo")</span></span>

<script src="/assets/scripts/copyCode.js"></script>