---
title: 'Desafio'
description: 'Desafio para aplicar o composable de responsividade nos componentes Vue'
permalink: /composables-responsividade/desafio
---

# Desafio

Considerando o exemplo que estamos desenvolvendo para a loja de produtos, sugiro como desafio:

- aplicar o composable `useScreen` no componente `ListagemProdutos.vue` para verificar o tamanho da tela e aplicar estilos condicionais.
- adicionar uma classe condicional ao elemento `ul` que contém a lista de produtos. Se a tela for menor que 768 pixels, adicione a classe `mobile` ao elemento `ul`.
- criar um componente para rodapé da página com informações sobre a loja e apresentar apenas em telas que não são móveis (menores que 768 pixels).
- criar um outro componente, estilo um barButton, para apresentar apenas em telas móveis (menores que 768 pixels). Esse componente deve conter quatro botões: Home, Carrinho, Usuário e Sobre. Esses botões devem ser apresentados em uma linha, com o texto abaixo do ícone.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Uso do composable nos componentes](uso-nos-componentes.html 'Voltar')</span> <span>[Correção do desafio &gt;](correcao.html 'Próximo')</span></span>
