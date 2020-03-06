[Início](/readme.md) &raquo; Autenticação &raquo; Qual fluxo de autenticação OAUTH2 devo escolher?

# Qual fluxo de autenticação OAUTH2 devo escolher

A definição do fluxo ideal basicamente se dá através da atuação ou não de um ator importante no fluxo: **Participante**.

## Authorization Code

Quando há o envolvimento do participante no fluxo, por padrão o fluxo a se utilizar é o **Authorizaton Code.**

Porém há requisitos importantes para utilizar o fluxo de **Authorization Code**

### Requisitos para o uso do Fluxo de Authorization Code

- Frontend Web APP / Mobile App
- Backend APP

## Client Credentials

Para fluxo que não tenha participação direta, ou seja, o participante não é responsável pelo login mesmo que ações serão tomadas em nome dele, o fluxo deverá ser o **client_credentials.**

### Requisitos para o uso do Client Credentials

- Backend APP

## Implicit Grant

Para aplicações 100% frontend, que não possuem um recurso de backend sob a gestão do integrador, o fluxo possível é o **Implicit.**

O **Authorization Code** não poderá ser utilizado nesse caso, pois o uso da chave secreta do client "client_secret" faz parto do fluxo. É uma brecha de segurança expor essa informação.

### Requisitos para o uso do Implicit Grant

- Frontend Web APP / Mobile App

## Conclusão

Para escolher a versão que o integrador deverá utilizar é necessário um parecer do time técnico da LTM Fidelidade.

## Próximos passos

[Qual fluxo de autenticação OAUTH2 devo escolher?](/auth/flows.md)
