---
title: 'Deploy da aplicação'
permalink: /aplicacoes-pwa/deploy-aplicacao
---

# Deploy da aplicação

Agora que a aplicação está pronta, vamos publicá-la. Usaremos o [Vercel](https://vercel.com/) para publicar a aplicação, mas você pode usar qualquer outro serviço de hospedagem. Para o uso do Vercel, é necessário que o seu projeto esteja hospedado em uma plataforma no github.

Para iniciar o processo de deploy, acesse o site do Vercel e clique em "Log in" para fazer o login. Caso você ainda não tenha uma conta, basta criá-la. Eu sugiro criar uma conta associada com a conta do GitHub. Em seguida, clique em "Add New" - "Project". Na tela seguinte, faça a integração com o GitHub e escolha o repositório que você deseja publicar. Em seguida, clique em "Deploy".

Se o seu projeto estiver configurado corretamente, o Vercel irá fazer o deploy da aplicação e disponibilizará um link para acesso. Caso você tenha feito alguma configuração errada, o Vercel irá informar o erro e você poderá corrigi-lo.

Agora, acesse o link fornecido pelo Vercel e veja a sua aplicação rodando. Se tudo estiver correto, a aplicação estará disponível para acesso.

# Construção do APK

Para que a aplicação seja instalada em dispositivos móveis, é necessário que ela seja empacotada em um arquivo APK. Para isso, utilizaremos a plataforma PWABuilder. Acesse o site [https://www.pwabuilder.com/](https://www.pwabuilder.com/), preencha o campo com o endereço da PWA publicada e clique em "Start" para iniciar o processo.

A tela seguinte apresentará um resumo da aplicação com informações sobre o ícone, o nome, a descrição, etc. Também serão descritas algumas `Action Items`, que são ações que você pode realizar para melhorar a experiência do usuário. Outras informações estão disponíveis nesta tela, que sugiro que você leia com atenção.

Para dar continuidade clique em `Package for Stores`. Em seguida, selecione o `Android` e clique em `Generate Package`. Na tela que será apresentada, clique em `Download Package`. O arquivo gerado será um arquivo `.zip` que contém, entre outros, um arquivo `.apk` para ser instalado em ambientes Android..

Ao longo das aulas outras formas de publicação de aplicativos serão apresentadas, bem como algumas dicas para melhorar a experiência do usuário.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Configuração do VueJs com PWA](configuracao-vue-com-pwa.html 'Voltar')</span> <span>[Sumário &gt;](../ 'Próximo')</span></span>
