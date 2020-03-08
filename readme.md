# Introdução

_Esta documentação visa descrever os fluxos necessários para consumo das apis do **LTM CloudLoyalty** por aplicações terceiras._

A documentação apresenta uma ordem lógica, os termos mais técnicos como request, response, etc deverão estar na documentação técnica no [**portal do desenvolvedor.**](https://portal.ltm.digital/)

Porém é necessário um fluxo lógico de acordo com a necessidade do integrador para maior agilidade.
O portal do desenvolvedor apresenta uma lista de chamadas, **aqui apresentamos um mapa lógico disso tudo.**

**LTM CloudLoyalty** é um produto de <a href="https://vertem.com" target="_blank">**LTM Fidelidade.**</a>

**LTM Fidelidade** é uma empresa da holding <a href="https://vertem.com" target="_blank">**Vertem.**</a>

A api do **LTM CloudLoyalty** foi desenvolvida baseada em padrões [**REST**](https://pt.wikipedia.org/wiki/REST), o que garante o mais alto nível de interoperabilidade entre aplicações uma vez que todos os componentes se comunicam através de interfaces HTTP.

# Sumário

- [Primeiros passos com o **CloudLoyalty**](/starting.md)
- [Autenticação](/auth/cognito/readme.md)

  - [Qual versão de integração devo escolher?](/auth/new-or-legacy.md)
  - [Qual fluxo de autenticação OAUTH2 devo escolher?](/auth/flows.md)

  - [Versão 2.0 - Integração de Autenticação](/auth/cognito/readme.md)

    - [OpenId Connect / Single Sign On](/auth/cognito/sso.md)
      - [Discovery Endpoint](/auth/cognito/well-known.md)
        - [Authorization Endpoint](/auth/cognito/well-known.md)
        - [Token Endpoint](/auth/cognito/well-known.md)
        - [UserInfo Endpoint](/auth/cognito/well-known.md)
        - [Logout Endpoint](/auth/cognito/well-known.md)
        - [Issuer e jwks_uri (JWT)](/auth/cognito/well-known.md)
      - [Authorization Code](/auth/cognito/authorization_code.md)
    - [Client Credentials](/auth/cognito/client_credentials.md)
    - Federação _(em breve...)_
    - Mobile _(em breve)_

  - [Versão 1.0 - Integração de Autenticação](/auth/legacy/readme.md)

    - OAuth2 _(em breve...)_
    - Client Credentials _(em breve...)_
    - Authorization Code _(em breve...)_
    - Password Credentials _(em breve...)_

## Participantes

- [Pesquisar um participante - Fluxo Client Credentials](/participant/client_credentials.md)
  - [User Impersonation para Administradores](/participant/user_impersonation.md)
- [Pesquisar um participante - Fluxo Authorization Code (SSO)](/participant/authorization_code.md)
- [Saldo de pontos de um participante](/participant/balance.md)

## Compras / Resgates

- [Qual o modelo de resgates devo adotar?](/purchase/readme.md)
- [Tipos de autenticação](/purchase/auth.md)

- [Compras Internas](/purchase/internal.md)

  - Catálogo de Produtos
    - Vitrines
    - Busca de produtos
    - Preço e disponibilidade
    - Cálculo de frete
      - Produto virtual
      - Produto físico
  - Carrinho de compras
  - Criando uma compra

- [Compras Externas](/purchase/external.md)
  - Authorização de compra
    - Antifraude _(em breve...)_
  - Confirmação de compra
  - Cancelamento de compra
  - Consultar pedidos

## Estorno de pedidos

## Monitoria
