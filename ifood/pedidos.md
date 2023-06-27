---
title: Pedidos"
permalink: /ifood/pedidos
---

# Tela Pedidos

Nessa etapa, vamos contruir a tela de pedidos.

## Instalando as dependências

Para iniciar, vamos instalar as dependências:

```bash
npm install @react-navigation/material-top-tabs react-native-tab-view
```

# Criando as screens

## Editar o arquivo de pedidos

Vamos editar o arquivo `src/screens/Pedidos/index.js` com o código abaixo:

```javascript
import React from 'react';
import { View, Image, Text, StyleSheet } from 'react-native';

export default function Pedidos() {
  return (
    <View style={styles.container}>
      <Text style={styles.aviso}>Você ainda não fez nenhum pedido</Text>
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
  aviso: {
    marginTop: 25,
    fontSize: 18,
    color: '#333',
  },
});
```

## Cria a página de pedidos anteriores

Crie um arquivo `src/screens/PedidosAnteriores/index.js` com o código abaixo:

```javascript
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

export default function PedidosAnteriores() {
  return (
    <View style={styles.container}>
      <Text>Pedidos Anteriores</Text>
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

# Ajustando as rotas

Vamos ajustar as rotas para que a tela de pedidos seja a tela inicial do nosso app. Para isso, vamos editar o arquivo `src/routes.js` adicionando o código abaixo:

```javascript
import { createMaterialTopTabNavigator } from '@react-navigation/material-top-tabs';
const Tab = createMaterialTopTabNavigator();

function PedidosRouter() {
  return (
    <Tab.Navigator>
      <Tab.Screen name="Pedidos" component={Pedidos} />
      <Tab.Screen
        name="PedidosAnteriores"
        component={PedidosAnteriores}
        options={% raw %}{{ tabBarLabel: 'Pedidos Anteriores' }}{% endraw %}
      />
    </Tab.Navigator>
  );
}
```

No mesmo arquivo `src/routes.js`, vamos alterar o componente `BottomTab.Navigator` do aba de `Pedidos` para utilizar o componente `PedidosRouter`:

```javascript
 <BottomTab.Screen
  name="Pedidos"
  component={PedidosRouter}
  options={% raw %}{{
    tabBarLabel: 'Pedidos',
    tabBarIcon: ({ color }) => (
      <MaterialIcons name="assignment" color={color} size={26} />
    ),
  }}{% endraw %}
/>
```
<span style="display: flex; justify-content: space-between;"><span>>[&lt; Home](home.html "Voltar")</span> <span>[Exercícios &gt;](exercicios.html "Próximo")</span></span>