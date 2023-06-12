---
title: "Criando um clone do IFood"
description: Criando um clone do IFood
permalink: /ifood
---
# Índice da aula
1. [Navegação inicial](ifood/navegacao-inicial.html)  
2. [Perfil](ifood/perfil.html)    
<!-- 2. [Componentes](intro/componentes.html)  
3. [Interpolação de lista](intro/interpolacao-lista.html)  
4. [Exercícios](intro/exercicios.html)   -->


# Um clone do IFood

O objetivo dessa aula é criar um clone do IFood utilizando os conhecimentos adquiridos nas aulas anteriores. 

## 1. Criando o projeto

Para criar o projeto, vamos utilizar o comando:

```bash
npx create-expo-app ifood-clone
```

Depois de criado, vamos abrir o projeto no Visual Studio Code:

```bash
cd ifood-clone
code .
```

## 2. Instalação das dependências iniciais

Para iniciar o projeto, instalaremos as dependencias para roteamento:
    
```bash
npm install @react-navigation/native @react-navigation/stack @react-navigation/bottom-tabs
```

## 3. Criando a estrutura de pastas

Para criar a estrutura de pastas, vamos criar uma pasta `src` e dentro dela, vamos criar as pastas `screens` e `components`. Ao longo do projeto, vamos criar os componentes e as telas dentro dessas pastas.

## 4. Criando os arquivos base para as primeiras telas

Vamos criar os arquivos base para as primeiras telas do nosso projeto. Para isso, vamos criar os arquivos de código das telas: `src/screens/Home/index.js` (Home), `src/screens/Busca/index.js` (Busca), `src/screens/Pedidos/index.js` (Pedidos) e `src/screens/Perfil/index.js` (Perfil).

Inicialmente, esses arquivos terão um conteúdo básico, apenas para diferenciar as telas. 

A tela Home terá o seguinte conteúdo:

```jsx
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

export default function Home() {
  return (
    <View style={styles.container}>
      <Text>Home</Text>
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

As telas Busca, Pedidos e Perfil terão o mesmo conteúdo básico, apenas com o nome da função e o texto diferentes.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](./ "Início")</span> <span>[Navegação inicial &gt;](ifood/navegacao-inicial.html "Próximo")</span></span>
