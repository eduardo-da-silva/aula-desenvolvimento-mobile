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


<span style="display: flex; justify-content: space-between;"><span>[&lt; Instalação e criação de um aplicação](criar-aplicacao-react-native.html "Voltar")</span> <span>[Interpolação de uma lista &gt;](interpolacao-lista.html "Próximo")</span></span>