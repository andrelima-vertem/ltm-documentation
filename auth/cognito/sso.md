[Início](/readme.md) &raquo; Autenticação &raquo; [Nova Integração de Autenticação](/auth/cognito/readme.md) &raquo; OpenId Connect / SSO

# Introdução

O objetivo deste documento é descrever resumidamente as responsabilidades doSingle Sign On, OpenId Connect, e OAUTH2 dentro do ecosistema CloudLoayalty

![Cognito / OpenId Connect](/images/sso-amazon.png)

## Single Sign On (SSO)

https://en.wikipedia.org/wiki/Single_sign-on

Iniciar uma sessão de **SSO** agora deve acontecer apenas em uma página hospedada pelo Identity Server LTM e não em aplicativos.

Isso significa que, para que o SSO funcione, você deve estar usando o **CloudLoyalty Identity Server** com login universal.

Para cenário de federação, o Identity Provider de destino deverá ser integrado ao CloudLoyalty Identity Server.

Os usuários devem ser redirecionados para a página de login e redirecionados para o seu aplicativo assim que a autenticação for concluída.

### Links úteis:

https://tools.ietf.org/html/rfc6749

https://oauth.net/2/
