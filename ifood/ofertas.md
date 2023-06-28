---
title: Ofertas"
permalink: /ifood/ofertas
---

# Tela Detalhes da Oferta

Nessa etapa, vamos criar o arquivo `src/screens/Item/index.js` com o código abaixo:

```javascript
import React from 'react';
import { MaterialIcons } from '@expo/vector-icons';

import { Image, ScrollView, Text, View, StyleSheet } from 'react-native';

export default function Item({ route, navigation }) {
  const { item } = route.params;

  return (
    <ScrollView showsVerticalScrollIndicator={true} style={styles.container}>
      <View style={styles.detalhe}></View>
      <Image style={styles.itemImage} source={%raw %}{{ uri: item.offer_url }} {% endraw %} />
      <Text style={styles.itemTitulo}>{item.title}</Text>
      <Text style={styles.itemIngredientes}>{item.ingredients}</Text>
      <View style={styles.info}>
        <Text style={styles.itemPreco}>{item.newPrice}</Text>
        <Text style={styles.itemPrecoAntigo}>{item.price}</Text>
      </View>

      <View style={styles.entrega}>
        <View style={styles.wrapper}>
          <MaterialIcons name={item.icon} size={22} color="#F01" />
          <Text style={styles.entregaTitulo}>{item.delivery}</Text>
        </View>
        <Text style={styles.entregaAtraso}>{item.delay}</Text>
      </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    backgroundColor: '#fff',
  },
  detalhe: {
    marginTop: 10,
    marginBottom: 0,
    marginHorizontal: 20,
  },
  itemImage: {
    height: 180,
    borderRadius: 5,
  },
  itemTitulo: {
    fontSize: 32,
    color: '#333',
    fontWeight: 'bold',
    marginTop: 10,
  },
  itemIngredientes: {
    fontSize: 18,
    color: '#999',
    marginTop: 10,
  },
  itemPreco: {
    color: 'green',
    fontSize: 22,
  },
  itemPrecoAntigo: {
    marginLeft: 5,
    color: '#999',
    fontSize: 22,
    textDecorationLine: 'line-through',
  },
  entrega: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    marginTop: 20,
    borderWidth: 1,
    borderColor: '#eee',
    borderRadius: 2,
    padding: 15,
  },
  wrapper: {
    flexDirection: 'row',
    alignItems: 'center',
  },
  entregaTitulo: {
    fontSize: 15,
    color: 'red',
  },
  entregaAtraso: {
    marginLeft: 10,
  },
});
```

## Editar o componente de Ofertas

Vamos agora editar o arquivo que lista as ofertas, para que ele possa navegar para a tela de detalhes da oferta. Para isso, vamos editar o arquivo `src/components/Home/Ofertas.js` com o código abaixo:

```javascript
import React, { useEffect, useState } from 'react';
import { MaterialIcons } from '@expo/vector-icons';
import {
  Image,
  ScrollView,
  Text,
  TouchableOpacity,
  View,
  StyleSheet,
} from 'react-native';

import api from '../../services/api';
import { formatNumber } from '../../helpers/formatNumber';

export default function Ofertas({ navigation }) {
  const [ofertas, setOfertas] = useState([]);
  useEffect(() => {
    async function carregarOfertas() {
      const response = await api.get('offers');
      const data = response.data.map((offer) => ({
        id: offer.id,
        offer_url: offer.offer_url,
        title: offer.title,
        newPrice: formatNumber(offer.newPrice),
        price: formatNumber(offer.price),
        ingredients: offer.ingredients,
        delivery: offer.delivery,
        delay: offer.delay,
        icon: offer.icon,
      }));
      setOfertas(data);
    }
    carregarOfertas();
  }, []);

  return (
    <View style={styles.container}>
      <View style={styles.header}>
        <View>
          <Text style={styles.titulo}>Comida boa e barata!</Text>
          <Text style={styles.subTitulo}>Pratos com frete grátis.</Text>
        </View>
        <TouchableOpacity>
          <Text style={styles.vejaMais}>Ver mais</Text>
        </TouchableOpacity>
      </View>
      <ScrollView
        showsHorizontalScrollIndicator={false}
        horizontal
        style={styles.lista}
      >
        {ofertas.map((oferta) => (
          <TouchableOpacity
            style={styles.item}
            key={oferta.id}
            onPress={() => navigation.navigate('Item', { item: oferta })}
          >
            <Image source={% raw %} {{ uri: oferta.offer_url }} {% endraw %} style={styles.imagem} />
            <View style={styles.info}>
              <Text numberOfLines={2} style={styles.titulo}>
                {oferta.title}
              </Text>
              <View style={styles.itemPreco}>
                <Text style={styles.preco}>{oferta.newPrice}</Text>
                <Text style={styles.precoAntigo}>{oferta.price}</Text>
                <MaterialIcons name="local-offer" size={15} color="#000" />
              </View>
            </View>
          </TouchableOpacity>
        ))}
      </ScrollView>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    marginVertical: 20,
    marginHorizontal: 0,
  },
  header: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
    marginTop: 0,
    marginRight: 10,
    marginBottom: 15,
    marginLeft: 20,
  },
  titulo: {
    fontSize: 23,
    fontWeight: 'bold',
  },
  subTitulo: {
    color: '#999',
  },
  vejaMais: {
    color: 'red',
  },
  lista: {
    paddingLeft: 20,
  },
  item: {
    width: 200,
    marginRight: 15,
    borderWidth: 1,
    borderStyle: 'solid',
    borderColor: 'rbga(0,0,0, 0.06)',
    borderRadius: 4,
  },
  imagem: {
    height: 120,
    width: 200,
    backgroundColor: '#000',
  },
  info: {
    marginTop: 'auto',
    padding: 10,
  },
  itemPreco: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    marginTop: 10,
  },
  preco: {
    color: 'green',
    fontWeight: 'bold',
    fontSize: 18,
  },
  precoAntigo: {
    marginLeft: 5,
    fontWeight: 'bold',
    color: '#999',
    fontSize: 16,
    textDecorationLine: 'line-through',
  },
});
```

Nesse código, além da chamada da rota, foi ajustada a chamada da função `formatNumber` para que ela possa formatar os valores de preço, e o retorno da função map foi ajustado para que ele possa retornar um objeto com os dados da oferta.

## Editar a tela Home

Em seguida, vamos editar a tela Home para que ela possa navegar para a tela de detalhes da oferta. Para isso, vamos editar o arquivo `src/screens/Home/index.js` com o código abaixo:

```javascript
import React from 'react';

import { ScrollView, StyleSheet } from 'react-native';
import Endereco from '../../components/Home/Endereco';
import Input from '../../components/Input';
import CupomDesconto from '../../components/Home/CupomDesconto';
import Sugestoes from '../../components/Home/Sugestoes';
import Promocoes from '../../components/Home/Promocoes';
import Ofertas from '../../components/Home/Ofertas';
import Categorias from '../../components/Home/Categorias';
import Restaurantes from '../../components/Home/Restaurantes';

export default function Home({ navigation }) {
  return (
    <ScrollView showsHorizontalScrollIndicator={true} style={styles.container}>
      <Endereco />
      <Input placeholder="Busque por item ou loja" />
      <CupomDesconto />
      <Sugestoes />
      <Promocoes />
      <Ofertas navigation={navigation} />
      <Categorias />
      <Restaurantes />
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
});
```

Note que alteramos a definição da função Home para receber o parâmetro `navigation` e passamos esse parâmetro para o componente `Ofertas`.


# Ajustando as rotas

Vamos ajustar as rotas para que a tela de pedidos seja a tela inicial do nosso app. Para isso, vamos editar o arquivo `src/routes.js` com o código abaixo:

```javascript
import React from 'react';

import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import { createMaterialTopTabNavigator } from '@react-navigation/material-top-tabs';

import { MaterialIcons } from '@expo/vector-icons';

import Home from './screens/Home';
import Busca from './screens/Busca';
import Perfil from './screens/Perfil';
import Pedidos from './screens/Pedidos';
import PedidosAnteriores from './screens/PedidosAnteriores';
import Pagamentos from './screens/Pagamentos';
import Item from './screens/Item';

const BottomTab = createBottomTabNavigator();
const Stack = createNativeStackNavigator();
const Tab = createMaterialTopTabNavigator();

function HomeRoutes() {
  return (
    <Stack.Navigator>
      <Stack.Screen name="Home" component={Home} />
      <Stack.Screen name="Item" component={Item} />
    </Stack.Navigator>
  );
}

function PedidosRouter() {
  return (
    <Tab.Navigator>
      <Tab.Screen name="Pedidos" component={Pedidos} />
      <Tab.Screen
        name="PedidosAnteriores"
        component={PedidosAnteriores}
        options={%raw %}{{ tabBarLabel: 'Pedidos Anteriores' }} {% endraw %}
      />
    </Tab.Navigator>
  );
}

function PerfilRoutes() {
  return (
    <Stack.Navigator>
      <Stack.Screen name="Perfil" component={Perfil} />
      <Stack.Screen name="Pagamentos" component={Pagamentos} />
    </Stack.Navigator>
  );
}

export default function Routes() {
  return (
    <NavigationContainer>
      <BottomTab.Navigator
        screenOptions={% raw %}{{
          tabBarActiveTintColor: 'red',
          tabBarInactiveTintColor: 'black',
        }} {% endraw %}
      >
        <BottomTab.Screen
          name="HomeRoutes"
          component={HomeRoutes}
          options={% raw %} {{
            tabBarLabel: 'Home',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="home" color={color} size={26} />
            ),
          }} {% endraw %}
        />
        <BottomTab.Screen
          name="Busca"
          component={Busca}
          options={% raw %} {{
            tabBarLabel: 'Busca',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="search" color={color} size={26} />
            ),
          }} {% endraw %}
        />
        <BottomTab.Screen
          name="PedidosRouter"
          component={PedidosRouter}
          options={% raw %} {{
            tabBarLabel: 'Pedidos',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="assignment" color={color} size={26} />
            ),
          }} {% endraw %}
        />
        <BottomTab.Screen
          name="PerfilRoutes"
          component={PerfilRoutes}
          options={% raw %} {{
            headerShown: false,
            tabBarLabel: 'Perfil',
            tabBarIcon: ({ color }) => (
              <MaterialIcons name="person" color={color} size={26} />
            ),
          }} {% endraw %}
        />
      </BottomTab.Navigator>
    </NavigationContainer>
  );
}
```

Note que alteramos a chamada para o componente `Home` para que ele seja chamado dentro do componente `HomeRoutes`. Isso foi necessário para que a tela de detalhes da oferta pudesse ser acessada através da navegação. Também adicionamos o componente `Item` dentro do componente `HomeRoutes` para que ele possa ser acessado através da navegação.

Foi ajustado também o componente `PedidosRouter`, eliminando uma duplicidade de nomes de rotas.

<span style="display: flex; justify-content: space-between;"><span>>[&lt; Pedidos](pedidos.html "Voltar")</span> <span>[Exercícios &gt;](exercicios.html "Próximo")</span></span>