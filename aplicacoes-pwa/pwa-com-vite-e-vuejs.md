---
title: 'PWA com Vite e VueJS'
permalink: /aplicacoes-pwa/pwa-com-vite-e-vuejs
---

# PWA com Vite e VueJS

O Vite é um _build tool_ para aplicações web modernas. Ele é rápido, fácil de configurar e possui um _hot reload_ instantâneo. O Vite é uma ferramenta de desenvolvimento que visa otimizar a experiência do desenvolvedor, permitindo que o desenvolvimento seja mais rápido e eficiente. Além disso, o Vite é uma ferramenta moderna, que utiliza tecnologias modernas, como o _ES6 Modules_ e o _Service Worker_.

Já estamos familiarizados com o VueJS, um _framework_ progressivo para a construção de interfaces de usuário. O VueJS é uma ferramenta que permite a criação de interfaces de usuário interativas e dinâmicas, com a utilização de componentes reutilizáveis. Também, desde o lançamento da versão 3, é comum o uso do VueJS integrado com o Vite.

Para a criação de um PWA, vamos desenvolver uma aplicação web com VueJS e Vite. A aplicação utilizará a API REST pública https://fakestoreapi.com/. Nesta aplicação será possível visualizar uma lista de produtos, visualizar detalhes de um produto, gerenciar produtos em um carrinho.

Tal aplicação será desenvolvida em etapas, com a utilização de _commits_ para registrar as alterações realizadas. A cada etapa, será possível acompanhar o desenvolvimento da aplicação, com a visualização das alterações realizadas.

Como já temos uma certa familiaridade com o VueJS, é importante ressaltar quais são as principais configurações que são feitos em uma aplicação comum para que ela se torne um PWA. A seguir, vamos listar as principais configurações que são feitas em uma aplicação comum para que ela se torne um PWA:

1. **Service Worker**: O _Service Worker_ é um _script_ que é executado pelo navegador em _background_. Ele é responsável por interceptar requisições de rede e armazenar em _cache_ os recursos da aplicação. Dessa forma, é possível que a aplicação funcione offline, e que os recursos sejam carregados mais rapidamente.

2. **Manifest**: O _manifest_ é um arquivo que contém informações sobre a aplicação, como o nome, a descrição, o ícone, as cores, e a orientação. Esse arquivo é utilizado pelo navegador para exibir a aplicação de forma mais agradável, como se fosse um aplicativo nativo.

3. **HTTPS**: PWAs devem ser servidas via HTTPS, para garantir a segurança e a autenticidade dos recursos.

4. **Ícones**: PWAs devem ter ícones para a tela inicial, para que os usuários possam acessar a aplicação de forma mais rápida e fácil.

Também, vamos hospedar a aplicação em um servidor, para que ela possa ser acessada de qualquer lugar. Para isso, vamos utilizar os serviços de plataforma da Vercel, que permitem a hospedagem de aplicações web de forma gratuita e fácil.

Nestas primeiras aulas, vamos criar uma aplicação padrão VueJS, sem modificações para que ela se torne um PWA. Nas próximas aulas, vamos adicionar as configurações necessárias para que a aplicação se torne um PWA.

<span style="display: flex; justify-content: space-between;"><span>[&lt; O conceito de PWA](. 'Voltar')</span> <span>[Criando uma primeira aplicação PWA &gt;](criando-aplicacao-pwa.html 'Próximo')</span></span>
