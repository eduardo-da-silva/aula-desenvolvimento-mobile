---
title: Home"
permalink: /ifood/home
---

# Tela Home

Nessa etapa, vamos construir a tela inicial do aplicativo. Mas, precisamos criar um servidor para que possamos consumir os dados. Para isso, vamos utilizar o [json-server](https://github.com/typicode/json-server), com dados de exemplo.

## Instalando o json-server

Para instalar o json-server, vamos executar o seguinte comando:

```bash
npm install -g json-server
```

### Acessando um servidor remoto

Para este exercício, foi criado um container Docker. Para acessar o container, execute o comando abaixo:

```bash
sudo docker run -p 19003:19003 eduardosilvasc/django_clone_ifood:latest
```

Importante: O container deve estar sempre em execução. Então, não feche o terminal que você executou o comando acima. 

Importante 2: Sendo um container, vale ressaltar que as alterações que você fizer no banco de dados serão perdidas quando você reiniciar o container.

Para acessar a documentação da API, acesse: http://localhost:19003/api/ 

Importante 3: Lembre que para acessar via celular, você deve usar o IP da sua máquina. Para saber o IP da sua máquina, execute o comando abaixo:

```bash
nmcli device show | grep IP4.ADDRESS | head -1 | awk '{print $2}' | rev | cut -c 4- | rev
```

Caso você queira ter acesso ao código fonte desse projeto, feito em Django, acesse: https://github.com/eduardo-da-silva/backend-clone-Ifood

# Instalando as dependências

Vamos precisar de algumas dependências para o nosso projeto. Execute os comandos abaixo para instalar as dependências:

```bash
npm install axios numeral
```

O axios é uma biblioteca para fazer requisições HTTP. O numeral é uma biblioteca para formatar números.

## Configurando o axios

O axios é uma biblioteca para fazer requisições HTTP. Vamos configurar o axios para que ele sempre faça as requisições para o nosso servidor. Crie um arquivo chamado `api.js` na pasta `src/services` e adicione o código abaixo:

```javascript
import axios from 'axios';

const api = axios.create({
  baseURL: 'http://191.191.191.191:19003/api/',
});

export default api;
```

Sendo que o IP (191.191.191.191) deve ser o IP da sua máquina. Relembrando, para descobrir o IP execute:

```bash
nmcli device show | grep IP4.ADDRESS | head -1 | awk '{print $2}' | rev | cut -c 4- | rev
```

## Configurando o numeral

O numeral é uma biblioteca para formatar números. Vamos configurar o numeral para que ele sempre formate os números para o padrão brasileiro. Crie um arquivo chamado `formatNumber.js` na pasta `src/helpers` e adicione o código abaixo:

```javascript
import numeral from 'numeral';

export const formatNumber = (number) => numeral(number).format('$,0.00');
```

Neste arquivo, estamos criando uma função chamada `formatNumber` que recebe um número e retorna o número formatado para o padrão brasileiro.

# Criando os componentes

## Componente de Input

Crie um arquivo chamado `index.js` na pasta `src/components/Input` e adicione o código abaixo:

```javascript
import React from 'react';
import { MaterialIcons } from '@expo/vector-icons';
import { TextInput, View, StyleSheet } from 'react-native';

export default function Input(props) {
  return (
    <View style={styles.container}>
      <MaterialIcons name="search" size={25} color={'#FF5665'} />

      <TextInput style={styles.textInput} placeholder={props.placeholder} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    background: '#EEE',
    height: 'auto',
    flexDirection: 'row',
    alignItems: 'center',
    margin: 20,
    paddingLeft: 10,
    borderRadius: 4,
  },
  textInput: {
    paddingVertical: 15,
    paddingHorizontal: 20,
  },
});
```

## Componente de Endereço

* Todos os demais componentes serão criados na pasta `src/components/Home`.

Crie um arquivo chamado `Endereco.js` na pasta `src/components/Home` e adicione o código abaixo:

```javascript
import React from 'react';
import { MaterialIcons } from '@expo/vector-icons';
import { Text, TouchableOpacity, View, StyleSheet } from 'react-native';

export default function Endereco() {
  return (
    <View style={styles.container}>
      <TouchableOpacity style={styles.menuEndereco}>
        <Text style={styles.localizacao}>Próximo de minha casa...</Text>
        <MaterialIcons name="keyboard-arrow-down" size={20} color={'#FF5665'} />
      </TouchableOpacity>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    paddingVertical: 10,
    paddingHorizontal: 20,
  },
  menuEndereco: {
    flexDirection: 'row',
  },
  localizacao: {
    color: '#333',
    fontSize: 16,
    fontWeight: 'bold',
  },
});
```

## Componente de Cupom de desconto

Crie um arquivo chamado `CupomDesconto.js` na pasta `src/components/Home` e adicione o código abaixo:

```javascript
import React from 'react';
import { MaterialIcons } from '@expo/vector-icons';
import { Image, Text, TouchableOpacity, View, StyleSheet } from 'react-native';

export default function CupomDesconto() {
  return (
    <TouchableOpacity style={styles.cupom}>
      <View style={styles.divisor}>
        <View style={styles.conteudo}>
          <Image
            source={require('../../assets/discount-coupon.png')}
            style={styles.logo}
          />
          <View style={styles.info}>
            <Text style={styles.titulo}>Cupom de R$10</Text>
            <Text style={styles.validade}>Válido até as 17:30</Text>
          </View>
        </View>
        <MaterialIcons
          name="keyboard-arrow-right"
          color={'#FF5665'}
          size={20}
        />
      </View>
    </TouchableOpacity>
  );
}

const styles = StyleSheet.create({
  cupom: {
    borderColor: 'rgba(0,0,0,.1)',
    borderStyle: 'solid',
    borderWidth: 1,
    borderRadius: 4,
    paddingVertical: 5,
    paddingHorizontal: 15,
    marginVertical: 0,
    marginHorizontal: 20,
  },
  divisor: {
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
  },
  conteudo: {
    flexDirection: 'row',
    alignItems: 'center',
  },
  logo: {
    width: 50,
    height: 50,
  },
  info: {
    marginLeft: 10,
  },
  titulo: {
    fontWeight: 'bold',
  },
  validade: {
    marginTop: 5,
    color: '#999',
  },
});
```

## Componente de Sugestões

* A partir de agora, faremos uso de dados que estão no servidor `json-server`

Crie um arquivo chamado `Sugestoes.js` na pasta `src/components/Home` e adicione o código abaixo:

```javascript
import React, { useState, useEffect } from 'react';
import {
  Image,
  ScrollView,
  Text,
  TouchableOpacity,
  StyleSheet,
} from 'react-native';

import api from '../../services/api';

export default function Sugestoes() {
  const [sugestoes, setSugestoes] = useState([]);
  useEffect(() => {
    async function carregarSugestoes() {
      const response = await api.get('suggestions');
      setSugestoes(response.data);
    }
    carregarSugestoes();
  }, []);
  return (
    <ScrollView showsHorizontalScrollIndicator={false} style={styles.lista}>
      {sugestoes.map((sugestao) => (
        <TouchableOpacity style={styles.item} key={sugestao.id}>
          <Image source={% raw %}{{ uri: sugestao.image }} {% endraw %}style={styles.imagem} />
          <Text style={styles.titulo}>{sugestao.title}</Text>
        </TouchableOpacity>
      ))}
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  lista: {
    marginTop: 20,
    paddingLeft: 5,
  },
  item: {
    alignItems: 'center',
    marginLeft: 15,
  },
  imagem: {
    width: 100,
    height: 50,
    borderRadius: 5,
  },
  titulo: {
    marginTop: 3,
    color: '#999',
  },
});
```

## Componente de Promocoes

Crie um arquivo chamado `Promocoes.js` na pasta `src/components/Home` e adicione o código abaixo:

```javascript
import React, { useState, useEffect } from 'react';
import { Image, TouchableOpacity, ScrollView, StyleSheet } from 'react-native';
import api from '../../services/api';

export default function Promocoes({ navigation }) {
  const [promocoes, setPromocoes] = useState([]);

  useEffect(() => {
    async function carregarPromocoes() {
      const response = await api.get('promotions');
      setPromocoes(response.data);
    }
    carregarPromocoes();
  }, []);

  return (
    <ScrollView
      showsHorizontalScrollIndicator={false}
      horizontal
      style={styles.lista}
    >
      {promocoes.map((promocao) => (
        <TouchableOpacity style={styles.item} key={promocao.id}>
          <Image source={% raw %}{{ uri: promocao.image }} {% endraw %}style={styles.imagem} />
        </TouchableOpacity>
      ))}
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  lista: {
    marginVertical: 20,
    marginHorizontal: 0,
    paddingLeft: 5,
  },
  item: {
    marginLeft: 15,
  },
  imagem: {
    width: 300,
    height: 150,
  },
});
```

## Compoente de Ofertas

Crie um arquivo chamado `Ofertas.js` na pasta `src/components/Home` e adicione o código abaixo:

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
import formatNumber from '../../helpers/formatNumber';

export default function Ofertas({ navigation }) {
  const [ofertas, setOfertas] = useState([]);
  useEffect(() => {
    async function carregarOfertas() {
      const response = await api.get('offers');
      const data = response.data.map((offer) => ({
        id: offer.id,
        image: offer.image,
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
        {ofertas.map((oferta) => {
          <TouchableOpacity style={styles.item} key={oferta.id}>
            <Image source={% raw %}{{ uri: oferta.image }} {% endraw %}style={styles.imagem} />
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
          </TouchableOpacity>;
        })}
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

## Componente de Categorias

Crie um arquivo chamado `Categorias.js` na pasta `src/components/Home` e adicione o código abaixo:

```javascript
import React, { useEffect, useState } from 'react';
import {
  Image,
  ScrollView,
  Text,
  TouchableOpacity,
  View,
  StyleSheet,
} from 'react-native';
import api from '../../services/api';

export default function Categorias() {
  const [categorias, setCategorias] = useState([]);

  useEffect(() => {
    async function carregarCategorias() {
      const response = await api.get('categories');
      setCategorias(response.data);
    }
    carregarCategorias();
  }, []);

  return (
    <View style={styles.container}>
      <View style={styles.header}>
        <Text style={styles.titulo}>Categorias</Text>
      </View>
      <ScrollView
        showsHorizontalScrollIndicator={false}
        horizontal
        style={styles.lista}
      >
        {categorias.map((categoria) => (
          <TouchableOpacity key={categoria.id} style={styles.item}>
            <Image
              source={% raw %}{{ uri: categoria.image }} {% endraw %}
              style={styles.imagem}
            />
            <Text style={styles.categoriaTitulo}>{categoria.title}</Text>
          </TouchableOpacity>
        ))}
      </ScrollView>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    marginVertical: 30,
    marginHorizontal: 0,
  },
  header: {
    marginLeft: 20,
  },
  titulo: {
    fontSize: 23,
    fontWeight: 'bold',
  },
  lista: {
    marginTop: 10,
    paddingLeft: 20,
  },
  item: {
    marginRight: 15,
    alignItems: 'center',
  },
  imagem: {
    width: 200,
    height: 120,
    borderRadius: 10,
  },
  categoriaTitulo: {
    fontSize: 16,
    marginTop: 10,
    color: '#999',
  },
});
```

## Componente de Restaurantes

Crie um arquivo chamado `Restaurantes.js` na pasta `src/components/Home` e adicione o código abaixo:

```javascript
import React, { useEffect, useState } from 'react';
import {
  Image,
  ScrollView,
  View,
  Text,
  TouchableOpacity,
  StyleSheet,
} from 'react-native';
import { MaterialIcons } from '@expo/vector-icons';

import api from '../../services/api';

export default function Restaurantes() {
  const [restaurantes, setRestaurantes] = useState([]);

  useEffect(() => {
    async function carregarRestaurantes() {
      const response = await api.get('restaurants');
      setRestaurantes(response.data);
    }
    carregarRestaurantes();
  }, []);

  return (
    <View style={styles.container}>
      <View>
        <Text style={styles.titulo}>Restaurantes</Text>
      </View>
      <ScrollView style={styles.lista}>
        {restaurantes.map((restaurante) => (
          <TouchableOpacity style={styles.item} key={restaurante.id}>
            <Image
              source={% raw %}{{ uri: restaurante.image }} {% endraw %}
              style={styles.imagem}
            />
            <View style={styles.info}>
              <Text style={styles.restauranteTitulo}>
                {' '}
                {restaurante.title}{' '}
              </Text>
              <View style={styles.descricao}>
                <MaterialIcons name="star" size={20} color="#FF7C01" />
                <Text style={styles.estrela}>
                  {restaurante.star || 'Novo!'}
                </Text>
                <Text style={styles.categorias}> {restaurante.category.title}</Text>
                <Text style={styles.distancia}> {restaurante.distance}</Text>
              </View>
              <Text style={styles.atraso}> {restaurante.delay} </Text>
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
    marginLeft: 20,
    marginRight: 0,
  },
  titulo: {
    fontSize: 23,
    fontWeight: 'bold',
  },
  lista: {
    marginTop: 10,
  },
  item: {
    flexDirection: 'row',
    padding: 20,
    borderWidth: 1,
    borderStyle: 'solid',
    borderColor: 'rgba(0,0,0,0.1)',
    borderRadius: 4,
    marginTop: 5,
    marginRight: 15,
  },
  imagem: {
    width: 60,
    height: 60,
    borderRadius: 30,
  },
  info: {
    marginLeft: 15,
  },
  restauranteTitulo: {
    fontWeight: 'bold',
    color: '#333',
  },
  descricao: {
    flexDirection: 'row',
    marginTop: 3,
    alignItems: 'center',
  },
  estrela: {
    fontSize: 14,
    color: '#999',
  },
  categorias: {
    fontSize: 14,
    color: '#999',
  },
  distancia: {
    fontSize: 14,
    color: '#999',
  },
  atraso: {
    marginTop: 15,
    fontSize: 14,
    color: '#999',
  },
});
```

# Ajustando a Home

Agora que temos os componentes criados, vamos ajustar a Home para que ela fique com a cara do iFood.

Abra o arquivo `screens/Home/index.js` e adicione o código abaixo:

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

export default function Home() {
  return (
    <ScrollView showsHorizontalScrollIndicator={true} style={styles.container}>
      <Endereco />
      <Input placeholder="Busque por item ou loja" />
      <CupomDesconto />
      <Sugestoes />
      <Promocoes />
      <Ofertas />
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

<span style="display: flex; justify-content: space-between;"><span>>[&lt; Perfil](perfil.html "Voltar")</span> <span>[Pedidos &gt;](pedidos.html "Próximo")</span></span>