# LTM CloudLoyalty - Identity Server

## Fluxo Client Credentials

Com aplicações machine-to-machine (M2M), tais como CLIs, daemons ou serviços executando em seus back-ends, o sistema autentica e autoriza tais app sem um usuário.
Para esse cenário, autenticação típica como login + senha não fazem sentido.
Ao invés disso, aplicações M2M utiliza o **Fluxo Client Credentials** (definido em [OAuth 2.0 RFC 6749, section 4.4](https://tools.ietf.org/html/rfc6749#section-4.4)), no qual passamos adiante nosso Client ID e nosso Client Secret para nos autenticarmos e obtermos um token de acesso.

## How It Works

![CLient Credentials Flow](/images/auth-sequence-client-credentials.png)

- Sua aplicação se autentica com o **CloudLoyalty Authorization Server** usando seu Client ID e Client Secret em (/oauth/token endpoint)

- Nosso **CloudLoyalty Authorization Server** valida o Client ID e o Client Secret.

- Nosso **CloudLoyalty Authorization Server** responde com um Access Token.

- Sua aplicação pode usar o Access Token para chamar nossas apis.

- Nossas APIs devem responder com o dado requisitado.

### Exemplo de requisição

    curl --location --request POST 'https://auth.{your-tenant-domain}/oauth2/token' \
    --header 'Content-Type: application/x-www-form-urlencoded' \
    --data-urlencode 'client_id=your-client-id' \
    --data-urlencode 'scope=your-scopes' \
    --data-urlencode 'grant_type=client_credentials'

### Exemplo de resposta

    {
        "access_token": "XXX...",
        "expires_in": 3600,
        "token_type": "Bearer"
    }

## **_Links relacionados_**

[Autenticação]()

[Single Sign On (SSO)]()

### Documentação completa:

> [Clique aqui](/auth/cognito/sso.md) para acessar o sumário completo da documentação.

[<< Anterior]() [Próximo >>]()
