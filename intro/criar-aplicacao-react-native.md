---
title: "Instalação e criação de uma aplicação"
permalink: /intro/criar-aplicacao-react-native
---

### Introdução

Criar um primeiro projeto usando o React Native com Expo.

### Preparação

* Garantir que os passos da [Aula 0](../ambiente) foram executados.

# Criação de uma aplicação React Native

Vamos inicialmente criar uma aplicação React Native com Expo. Para isso, basta executar o seguinte comando:

```bash
npx create-expo-app exemplo-inicial-react-native
```

O comando anterior irá criar uma aplicação React Native usando uma ferramenta de scaffolding chamada `create-expo-app`. Em seguida, basta acessar a pasta do projeto e executar o comando `npm start` para iniciar a aplicação:

```bash
cd exemplo-inicial-react-native
npm run start
```
Note que código acima, inicialmente foi acessado o diretório do projeto. Então, foi invocado comando `npm run start`, que executa o script start definido no arquivo `package.json` do projeto. Isso permite que o seu aplicativa seja acessado por meio do Expo Go em um dispositivo físico.

Em seguida, basta abrir o aplicativo Expo Go no seu celular e escanear o QR Code que aparecerá no terminal. O Expo Go é um aplicativo que permite a execução de aplicações React Native em um dispositivo físico. Para instalar o Expo Go, basta acessar a [Play Store](https://play.google.com/store/apps/details?id=host.exp.exponent&hl=pt_BR&gl=US) ou a [App Store](https://apps.apple.com/br/app/expo-go/id982107779).

<!-- Caso o aplicativo Expo Go não consiga escanear o QR Code, você pode tentar executar o comando `npx expo start` com a flag `--tunnel`:

```bash
npx expo start --tunnel
```

Note que código acima foi invocado comando `npx expo start -- --tunnel`, sendo que a flag `--tunnel` é passada como argumento para o script e é usada para iniciar o servidor de desenvolvimento do Expo no modo túnel, permitindo o acesso do seu aplicativo de qualquer lugar do mundo e o teste em um dispositivo real. -->

## Manter um repositório Git

É muito importante que logo após a criação do projeto você crie um repositório Git para o projeto. Para isso, você pode usar o próprio Visual Studio Code. Para isso, abra o menu `Source Control` e clique em `Initialize Repository`. Em seguida, clique em `Create Repository`. O Visual Studio Code irá criar um repositório Git na pasta do projeto. Isso requer que o usuário tenha o Git instalado e configurado. Para mais informações, consulte a [Aula 0](../ambiente).

Também, é importante que a cada alteração que você fizer no projeto, você faça um commit. Para isso, abra o menu `Source Control` e clique em `Stage All Changes`. Em seguida, clique em `Commit`. O Visual Studio Code irá criar um commit com as alterações realizadas. Para mais informações, consulte a [Aula 0](../ambiente).

### O arquivo App.js

O arquivo `App.js` é o arquivo principal da aplicação. Ele define o componente raiz da aplicação, que será renderizado pelo React Native. Inicialmente, o arquivo `App.js` é o seguinte:

```javascript
import { StatusBar } from 'expo-status-bar';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
      <StatusBar style="auto" />
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

O código acima define um componente React Native chamado `App`. Esse componente é um componente funcional, que retorna um elemento JSX. O elemento JSX é um elemento React Native que define um elemento `View`. O elemento `View` é um elemento que define uma área retangular na tela. O elemento `View` define o estilo `styles.container`, que é definido no objeto `styles` no final do arquivo. O estilo `styles.container` define que o elemento `View` deve ocupar toda a tela, que deve ter o fundo branco e que deve centralizar os elementos filhos.

O elemento `View` também define dois elementos filhos: um elemento `Text` e um elemento `StatusBar`. O elemento `Text` define um texto na tela. O elemento `StatusBar` define a barra de status do dispositivo.

Para fins de teste, o elemento `Text` foi alterado para o seguinte:

```javascript
      <Text>Bem vindo ao React Native!</Text>
```

Ao salvar o arquivo, o aplicativo será atualizado automaticamente no dispositivo.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Introdução](./ "Voltar")</span> <span>[Componentes &gt;](componentes.html "Próximo")</span></span>