---
title: 'Componentes dinâmicos'
description: 'Responsividade usando componentes dinâmicos'
permalink: /componentes-dinamicos/
---

# Índice da aula

1. [Conceitos de responsividade](#componentes-dinâsmicos)
2. [Criando os arquivos de menu superior](criando-arquivos-menu-superior.html)
3. [Editando o HomeView](editando-homeview.html)
4. [Configurando o composable de responsividade](configurando-composable-responsividade.html)
5. [Finalizando o uso dos componentes dinâmicos](finalizando-uso-componentes-dinamicos.html)
6. [Desafio](desafio.html)
7. [Correção do desafio](correcao.html)

# Componentes dinâmicos

Os componentes dinâmicos são uma forma de criar componentes que se adaptam a diferentes tamanhos de tela. Eles são muito úteis para criar layouts responsivos e podem ser usados em conjunto com os composables para criar uma experiência de usuário mais agradável. Para usufruir o máximo possível desse recurso, aplicaremos também o conceito de _lazy loading_, que é uma técnica de carregamento de componentes apenas quando eles são necessários.

A ideia geral é que, ao invés de carregar todos os componentes de uma vez, carregaremos apenas os que são necessários para a tela atual. Buscaremos fazer isso de forma que o usuário não perceba a diferença, mas que o aplicativo seja mais rápido e eficiente.

Nos exemplos a seguir, a fim de fixação do conceito, faremos 5 modelos de menu superior distintos, apenas alterando o título, para que possamos verificar o comportamento do aplicativo em diferentes tamanhos de tela. Depois, sugiro que você crie outros componentes que melhor se adaptem ao seu projeto.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](../ 'Início')</span> <span>[Criando os arquivos de menu supoerior &gt;](criando-arquivos-menu-superior.html 'Próximo')</span></span>
