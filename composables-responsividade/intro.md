---
title: 'O conceito de composables aplicados em responsividade '
description: 'Aplicando o conceito de composables em responsividade'
permalink: /composables-responsividade/
---

# Índice da aula

1. [Conceitos de responsividade](#conceitos-de-responsividade)
2. [Criando o primeiro composable](criando-um-composable.html)
3. [Uso nos componentes](uso-nos-componentes.html)
4. [Desafio](desafio.html)
5. [Correção do desafio](correcao.html)

# Conceitos de responsividade

A responsividade é uma técnica que permite que o layout de um site se adapte a diferentes tamanhos de tela. Isso é importante para que o site seja acessível em diferentes dispositivos, como celulares, tablets, notebooks e desktops. A responsividade é uma prática comum no desenvolvimento web e é essencial para garantir uma boa experiência do usuário.

Vimos nos módulos anteriores como criar um menu superior responsivo, aplicando algumas técnicas de CSS. Agora, vamos aprimorar a responsividade do nosso site, criando _composables_ que nos ajudarão a lidar com a responsividade de forma mais eficiente.

# Composables

Os _composables_ são funções que encapsulam lógicas e comportamentos específicos, permitindo que eles sejam reutilizados em diferentes partes da aplicação. Eles são uma forma de organizar e compartilhar lógicas entre componentes, tornando o código mais limpo e fácil de manter. São compátiveis com a API de composição do Vue.

A tarefa de reutilizar lógicas é uma prática comum no desenvolvimento de aplicações frontend. Por exemplo, podemos precisar formatar datas em muitos lugares, então extraímos uma função reutilizável para isso. Essa função de formatação encapsula a lógica sem estado: ela recebe uma entrada e retorna imediatamente a saída esperada.

Por outro lado, a lógica com estado envolve gerenciar o estado que muda ao longo do tempo. Um exemplo simples seria rastrear a posição atual do mouse em uma página. Em cenários do mundo real, também poderia ser uma lógica mais complexa, como gestos de toque ou status de conexão com um banco de dados.

No contexto de responsividade, podemos criar _composables_ que encapsulam lógicas de _layout_, como a definição de _breakpoints_, a verificação do tamanho da tela e a aplicação de estilos condicionais. Isso nos permite criar _layouts_ responsivos de forma mais eficiente e organizada.

Nos exemplos que iremos desenvolver, em que adicionaremos um _eventListener_ sempre que a tela for redimensionada, vamos encapsular essa lógica em um _composable_ para que possamos reutilizá-la em diferentes partes da aplicação.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](../ 'Início')</span> <span>[Criando o primeiro composable &gt;](criando-um-composable.html 'Próximo')</span></span>
