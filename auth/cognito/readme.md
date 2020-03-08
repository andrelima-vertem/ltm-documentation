[Início](/readme.md) &raquo; Autenticação &raquo; Versão 2.0 - Integração de Autenticação

# Autenticação - Versão 2.0

Com o objetivo de separar melhor as responsabilidades (Separation of Concerns) das aplicações do CloudLoyalty, em 2019 a LTM Fidelidade investiu esforços em obter uma solução de **Identity Server.**

Esse Identity Server é uma solução **Amazon Cognito.**

## Amazon Cognito

O Amazon Cognito permite adicionar cadastramento, login e controle de acesso de usuários a aplicativos web e móveis com rapidez e facilidade. O Amazon Cognito escala até milhões de usuários e oferece suporte a login com provedores de identidade social como Facebook, Google e Amazon, além de provedores de identidade empresariais.

### Diretório de usuários seguro e escalável

Os grupos de usuários do Amazon Cognito oferecem um diretório de usuários seguro que escala até centenas de milhões de usuários. Como um serviço totalmente gerenciado, os grupos de usuários podem ser configurados facilmente, sem preocupações com a disponibilização de infraestrutura de servidores.

### Autenticação baseada em padrões

Os grupos de usuários do Amazon Cognito são provedores de identidade baseados em padrões e oferecem suporte a padrões de gerenciamento de identidade e acesso, como Oauth 2.0, SAML 2.0 e OpenID Connect.

> Saiba mais em [https://aws.amazon.com/pt/cognito/](https://aws.amazon.com/pt/cognito/)

### Estratégia

Os clientes LTM Fidelidade podem utilizar o Single Sign On para integrar multiplas aplicações ou gerenciar seu próprio servidor de identidade através de federação.

A divisão das responsabilidades agora é melhor definida pois há bem menos complexidade.

## Próximos passos

[OpenId Connect / Single Sign On](/auth/cognito/sso.md)
