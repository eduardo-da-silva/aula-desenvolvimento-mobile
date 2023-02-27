---
title: "Interpolação de lista"
permalink: /intro/interpolacao-lista
---

# Interpolação de uma lista

Para interpolar uma lista no React Native existem várias alternativas. Num primeiro momento, usaremos um componentes chamado `FlatList`.

O exemplo a seguir melhor o código que foi desenvolvido até então, incluindo a listagem de  uma lista de tarefas:

```javascript
import { StyleSheet, Text, View, FlatList } from 'react-native';
import Header from './src/components/Header';
export default function App() {
  const tasks = ['Tarefa 1', 'Tarefa 2', 'Tarefa 3', 'Tarefa 4', 'Tarefa 5'];
  return (
    <View style={styles.container}>
      <Header />
      <View>
        <FlatList data={tasks} renderItem={({ item }) => <Text>{item}</Text>} />
      </View>
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

Note que foi criada uma constante chamada `tasks`, com algumas tarefas armazenadas em um Array de strings. Então, na template que será renderizada, é utilizado o componente `FlatList` que possui dois atributos:

* data: que contém os dados a serem manipulados pelo componente
* renderItem: que indica o que deve ser feito com cada item manipulado. No exemplo, cada item é interpolado dentro de uma tag `<Text></Text>`.


<span style="display: flex; justify-content: space-between;"><span>[&lt; Componentes do React Native](componentes.html "Voltar")</span> <span>[Exercícios &gt;](exercicios.html "Próximo")</span></span>