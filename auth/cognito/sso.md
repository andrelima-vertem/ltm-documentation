[Início](/readme.md) &raquo; Autenticação &raquo; [Versão 2.0 - Integração de Autenticação](/auth/cognito/readme.md) &raquo; OpenId Connect / SSO

# Introdução

O objetivo deste documento é descrever resumidamente as responsabilidades do Single Sign On, OpenId Connect e OAUTH2 dentro do ecosistema CloudLoyalty

![Cognito / OpenId Connect](/images/sso-amazon.png)

## Single Sign On (SSO)

https://en.wikipedia.org/wiki/Single_sign-on

Iniciar uma sessão de **SSO** agora deve acontecer apenas em uma página hospedada pelo **CloudLoyalty Identity Server** e não em aplicativos.

Isso significa que, para que o SSO funcione, você deve estar usando o **CloudLoyalty Identity Server** com login universal.

Para cenário de federação, o Identity Provider de destino deverá ser integrado ao CloudLoyalty Identity Server.

Os usuários devem ser redirecionados para a página de login e redirecionados para o seu aplicativo assim que a autenticação for concluída.

> Importante: **O Fluxo padrão para SSO** definido pela LTM Fidelidade é o **Authorization Code.**

## OpenId Connect

O OpenID Connect **(OIDC)** é um protocolo de autenticação, baseado na família de especificações **OAuth 2.0.**

Ele usa **JSON Web Tokens (JWT)** simples, que você pode obter usando fluxos em conformidade com as especificações do OAuth 2.0.

O CloudLoyalty Identity Server gera JSON Web Tokens (JWT).

### Links úteis:

https://openid.net/developers/specs/

https://jwt.io

## OAUTH 2

### Estrutura de autorização do OAuth 2.0

O OAuth 2.0 é um protocolo que permite que um usuário conceda acesso limitado a seus recursos em um site, em outro site, sem precisar expor suas credenciais.

### Papéis do OAuth

Em qualquer fluxo do OAuth 2.0, podemos identificar os seguintes papéis:

- **Proprietário do recurso (Resource Owner):** a entidade que pode conceder acesso a um recurso
  protegido (APIs do Webpremios Marketplace). Normalmente, este é o usuário final.

- **Servidor de Recursos (Resource Server):** o servidor que hospeda os recursos protegidos. Esta
  é a API do Webpremios Marketplace.

- **Cliente (Client):** o aplicativo (YourApp / Ragnarok) solicitando acesso a um recurso protegido em nome do Resource Owner.

- **Servidor de Autorização (Authorization Server):** o servidor que autentica o Resource Owner e emite Tokens de Acesso depois de obter a devida autorização. Nesse caso, o LTM Identity Server.

### Links úteis:

https://tools.ietf.org/html/rfc6749

https://oauth.net/2/

## Próximos passos

[Discovery Endpoint](/auth/cognito/well-known.md)
