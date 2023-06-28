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

### Criando o arquivo de dados

Crie um arquivo chamado `server.json` com o seguinte conteúdo:

```json
{
  "suggestions": [
    {
      "id": 1,
      "title": "Bebidas",
      "sugg_url": "https://live.staticflickr.com/3567/3358256632_231074ae3c_c.jpg"
    },
    {
      "id": 2,
      "title": "Café & Padaria",
      "sugg_url": "https://live.staticflickr.com/131/344713294_8fae6be5e1_b.jpg"
    },
    {
      "id": 3,
      "title": "Doces",
      "sugg_url": "https://live.staticflickr.com/5559/14657787373_4e325006da_h.jpg"
    },
    {
      "id": 4,
      "title": "Promoções",
      "sugg_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_medium/pratos/704d4888-f4f4-4ad5-b520-6a2cd631f854/201907291413_dUKd_3.png"
    },
    {
      "id": 5,
      "title": "Doação",
      "sugg_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_medium/pratos/b967e2f9-fe05-471d-913e-4fe463d5dbb9/201912171124_jD6O_i.png"
    }
  ],
  "promotions": [
    {
      "id": 1,
      "categorie": "OS MELHORES DO IFOOD",
      "promo_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_high/discoveries/ifood-capas-novas-super-restaurantes2.jpg"
    },
    {
      "id": 2,
      "categorie": "JANTAR IFOOD",
      "promo_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_high/discoveries/ifood-capas-novas-jantar10-2.jpg"
    },
    {
      "id": 3,
      "categorie": "TAXA NA FAIXA",
      "promo_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_high/discoveries/ifood-capas-novas-taxa-gratis.jpg"
    },
    {
      "id": 4,
      "categorie": "PROMOÇÕES POR R$4,99",
      "promo_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_high/discoveries/ifood-capas-tudo-por-10-reais.png"
    }
  ],
  "offers": [
    {
      "id": 1,
      "title": "McOferta Big Mac",
      "offer_url": "https://mcd-production.ams3.digitaloceanspaces.com/produtos/bigmac_62364267588f60a0780c9_7.jpg",
      "price": 30.90,
      "newPrice": 26.50,
      "ingredients": "Ingredientes frescos",
      "delivery": "McDonalds's | Bebedouro Shopping",
      "delay": "45-90 min",
      "icon": "store"
    },
    {
      "id": 2,
      "title": "McOferta McChicken",
      "offer_url": "https://www.mcdonalds.com/is/image/content/dam/usa/nfl/nutrition/items/hero/desktop/t-mcdonalds-McChicken.jpg",
      "price": 22.00,
      "newPrice": 17.90,
      "ingredients": "Ingredientes frescos",
      "delivery": "McDonalds's | Bebedouro Shopping",
      "delay": "45-90 min",
      "icon": "store"
    },
    {
      "id": 3,
      "title": "Combo Big King",
      "offer_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_medium/pratos/6e73dce2-a17f-4aef-9035-1409cea198fe/202002111702_EFlu_.jpeg",
      "price": 32.00,
      "newPrice": 28.90,
      "ingredients": "Ingredientes frescos",
      "delivery": "BURGER KING® | Bebedouro Shopping",
      "delay": "45-90 min",
      "icon": "store"
    },
    {
      "id": 4,
      "title": "Compre 1 leve 2 (frango empanado de 15)",
      "offer_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_medium/pratos/f627d0e7-f129-4764-8f00-18814b1b9068/201907171144_TLPZ_f.jpg",
      "price": 45.90,
      "newPrice": 22.90,
      "ingredients": "Ingredientes frescos",
      "delivery": "Subway® - Praça Valêncio de Barros",
      "delay": "35-70 min",
      "icon": "store"
    }
  ],
  "categories": [
    {
      "id": 1,
      "title": "Brasileira",
      "categorie_url": "https://farm4.static.flickr.com/3748/9699877429_68d829c600_c.jpg"
    },
    {
      "id": 2,
      "title": "Carnes",
      "categorie_url": "https://farm9.static.flickr.com/8026/28997985340_97bbd9966f_c.jpg"
    },
    {
      "id": 3,
      "title": "Lanches",
      "categorie_url": "https://farm9.static.flickr.com/8532/8607941081_64837859f9_c.jpg"
    },
    {
      "id": 4,
      "title": "Japonesa",
      "categorie_url": "https://live.staticflickr.com/152/348622907_d759f02862_b.jpg"
    },
    {
      "id": 5,
      "title": "Italiana",
      "categorie_url": "https://live.staticflickr.com/4130/4957272425_85d2dd19df_b.jpg"
    },
    {
      "id": 6,
      "title": "Pizza",
      "categorie_url": "https://live.staticflickr.com/7557/16024361559_ea0788337d_h.jpg"
    },
    {
      "id": 7,
      "title": "Salgados & Pastéis",
      "categorie_url": "https://farm3.static.flickr.com/2831/9721033596_f65752349e_b.jpg"
    },
    {
      "id": 8,
      "title": "Saudável",
      "categorie_url": "https://farm8.static.flickr.com/7336/8716617128_be1c8d8cf3_b.jpg"
    },
    {
      "id": 9,
      "title": "Congelados",
      "categorie_url": "https://live.staticflickr.com/5251/5559164555_c205dceda3_h.jpg"
    },
    {
      "id": 10,
      "title": "Marmitas",
      "categorie_url": "https://live.staticflickr.com/8304/7890484144_c17caf95b9_c.jpg"
    },
    {
      "id": 11,
      "title": "Doces & Sorvetes",
      "categorie_url": "https://live.staticflickr.com/3570/3544235183_eae55601ba_b.jpg"
    },
    {
      "id": 12,
      "title": "Bebidas",
      "categorie_url": "https://live.staticflickr.com/1819/42231172380_96c6ad5390_h.jpg"
    }
  ],
  "restaurants": [
    {
      "id": 1,
      "restaurant_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_thumbnail/logosgde/201907222152_777201af-bd2b-456c-ba4c-f89d671a9b5e.png",
      "title": "McDonald's",
      "star": 4.7,
      "categories": [
        "Lanches"
    ],
      "delay": "45-90 min",
      "distance": "3.4 km"
    },
    {
      "id": 2,
      "restaurant_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_thumbnail/logosgde/202002272108_30f00633-e7d9-4b30-883b-8f701353a6af.png",
      "title": "Burger King",
      "star": 4.6,
      "categories": [
        "Lanches"
    ],
      "delay": "45-90 min",
      "distance": "3.4 km"
    },
    {
      "id": 3,
      "restaurant_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_thumbnail/logosgde/201901041516_adfc3efe-3950-4d8d-b2af-e103445aa79a.png",
      "title": "Subway",
      "star": 4.4,
      "categories": [
        "Lanches"
    ],
      "delay": "35-70 min",
      "distance": "2.3 km"
    },
    {
      "id": 4,
      "restaurant_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_thumbnail/logosgde/a20ae81a-7345-4165-91cc-35ec91020637/201910281151_3TRJ_i.png",
      "title": "Sushi da Facul",
      "star": 4.3,
      "categories": [
        "Japonesa"
    ],
      "delay": "40-50 min",
      "distance": "1.7 km"
    },
    {
      "id": 5,
      "restaurant_url": "https://static-images.ifood.com.br/image/upload/f_auto,t_thumbnail/logosgde/02602d2b-d6cb-469f-92d4-2e4518c4acbd/201911221041_W80r_i.png",
      "title": "Pimentas Bar",
      "star": 4.2,
      "categories": [
        "Brasileira"
    ],
      "delay": "50-60 min",
      "distance": "2.4 km"
    }
  ]
}
```

### Executando o json-server

Para executar o json-server, basta executar o comando abaixo:

```bash
json-server -H 191.191.191.191 server.json
```

Onde o IP (191.191.191.191) deve ser o IP da sua máquina. Preste muita atenção nesta etapa. O endereço IP você pode ver quando executar a o npm start do expo. 

Outro ponto importante é que o json-server deve estar sempre em execução. Então, não feche o terminal que você executou o comando acima.

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
  baseURL: 'http://191.191.191.191:3000',
});

export default api;
```

Sendo que o IP (191.191.191.191) deve ser o IP da sua máquina, o mesmo que você usou para executar o json-server.

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
          <Image source={% raw %}{{ uri: sugestao.sugg_url }} {% endraw %}style={styles.imagem} />
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
          <Image source={% raw %}{{ uri: promocao.promo_url }} {% endraw %}style={styles.imagem} />
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
        {ofertas.map((oferta) => {
          <TouchableOpacity style={styles.item} key={oferta.id}>
            <Image source={% raw %}{{ uri: oferta.offer_url }} {% endraw %}style={styles.imagem} />
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
              source={% raw %}{{ uri: categoria.categorie_url }} {% endraw %}
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
              source={% raw %}{{ uri: restaurante.restaurant_url }} {% endraw %}
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
                <Text style={styles.categorias}> {restaurante.categories}</Text>
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