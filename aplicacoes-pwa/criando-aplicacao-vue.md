---
title: 'Criando a aplicação Vue'
permalink: /aplicacoes-pwa/criando-aplicacao-vue
---

# Criando a aplicação VueJS

Para criar a aplicação VueJS, vamos utilizar o Vite. Inicialmente, vamos criar uma pasta chamada `pwa-fakestore` e abri-la no VsCode. Em seguida, no terminal, executaremos o seguinte comando:

```bash
npm init vue@latest .
```

_Note que usamos a opção `.` para criar a aplicação na pasta atual. Caso você não queira criar a aplicação na pasta atual, basta informar o nome da pasta que deseja criar._

O comando anterior irá criar uma aplicação VueJS usando uma ferramenta de scaffolding chamada `create-vue`. Ele apresentará uma série de perguntas para você. Responda conforme a seguir (assumo que o nome da pasta e do projeto são iguais: `pwa-fakestore`):

```bash
✔ Project name: … pwa-fakestore
✔ Add TypeScript? … No
✔ Add JSX Support? … No
✔ Add Vue Router for Single Page Application development? … Yes
✔ Add Pinia for state management? … Yes
✔ Add Vitest for Unit testing? … No
✔ Add Cypress for both Unit and End-to-End testing? … No
✔ Add ESLint for code quality? … Yes
✔ Add Prettier for code formatting? … Yes

Scaffolding project in ./<your-project-name>...
Done.
```

Note que no exemplo anterior, escolhemos não usar o o suporte ao TypeScript e JSX, nem o Vitest e o Cypress. Você pode escolher o que desejar.

Em seguida, basta executar os seguintes comandos:

```bash
npm install
npm run dev
```

O primeiro comando instala as dependências do projeto. O segundo comando executa o servidor de desenvolvimento do VueJS. Em geral, o servidor estará em execução na porta 5173, caso esta esteja livre. Para acessar a aplicação, basta abrir o navegador e acessar a URL `http://localhost:5173`.

```bash
  VITE v3.2.2  ready in 500 ms

  ➜  Local:   http://127.0.0.1:5173/
  ➜  Network: use --host to expose
```

# Recomendações gerais

No decorrer das aulas, sugiro que você mantenha sempre atualizado o seu projeto em um repositorio Git. Isso facilitará a compreensão das alterações realizadas em cada etapa, e também permitirá que você possa voltar a um estado anterior do projeto, caso necessário.

Também, estamos considerando que você já tem a familiaridade com o VueJS, como estudado em outros cursos. As notas de aula do curso de Desenvolvimento Web com VueJS está [aqui](https://eduardo-da-silva.github.io/aula-desenvolvimento-web/)

<span style="display: flex; justify-content: space-between;"><span>[&lt; PWA com Vite e Vuejs](pwa-com-vite-e-vuejs.html 'Voltar')</span> <span>[Configuração do VueJs com PWA &gt;](configuracao-vue-com-pws.html 'Próximo')</span></span>
