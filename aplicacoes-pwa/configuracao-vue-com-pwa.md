---
title: 'Criando a aplicação Vue'
permalink: /aplicacoes-pwa/configuracao-vue-com-pwa
---

# Instalação dos pré-requisitos

Uma vez que a aplicação VueJS já está criada, vamos instalar os pré-requisitos para que ela se torne um PWA. Para isso, vamos instalar o `vite-plugin-pwa` e o `workbox-precaching`:

```bash
npm install vite-plugin-pwa workbox-precaching
```

O pacote `vite-plugin-pwa` é um _plugin_ para o Vite que facilita a criação de PWAs. Ele é responsável por gerar o _Service Worker_ e o _manifest_ da aplicação. O pacote `workbox-precaching` é uma biblioteca que permite a criação de _Service Workers_ para aplicações web, sendo que ele procura por arquivos estáticos e os armazena em _cache_, remove arquivos antigos e atualiza arquivos novos, além de evitar a duplicação de arquivos.

# Geração dos ícones

Para que a aplicação se torne um PWA, é necessário que ela tenha ícones para a tela inicial. Para isso, sugiro que você crie alguma logo para a aplicação, e o salve na pasta `public` com o nome `logo.png`. Em seguida, acesse o site `https://www.pwabuilder.com/imageGenerator`. Neste site, você escolherá o arquivo `logo.png` e o site irá gerar os ícones necessários para a aplicação. Em seguida, basta baixar o arquivo gerado e descompactá-lo.

Nós não utilizaremos todos os arquivos gerados, mas apenas os arquivos `android/android-launchericon-192x192.png` e `android/android-launchericon-512x512.png`. Esses arquivos devem ser salvos na pasta `public` da aplicação, com os nomes `pwa-192x192.png` e `pwa-512x512.png`, respectivamente.

Também usaremos o arquivo `ios/180.png` que será salvo na pasta `public` com o nome `apple-touch-icon.png`.

_Obs: Você pode gerar esses arquivos com outros utilitários, como o `pwa-asset-generator`, bem como fazer uso de outros arquivos para a sua aplicação. Estamos aqui com uma configuração mínima_

# Ajustes no arquivo de configuração do Vite

Agora, vamos ajustar o arquivo de configuração do Vite, que é o arquivo `vite.config.js`. Abra este arquivo e adicione o seguinte conteúdo:

```javascript
import { fileURLToPath, URL } from 'node:url';

import { defineConfig } from 'vite';
import vue from '@vitejs/plugin-vue';
import { VitePWA } from 'vite-plugin-pwa';

export default defineConfig({
  plugins: [
    vue(),
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
- `icons`: Os ícones da aplicação.

# Ajustes no arquivo index

Agora, vamos ajustar o arquivo `index.html`. Abra este arquivo e adicione a seguinte `tag` no bloco `head` conteúdo:

```html
<link rel="apple-touch-icon" href="/apple-touch-icon.png" sizes="180x180" />
<meta name="theme-color" content="#ffffff" />
```

Neste arquivo, você também pode alterar a `tag` `title` para o nome da aplicação, e a `tag` `meta` `description` para a descrição da aplicação. Você também poderia adicionar uma fonte personalizada, ou mesmo alterar o estilo da aplicação.

<!-- # Componente de instalação

Agora, vamos criar um componente que será exibido quando a aplicação for instalada. Para isso, crie um arquivo chamado `InstallApp.vue` na pasta `src/components` com o seguinte conteúdo:

```html
<script setup>
  import { useRegisterSW } from 'virtual:pwa-register/vue';
  const { isUpdateAvailable, updateServiceWorker } = useRegisterSW();

  const update = async () => {
    await updateServiceWorker();
    window.location.reload();
  };
</script>

<template>
  <div v-if="isUpdateAvailable" class="install-app">
    <button @click="update">Atualizar aplicação</button>
  </div>
</template>
```

Neste arquivo, estamos importando o `useRegisterSW` do `virtual:pwa-register/vue`. Este _hook_ nos permite verificar se há uma atualização disponível, e atualizar o _Service Worker_ quando houver. Também estamos verificando se há uma atualização disponível, e se houver, exibimos um botão para atualizar a aplicação. -->

<!-- # Registro do componente de instalação

Agora, vamos registrar o componente de instalação na aplicação. Para isso, abra o arquivo `App.vue` e adicione o seguinte conteúdo:

```html
<script setup>
  import InstallApp from './components/InstallApp.vue';
  ...
</script>
<template>
  <InstallApp />
  ...
</template>
```

_Note que estamos apenas editando o arquivo com algumas inserções._ -->

# Testando a aplicação

Agora, basta executar o comando `npm run dev` e acessar a aplicação no navegador. Você verá que a aplicação será instalada, e que o componente de instalação será exibido. Se você atualizar a aplicação, verá que o _Service Worker_ será atualizado, e que a aplicação será recarregada.

Também, se você acessar a aplicação no navegador, e clicar no botão de instalação, verá que a aplicação será instalada na tela inicial do dispositivo.

Mais adiante, vamos publicar essa aplicação e gerar um pacote para instalação em dispositivos móveis.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Criando a aplicação Vue](criando-aplicacao-vue.html 'Voltar')</span> <span>[Deploy da aplicação &gt;](deploy-da-aplicacao.html 'Próximo')</span></span>
