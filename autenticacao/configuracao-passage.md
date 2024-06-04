---
title: 'Configuração do Passage'
description: 'Configuração da plataforma de autenticação Passage'
permalink: /autenticacao/configuracao-passage
---

# Configuração do Passage

Para configurar o Passage, você precisa criar uma conta na plataforma. Acesse o site [https://passage.id/](https://passage.id/) e clique em "Login" e depois em "Registre-se" para criar uma conta. Siga os passos solicitados para criar a conta.

Após criar a conta, você deve criar um aplicativo. Para isso, clique em "Create App". Na sequência, escolha a opção `Passkey complete` e clique no botão `Continue`. Em seguida, escolha a opção `Embedded login experience` e preencha os campos solicitados:

- Name your app: _Fake Store_
- Enter the domain for your app: _http://localhost:5173_
- Enter the redirect URL: _/_

Importante: o domínio e a porta devem ser os mesmos que você está utilizando para desenvolver o seu PWA. No nosso caso, estamos utilizando o domínio `http://localhost:5173`. Quando você for colocar o seu PWA em produção, você deve alterar o domínio para o domínio do seu site.

Clique em `Create App` para finalizar a criação do aplicativo

# Visão geral do aplicativo no Passage

Após criar o aplicativo, você será redirecionado para a página de visão geral do aplicativo. Nesta página, você pode visualizar as informações do aplicativo. Um menu lateral será apresentado, com as seguintes opções:

- **Quick Start**: apresenta um guia rápido para você começar a utilizar o Passage.
- **Dashboard**: apresenta um resumo das informações do aplicativo.
- **Authentication**: permite configurar a autenticação do aplicativo, com configurações de: `Login Settings`, `Registration Fields`, `Session Management` e `Authentication Methods`.
- **Automation**: permite configurar ações automáticas. Neste momento, apenas a opção de `Authorizers`, que são funções Javascript executadas antes de uma ação ser realizada.
- **Native Apps**: permite configurar aplicativos nativos.
- **Users**: permite visualizar os usuários cadastrados no aplicativo.
- **Events**: permite visualizar os eventos gerados no aplicativo.
- **Branding**: permite personalizar a aparência do aplicativo e _templates_ de email, SMS, etc.
- **Settings**: permite configurar as configurações do aplicativo.

# Configuração do aplicativo no Passage

Embora eu aconselhe explorar as opções disponíveis no Passage, vamos focar na configuração da autenticação do aplicativo.

Para isso, clique em `Authentication` no menu lateral. Na aba de `Login Settings`, vamos selecionar as duas opções disponíveis: `Public Signups` e `Profile Management`. A primeira opção vai permitir o auto cadastro de usuários e a segunda opção vai permitir que os usuários editem o seu perfil.

Não faremos alteração nas abas `Registration Fields` e `Session Management`. Por fim, na aba `Authentication Methods`, vamos selecionar a opção `Identify Verification Required`. Esta opção vai exigir que o usuário faça a verificação de identidade antes de acessar o aplicativo. Deixaremos apenas a opção `Email` selecionada em `Username Types Supported`. Deixaremos habilitadas as opções `Passkeys` e `SMS and Email logins`.

Por fim, na opção `Social Connections`, podemos habilitar as três opções: `Google`, `Github` e `Apple`. Configurações adicionais de OAuth são recomendadas nesta etapa, mas que não faremos neste exemplo.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. 'Voltar')</span> <span>[Configuração do Login no Vue &gt;](configuracao-no-vue.html 'Próximo')</span></span>
