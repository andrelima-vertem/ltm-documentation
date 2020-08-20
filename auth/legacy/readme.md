[Início](/readme.md) &raquo; Autenticação &raquo; Integração Antiga de Autenticação

# Autenticação - Versão 1.0

A autenticação antiga do Cloud Loyalty possui algumas limitações no que diz respeito à integrações com aplicações externas.

Apesar de ser compatível com [OAUTH2](https://oauth.net/2/), o papel do **authorizarion provider** não está presente por questões estratégicas no momento em que foi concebido.

Isso trazia algumas limitações para as aplicações cliente.

Em um fluxo de autenticação de um participante (usuário) é necessário a intervenção do time técnico da LTM Fidelidade.
Isso gerá uma efetividade menor e torna o processo um pouco mais burocrático.

Além do mais qualquer nova integração precisa sempre de uma camada middleware para orquestração.

## Fluxos permitidos

- Authorization Code
- Client Credentials
- Password Credentials
- [Refresh Token](refresh_token.md)

### Links úteis:

https://tools.ietf.org/html/rfc6749

https://oauth.net/2/

#

## Próximos passos

[Qual tipo de integração de autenticação devo escolher &raquo;](/auth/new-or-legacy.md)
