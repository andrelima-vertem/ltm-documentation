# Introdução

_Esta documentação visa descrever os fluxos necessários para consumo das apis do **LTM CloudLoyalty** por aplicações terceiras._

**LTM CloudLoyalty** é um produto de <a href="https://vertem.com" target="_blank">**LTM Fidelidade.**</a>

**LTM Fidelidade** é uma empresa da holding <a href="https://vertem.com" target="_blank">**Vertem.**</a>

A api do **LTM CloudLoyalty** foi desenvolvida baseada em padrões [**REST**](https://pt.wikipedia.org/wiki/REST), o que garante o mais alto nível de interoperabilidade entre aplicações uma vez que todos os componentes se comunicam através de interfaces HTTP.

# Sumário

- [Primeiros passos com o **CloudLoyalty**](/starting.md)
- [Autenticação](/auth/cognito/readme.md)

  - [Nova Integração de Autenticação (Single Sign On)](/auth/cognito/readme.md)

    - [OpenId Connect / Single Sign On](/auth/cognito/sso.md)
      - [Discovery Endpoint](/auth/cognito/well-known.md)
      - [Authorization Code](/auth/cognito/authorization_code.md)
    - [Client Credentials](/auth/cognito/client_credentials.md)
    - Federação _(em breve...)_

  - [Integração Antiga de Autenticação](/auth/legacy/readme.md)

    - OAuth2 _(em breve...)_
    - CLient Credentials _(em breve...)_
    - Authorization Code _(em breve...)_
    - Password Credentials _(em breve...)_

  - [Qual tipo de integração de autenticação devo escolher?](/auth/new-or-legacy.md)
  - [Qual fluxo de autenticação OAUTH2 devo escolher?](/auth/flows.md)

- Participante
  - Fluxo Client Credentials
  - Fluxo Authorization Code (SSO)
  - Saldo de pontos

## Compras Internas

- Tipos de autenticação
- Catálogo de Produtos
  - Vitrines
  - Busca de produtos
  - Preço e disponibilidade
  - Cálculo de frete
    - Produto virtual
    - Produto físico
- Carrinho de compras
- Criando uma compra

## Compras Externas

- Tipos de autenticação
- Authorização de compra
  - Antifraude _(em breve...)_
- Confirmação de compra
- Cancelamento de compra
- Consultar pedidos

## Estorno de pedidos

## Monitoria
