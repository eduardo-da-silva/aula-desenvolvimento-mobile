---
title: 'Ajustes finos na organização do layout'
permalink: /loja-virtual/layout-grid
---

# Ajustes finos no layout para telas grandes

Vamos fazer alguns ajustes finos no layout da aplicação para telas grandes. Para isso, vamos adicionar uma grade de layout e ajustar o espaçamento entre os elementos. Abra o arquivo `src/layouts/LayoutLarge.vue` e adicione o seguinte conteúdo depois do bloco de `template`:

```vue
<style scoped>
#layout-large {
  display: grid;
  grid-template-columns: 1fr 5fr;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    'aside header'
    'aside main'
    'aside footer';
  min-height: 100vh;
}

header {
  display: flex;
  widows: 100vw;
  justify-content: flex-end;
  padding: 1.5rem;
  grid-area: header;
}

aside {
  border-right: #eeeeee 1px solid;
  box-shadow: 0 0 10px 0 #eeeeee;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 1.5rem;
  padding-bottom: 1.5rem;
  grid-area: aside;
}

main {
  min-height: 80%;
  padding: 2rem;
  grid-area: main;
}

footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 3rem;
  background-color: #eeeeee;
  grid-area: footer;
}
</style>
```

Neste arquivo, estamos definindo um layout de grade com quatro áreas: `header`, `aside`, `main` e `footer`. Estamos ajustando o espaçamento entre os elementos e definindo a altura mínima da aplicação.

# Ajustes finos no layout para telas médias

Agora, vamos fazer alguns ajustes finos no layout da aplicação para telas médias. Para isso, vamos adicionar uma grade de layout e ajustar o espaçamento entre os elementos. Abra o arquivo `src/layouts/LayoutMedium.vue` e adicione o seguinte conteúdo depois do bloco de `template`:

```vue
<style scoped>
#layout-medium {
  display: grid;
  grid-template-columns: 1fr 6fr;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    'aside header'
    'aside main'
    'aside footer';
  min-height: 100vh;
}

header {
  display: flex;
  widows: 100vw;
  justify-content: flex-end;
  padding: 1.5rem;
  grid-area: header;
}

aside {
  border-right: #eeeeee 1px solid;
  box-shadow: 0 0 10px 0 #eeeeee;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 1.5rem;
  padding-bottom: 1.5rem;
  grid-area: aside;
}

main {
  min-height: 80%;
  padding: 2rem;
  grid-area: main;
}

footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 3rem;
  background-color: #eeeeee;
  grid-area: footer;
}
</style>
```

Neste arquivo, estamos definindo um layout de grade com quatro áreas: `header`, `aside`, `main` e `footer`. Estamos ajustando o espaçamento entre os elementos e definindo a altura mínima da aplicação.

# Ajustes finos no layout para telas pequenas

Agora, vamos fazer alguns ajustes finos no layout da aplicação para telas pequenas. Para isso, vamos adicionar uma grade de layout e ajustar o espaçamento entre os elementos. Abra o arquivo `src/layouts/LayoutSmall.vue` e adicione o seguinte conteúdo depois do bloco de `template`:

```vue
<style scoped>
#layout-small {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

header {
  display: flex;
  justify-content: space-between;
  padding: 1.5rem;
  border-bottom: #eeeeee 2px solid;
  background-color: white;

  z-index: 10;
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 5%;
}

main {
  margin-top: 5%;
  margin-bottom: 4rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  padding-bottom: 4rem;
  padding-top: 1.5rem;
  position: relative;
}

footer {
  border-top: #eeeeee 1px solid;
  box-shadow: 0 0 10px 0 #eeeeee;
  padding: 1.5rem;
  margin-top: auto;
  background-color: white;

  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  color: white;
  text-align: center;
  z-index: 10;
}
</style>
```

Neste arquivo, estamos definindo um layout de grade com três áreas: `header`, `main` e `footer`. Estamos ajustando o espaçamento entre os elementos e definindo a altura mínima da aplicação.

<span style="display: flex; justify-content: space-between;"><span>[&lt; A organização do layout](layout.html 'Voltar')</span><span>[Listagem de produtos &gt;](listagem-produtos.html 'Próximo')</span></span>
