---
title: "Perfil"
permalink: /ifood/perfil
---

# Tela de perfil

Faremos agora a tela de perfil do usuário. Para isso, vamos editar arquivo `src/screens/Perfil/index.js` com o seguinte conteúdo:

```jsx
import React from 'react';
import {
  ScrollView,
  Text,
  TouchableOpacity,
  View,
  StyleSheet,
} from 'react-native';
import { MaterialCommunityIcons, MaterialIcons } from '@expo/vector-icons';

export default function Perfil({ navigation }) {
  return (
    <ScrollView style={styles.container}>
      <ScrollView>
        <TouchableOpacity style={styles.option} onPress={() => {}}>
          <MaterialCommunityIcons name="bell-outline" size={35} color="#333" />
          <ScrollView style={styles.info}>
            <Text style={styles.title}>Notificações</Text>
            <Text style={styles.description}>
              Minha central de notificações
            </Text>
          </ScrollView>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>
        <TouchableOpacity
          style={styles.option}
          onPress={() => navigation.navigate('Pagamentos')}
        >
          <MaterialCommunityIcons name="credit-card" size={35} color="#333" />
          <ScrollView style={styles.info}>
            <Text style={styles.title}>Pagamentos</Text>
            <Text style={styles.description}>Meus saldos e cartões</Text>
          </ScrollView>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>

        <TouchableOpacity style={styles.option} onPress={() => {}}>
          <MaterialCommunityIcons
            name="ticket-outline"
            size={35}
            color="#333"
          />
          <ScrollView style={styles.info}>
            <Text style={styles.title}>Cupons</Text>
            <Text style={styles.description}>Meus cupons de desconto</Text>
          </ScrollView>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>

        <TouchableOpacity style={styles.option} onPress={() => {}}>
          <MaterialCommunityIcons name="heart-outline" size={35} color="#333" />
          <ScrollView style={styles.info}>
            <Text style={styles.title}>Favoritos</Text>
            <Text style={styles.description}>Meus locais favoritos</Text>
          </ScrollView>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>

        <TouchableOpacity style={styles.option} onPress={() => {}}>
          <MaterialCommunityIcons name="credit-card" size={35} color="#333" />
          <ScrollView style={styles.info}>
            <Text style={styles.title}>Fidelidade</Text>
            <Text style={styles.description}>Minhas fidelidades</Text>
          </ScrollView>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>

        <TouchableOpacity style={styles.option} onPress={() => {}}>
          <MaterialCommunityIcons name="map-marker" size={35} color="#333" />
          <ScrollView style={styles.info}>
            <Text style={styles.title}>Endereços</Text>
            <Text style={styles.description}>Meus endereços de entrega</Text>
          </ScrollView>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>
      </ScrollView>

      <View style={styles.menuAdicional}>
        <TouchableOpacity style={styles.opcoesAdicionais}>
          <View style={styles.wrapper}>
            <MaterialCommunityIcons name="lifebuoy" size={25} color="#CDC" />
            <Text style={styles.optionName}>Ajuda</Text>
          </View>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>

        <TouchableOpacity style={styles.opcoesAdicionais}>
          <View style={styles.wrapper}>
            <MaterialIcons name="settings" size={25} color="#CDC" />
            <Text style={styles.optionName}>Configurações</Text>
          </View>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>

        <TouchableOpacity style={styles.opcoesAdicionais}>
          <View style={styles.wrapper}>
            <MaterialIcons name="security" size={25} color="#CDC" />
            <Text style={styles.optionName}>Segurança</Text>
          </View>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>

        <TouchableOpacity style={styles.opcoesAdicionais}>
          <View style={styles.wrapper}>
            <MaterialIcons name="store-mall-directory" size={25} color="#CDC" />
            <Text style={styles.optionName}>Sugerir Restaurantes</Text>
          </View>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>

        <TouchableOpacity style={styles.opcoesAdicionais}>
          <View style={styles.wrapper}>
            <MaterialCommunityIcons name="rocket" size={25} color="#CDC" />
            <Text style={styles.optionName}>Seja parceiro!</Text>
          </View>
          <MaterialIcons name="keyboard-arrow-right" color="#999" size={20} />
        </TouchableOpacity>
      </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
  option: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-around',
    marginTop: 5,
    paddingTop: 10,
    paddingBottom: 10,
    paddingLeft: 20,
    paddingRight: 20,
    border: 1,
  },
  info: {
    marginLeft: 20,
  },
  title: {
    color: '#333',
    fontSize: 18,
  },
  description: {
    fontSize: 16,
    color: '#999',
  },
  menuAdicional: {
    marginTop: 30,
  },

  opcoesAdicionais: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
    marginTop: 5,
    marginBottom: 5,
    marginLeft: 0,
    marginRight: 0,
    paddingTop: 10,
    paddingBottom: 10,
    paddingLeft: 20,
    paddingRight: 20,
    border: 1,
  },
  wrapper: {
    flexDirection: 'row',
    alignItems: 'center',
  },
  optionName: {
    marginLeft: 25,
    color: '#ccc',
    fontSize: 15,
  },
});
```


Note que a função Perfil recebe um parâmetro chamado `navigation`. Esse parâmetro é responsável por fazer a navegação entre as telas. No caso, estamos utilizando o método navigate para navegar para a tela de Pagamentos, usando o comando `navigation.navigate('Pagamentos')`.

Ainda, a tela define vários componentes do tipo TouchableOpacity, que são botões que podem ser clicados. Cada um desses botões possui um estilo próprio, e um evento de clique que chama a função `navigation.navigate` para navegar para a tela desejada.

Embora tenhamos definida apenas a navegação para a rota `Pagamentos`, você pode definir a navegação para outras rotas que forem desejadas.

## Tela de Pagamentos

A tela de Pagamentos ainda será bem simples, apenas para demonstrar a navegação entre as telas.
Vamos criar o arquivo `src/pages/Pagamentos/index.js` com o seguinte conteúdo:

```jsx
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

export default function Pagamentos() {
  return (
    <View style={styles.container}>
      <Text>Pagamentos</Text>
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

## Ajustes no arquivo de rotas

Depois de ajustar as telas, precisamos ajustar o arquivo de rotas para que as telas sejam exibidas corretamente. Para isso, vamos alterar o arquivo `src/routes.js` com as seguintes alterações:

* Adicionar a importação das telas de Perfil e Pagamentos:

```jsx
import Perfil from './pages/Perfil';
import Pagamentos from './pages/Pagamentos';
```

* Criar um stack navigator para as telas de Perfil e Pagamentos:

```jsx
const PerfilStack = createStackNavigator();

function PerfilRoutes() {
  return (
    <PerfilStack.Navigator>
      <PerfilStack.Screen name="Perfil" component={Perfil} />
      <PerfilStack.Screen name="Pagamentos" component={Pagamentos} />
    </PerfilStack.Navigator>
  );
} 
```

* Alterar o BottomTab.Screen para utilizar o componente PerfilRoutes:

```jsx
        <BottomTab.Screen
          name="PerfilRoutes"
          component={PerfilRoutes}
          options={% raw %}{{
            headerShown: false,
            tabBarLabel: 'Perfil',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="person" color={color} size={26} />
            ),
          }}{% endraw %}
        />
```

Note que a alteração acima foi feita para que a tela de Perfil seja exibida como uma stack, ou seja, com a possibilidade de navegar entre as telas de Perfil e Pagamentos. Se você executar o projeto agora, verá que a tela de Perfil será exibida, mas a tela de Pagamentos não será exibida. A exibição da tela de Pagamentos será feita a partir da tela de Perfil




<span style="display: flex; justify-content: space-between;"><span>>[&lt; Navegação inicial](navegacao-inicial.html "Voltar")</span> <span>[Exercícios &gt;](exercicios.html "Próximo")</span></span>