---
title: 'O projeto da loja virtual - tutorial'
description: 'Entendendo o projeto'
permalink: /loja-virtual/
---

# Índice da aula

1. [Entendendo o projeto](#entendendo-o-projeto)
2. [Organização do Layout](layout.html)

# Entendendo o projeto

O projeto da loja virtual é um projeto que visa aplicar os conceitos aprendidos nas aulas anteriores. Nele, vamos criar uma loja virtual simples, com listagem de produtos, detalhes do produto, carrinho de compras e finalização de compra. Também teremos um painel administrativo para gerenciar os produtos.

O projeto será dividido em várias partes, cada uma com um objetivo específico. A ideia é que você consiga entender como cada parte do projeto se relaciona com as outras e como elas se encaixam para formar a aplicação final.

Usaremos como base um protótipo desenvolvido pela estudante Giulia Nobre. O protótipo pode ser acessado [aqui](https://www.figma.com/file/6mbTzRwIf3ELdp5Q4N3JPt/FakeStore?type=design&node-id=101-344&mode=design&t=TRGpDnAUpGg76p1i-0). Ao longo do projeto, vamos adaptar o protótipo para a nossa aplicação, mas a ideia é manter a estrutura e o design propostos por ela.

# Criando o projeto da loja virtual

Para criar o projeto da loja virtual, vamos utilizar o Vite.

1. Crie uma nova pasta chamada `loja-virtual` e abra-a no VsCode.
2. No terminal, execute o seguinte comando:

```bash
npm init vue@latest .
```

Note que usamos a opção `.` para criar a aplicação na pasta atual. Caso você não queira criar a aplicação na pasta atual, basta informar o nome da pasta que deseja criar.

O comando anterior irá criar uma aplicação VueJS usando uma ferramenta de scaffolding chamada `create-vue`. Ele apresentará uma série de perguntas para você. Responda conforme a seguir (assumo que o nome da pasta e do projeto são iguais: `loja-virtual`):

```bash
✔ Project name: … loja-virtual
✔ Add TypeScript? … No
✔ Add JSX Support? … No
✔ Add Vue Router for Single Page Application development? … Yes
✔ Add Pinia for state management? … Yes
✔ Add Vitest for Unit testing? … No
✔ Add Cypress for both Unit and End-to-End testing? … No
✔ Add ESLint for code quality? … Yes
✔ Add Prettier for code formatting? … Yes
✔ Add Vue DevTools 7 extension for debugging? … Yes
```

Note que no exemplo anterior, escolhemos não usar o o suporte ao TypeScript e JSX, nem o Vitest e o Cypress.

Em seguida, já faremos as instalações necessárias, como estudadas nas aulas anteriores, para suportar aplicações PWA.

```bash
npm install vite-plugin-pwa workbox-precaching axios
```

Já estudamos a instalação do `vite-plugin-pwa` e do `workbox-precaching`. O `axios`, também já conhecido, é uma biblioteca que facilita a realização de requisições HTTP.

Em seguida, é necessário gerar os ícones para a aplicação. Para isso, sugiro que você crie alguma logo para a aplicação, e o salve na pasta `src/assets` com o nome `logo.png`. Em seguida, acesse o site `https://www.pwabuilder.com/imageGenerator`. Neste site, você escolherá o arquivo `logo.png` e o site irá gerar os ícones necessários para a aplicação. Lembre que você deve adicionar os ícones gerados na pasta `public` da aplicação.

Lembre que ao descompactar os arquivos gerados, você não utilizará todos eles. Nesse momento, usaremos apenas três arquivos:

- `android/android-launchericon-192x192.png` que será gravado na pasta `public` com o nome `pwa-192x192.png`.
- `android/android-launchericon-512x512.png` que será gravado na pasta `public` com o nome `pwa-512x512.png`.
- `ios/180.png` que será gravado na pasta `public` com o nome `apple-touch-icon.png`.

Também sugiro que você grave na pasta `public` o arquivo `logo.png` que você gerou.

Deixo abaixo os links para os arquivos que eu gerei:
_IMPORTANTE_: Você só precisa dos arquivos que eu gerei se você não quiser gerar os seus próprios arquivos, como sugerido acima.

- Arquivo `pwa-192x192.png`: [pwa-192x192.png](../assets/pwa-192x192.png)
- Arquivo `pwa-512x512.png`: [pwa-512x512.png](../assets/pwa-512x512.png)
- Arquivo `apple-touch-icon.png`: [apple-touch-icon.png](../assets/apple-touch-icon.png)
- Arquivo `logo.png`: [logo.png](../assets/logo.png)

Você pode baixar esses arquivos e gravá-los na pasta `public` do seu projeto. Lembre que o arquivo `logo.png` também deve estar na pasta `src/assets`.

# Ajustes no arquivo de configuração do Vite

Agora, vamos ajustar o arquivo de configuração do Vite, que é o arquivo `vite.config.js`. Abra este arquivo e adicione o seguinte conteúdo:

```javascript
import { fileURLToPath, URL } from 'node:url';

import { defineConfig } from 'vite';
import vue from '@vitejs/plugin-vue';
import VueDevTools from 'vite-plugin-vue-devtools';
import { VitePWA } from 'vite-plugin-pwa';

export default defineConfig({
  plugins: [
    vue(),
    VueDevTools(),
    VitePWA({
      registerType: 'autoUpdate',
      includeAssets: ['favicon.svg', 'apple-touch-icon.png', 'masked-icon.svg'],
      manifest: {
        name: 'Fake Store',
        short_name: 'FakeStore',
        description: 'Fake Store: Fantástica loja de produtos',
        theme_color: '#ffffff',
        icons: [
          {
            src: 'pwa-192x192.png',
            sizes: '192x192',
            type: 'image/png',
            purpose: 'any',
          },
          {
            src: 'pwa-512x512.png',
            sizes: '512x512',
            type: 'image/png',
            purpose: 'maskable',
          },
        ],
        id: 'com.fake-store.app',
        orientation: 'any',
        background_color: '#ffffff',
        start_url: '.',
        launch_handler: {
          client_mode: ['navigate-existing', 'auto'],
        },
      },
      devOptions: {
        enabled: true,
      },
    }),
  ],
  resolve: {
    alias: {
      '@': fileURLToPath(new URL('./src', import.meta.url)),
    },
  },
});
```

Neste arquivo, estamos importando o `VitePWA` e adicionando-o como _plugin_ do Vite. Também estamos configurando o _Service Worker_ para que ele seja atualizado automaticamente, e estamos configurando o _manifest_ da aplicação. Alguns itens que podem ser configurados no _manifest_ são:

- `name`: O nome da aplicação.
- `short_name`: O nome curto da aplicação.
- `description`: A descrição da aplicação.
- `theme_color`: A cor do tema da aplicação.

# Ajustes no arquivo index.html

Agora, vamos ajustar o arquivo `index.html` que está na pasta `public`. Abra este arquivo e adicione o seguinte conteúdo, dentro da tag `head`:

```html
<link rel="apple-touch-icon" href="/apple-touch-icon.png" sizes="180x180" />
<meta name="theme-color" content="#ffffff" />
<title>Fake Store</title>
```

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](../ 'Início')</span> <span>[A organização do layout &gt;](layout.html 'Próximo')</span></span>
