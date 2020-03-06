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

Para fluxo que não tenha participação direta do participante, ou seja, o participante não é responsável pelo login mesmo que ações serão tomadas em nome dele, o fluxo deverá ser o **client_credentials.**

É um fluxo comumente **utilizado para fins de aplicações backoffice.**

O Fluxo **client_credentials** é geralmente o mais desejado por ser de muito mais fácil integração.
Porém, é incorreto fazer a escolha por questões de simplicidade.

Apesar de simples, é um fluxo arbitrário no que diz respeito à resgate de pontos de qualquer modalidade.
Portanto são necessários:

- Uma justificativa de negócios pela parte integradora
- Um consentimento do **dono da campanha (cliente)**
- Um aval técnico do time de **Segurança da informação**

### Requisitos para o uso do Client Credentials

- Escopos específicos de backoffice, por se tratar (por padrão) de um fluxo específico para essa finalidade
- Backend APP
- Uma justificativa de negócios pela parte integradora
- Um consentimento do **dono da campanha (cliente)**
- Um aval técnico do time de **Segurança da informação**

## Implicit Grant

Para aplicações 100% frontend, que não possuem um recurso de backend sob a gestão do integrador, o fluxo possível é o **Implicit.**

O **Authorization Code** não poderá ser utilizado nesse caso, pois o uso da chave secreta do client "client_secret" faz parte do fluxo. É uma brecha de segurança expor essa informação.

### Requisitos para o uso do Implicit Grant

- Frontend Web APP / Mobile App

## Conclusão

Para escolher o fluxo correto de integração é preciso .

## Próximos passos

[Versão 2.0 - Integração de Autenticação](/auth/cognito/readme.md)
