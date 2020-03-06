[Início](/readme.md) &raquo; Autenticação &raquo; [Versão 2.0 - Integração de Autenticação](/auth/cognito/readme.md) &raquo; Client Credentials

# LTM CloudLoyalty - Identity Server

## Fluxo Client Credentials

Com aplicações machine-to-machine (M2M), tais como CLIs, daemons ou serviços executando em seus back-ends, o sistema autentica e autoriza tais app sem um usuário.
Para esse cenário, autenticação típica como login + senha não fazem sentido.
Ao invés disso, aplicações M2M utiliza o **Fluxo Client Credentials** (definido em [OAuth 2.0 RFC 6749, section 4.4](https://tools.ietf.org/html/rfc6749#section-4.4)), no qual passamos adiante nosso Client ID e nosso Client Secret para nos autenticarmos e obtermos um token de acesso.

Para saber se o Client Credentials é o fluxo ideal para a sua integração consulte: [Qual fluxo de autenticação OAUTH2 devo escolher?](/auth/flows.md)

## How It Works

![Client Credentials Flow](/images/auth-sequence-client-credentials.png)

- Sua aplicação se autentica com o **CloudLoyalty Authorization Server** usando seu Client ID e Client Secret em (/oauth/token endpoint)

- Nosso **CloudLoyalty Authorization Server** valida o Client ID e o Client Secret.

- Nosso **CloudLoyalty Authorization Server** responde com um Access Token.

- Sua aplicação pode usar o Access Token para chamar nossas apis.

- Nossas APIs devem responder com o dado requisitado.

### Exemplo de requisição

    curl --location --request POST 'https://auth.{your-tenant-domain}/oauth2/token' \
    --header 'Content-Type: application/x-www-form-urlencoded' \
    --authorization 'Basic Base64(XXXX...)' \
    --data-urlencode 'client_id=your-client-id' \
    --data-urlencode 'scope=your-scopes' \
    --data-urlencode 'grant_type=client_credentials'

### Exemplo de resposta

    {
        "access_token": "XXX...",
        "expires_in": 3600,
        "token_type": "Bearer"
    }

### Token Endpoint

A url de token está no documento de descoberta do seu user pool. Consulte [Discovery Endpoint](/auth/cognito/well-known.md) para saber mais.

Para obter informações acesse a documentação da Amazon:

https://docs.aws.amazon.com/cognito/latest/developerguide/token-endpoint.html

### Permited Scopes

- Fluxo Client Credentials

  - _webpremios.campaigns/{tenant-id}_
  - _webpremios.backoffice/all.read_
  - _webpremios.backoffice/all.write_

Para entender melhor os parametros da request acesse o link: [Primeiros passos com o **CloudLoyalty**](/starting.md)

## **_Links relacionados_**

[Fluxo Client Credentials para consultar um participante.](/participant/client_credentials.md)

[User Impersonation para Administradores.](/participant/user_impersonation.md)

# Próximos passos

[Participante - Fluxo Client Credentials](/participant/client_credentials.md)
