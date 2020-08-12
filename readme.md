# Introdução

_Esta documentação visa descrever os fluxos necessários para consumo das apis do **LTM CloudLoyalty** por aplicações terceiras._

A documentação apresenta uma ordem lógica, os termos mais técnicos como request, response, etc deverão estar na documentação técnica no [**portal do desenvolvedor.**](https://portal.ltm.digital/)

Porém é necessário um fluxo lógico de acordo com a necessidade do integrador para maior agilidade.
O portal do desenvolvedor apresenta uma lista de chamadas, **aqui apresentamos um mapa lógico disso tudo.**

**LTM CloudLoyalty** é um produto de <a href="https://vertem.com" target="_blank">**LTM Fidelidade.**</a>

**LTM Fidelidade** é uma empresa da holding <a href="https://vertem.com" target="_blank">**Vertem.**</a>

A api do **LTM CloudLoyalty** foi desenvolvida baseada em padrões [**REST**](https://pt.wikipedia.org/wiki/REST), o que garante o mais alto nível de interoperabilidade entre aplicações uma vez que todos os componentes se comunicam através de interfaces HTTP.

# Sumário

## Início

- Primeiros passos com uma campanha de fidelidade _(em breve...)_
- [Primeiros passos com o **CloudLoyalty**](/starting.md)

## Segurança

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

## Dicas e boas práticas

- [Dicas de utilização das apis do CloudLoyalty](/tips/readme.md)

## Campanha _(em breve)_

## Participante

- [O que é um participante](/participant/readme.md)

- [Pesquisar um participante - Fluxo Client Credentials](/participant/client_credentials.md)
  - [User Impersonation para Administradores](/participant/user_impersonation.md)
- [Pesquisar um participante - Fluxo Authorization Code (SSO)](/participant/authorization_code.md)
- [Saldo de pontos de um participante](/participant/balance.md)

## Compra / Resgate

- [Modelo de resgates e qual devo adotar](/purchase/readme.md)
- [Tipos de autenticação](/purchase/auth.md)

- [Compra com carrinho](/purchase/internal.md)

  - Catálogo de Produtos
    - [Obter categorias de produtos](/product/category.md)
    - [Vitrines](/showcase/readme.md)
    - [Busca de produtos](/product/readme.md)
    - [Preço e disponibilidade](/product/availability.md)
    - [Obter detalhes de um produto](/product/detail.md)
    - Cálculo de frete
      - Produto virtual
      - [Produto físico](/product/phisical-shipping.md)
  - Carrinho de compras
    - [Obter dados do carrinho](/cart/readme.md)
    - [Adicionar item físico ao carrinho](/cart/add.md)
    - [Adicionar voucher ao carrinho](/cart/add-voucher.md)
    - [Alterar um item do carrinho](/cart/update.md)
    - Remover um item do carrinho
    - Adicionar endereço de entrega
    - Calcular o frete do carrinho
  - Compra
    - Criar uma compra
    - Criar uma compra com cartão de crédito

- [Resgate de serviços] _(em breve...)_
  - Recarga de Celular - _em breve_
  - Pagamento de Boletos - _em breve_
  - Milhas Aéreas - _em breve_
  - Compra de Pontos - _em breve_
  - Doações de pontos - _em breve_

- [Authorize e Confirm (Apenas débito de pontos)](/purchase/external.md)
  - [Authorização de débito](/purchase/authorize.md)
    - Antifraude _(em breve...)_
  - [Confirmação de débito](/purchase/confirm.md)
  - [Cancelamento de débito](/purchase/cancel.md)
  - Consultar pedidos

## Estorno de pedido
- [Introdução](reversal/readme.md) 
- [Estorno Total](reversal/total.md)
- Estorno parcial
  - [Valor da order](reversal/order-value.md)
  - [Valor do frete](reversal/shipping-value.md)
  - [Quantidade de produtos](reversal/product-quantity.md)

## Monitoria

## Laboratórios
- Implementado um catalogo de pontos - Passo a Passo
