[Início](/readme.md) &raquo; Autenticação &raquo; [Versão 2.0 - Integração de Autenticação](/auth/cognito/readme.md) &raquo; Discovery Endpoint

# OIDC Discovery Endpoint

O CloudLoyalty Identity Server expõe documentos de descoberta do OIDC (https://auth.tenant-demo.webpremios.digital/.well-known/openid-configuration). Estes podem ser usados para configurar aplicativos automaticamente.

> OBS: O discovery endpoint é fornecido pela LTM Fidelidade, conforme descrito em: [Primeiros passos com o **CloudLoyalty.**](/starting.md)

Através de nosso well-known é possível a aplicação cliente estar em conformidade com qualquer tipo de mudança que o CloudLoyalty Identity Server possa sofrer.

Entre os objetivos estão, evitar que alterações de qualquer natureza possam afetar as aplicações clientes e tornar qualquer integração sustentável e com o mínimo possível de alterações.

### Exemplo de nossa api com os metadados de uma integração:

### Request

    curl -X GET \ https://auth.tenant-demo.webpremios.digital/.well-known/openid-configuration \ -H 'Postman-Token: 5e92dd6f-97d5-4686-821c-e1959fa64b6a' \
    -H 'cache-control: no-cache’

### Response

    {
        "authorization_endpoint": "https://auth.tenant-demo.webpremios.digital/oauth2/authorize",
        "id_token_signing_alg_values_supported": [
        "RS256"
        ],
        "issuer": "https://cognito-idp.us-east-1.amazonaws.com/us-
        east-1_999ZdNQiH",
        "jwks_uri": "https://cognito-idp.us-east-1.amazonaws.com/us-
        east-1_999ZdNQiH/.well-known/jwks.json",
        "response_types_supported": [
        ],
        "code",
        "token",
        "token id_token"
        "scopes_supported": [
        "openid",
        "email",
        "phone",
        "profile"
        ],
        "subject_types_supported": [
        "public"
        ],
        "token_endpoint": "https://auth.tenant-demo.webpremios.digital/oauth2/token",
        "token_endpoint_auth_methods_supported": [
        ],
        "client_secret_basic",
        "client_secret_post"
        "userinfo_endpoint": "https://auth.tenant-demo.webpremios.digital/oauth2/userInfo"
    }

## Authorization Endpoint

Para obter informações acesse a documentação da Amazon:

https://docs.aws.amazon.com/cognito/latest/developerguide/authorization-endpoint.html

## Token Endpoint

Para obter informações acesse a documentação da Amazon:

https://docs.aws.amazon.com/cognito/latest/developerguide/token-endpoint.html

## UserInfo Endpoint

As informações contidas no endpoint fornecem informações de segmentação do cliente.

Requisição:

    curl --location --request GET 'https://auth.campaign-demo.webpremios.digital/oauth2/userInfo' \
    --header 'Authorization: Bearer xxx...'

Exemplo de Resposta:

    {
        "sub": "7345188d-ae89-47d1-808f-506edaa116e8",
        "custom:campaign_id": "99999",
        "custom:catalog_id": "88888",
        "custom:participant_id": "28891366",
        "custom:client_id": "30303",
        "username": "12345678926"
    }

As informações mostram o tenant, segmento (catalog), id do usuário, id do cliente (cnpj da campanha) e login do usuário.

Para obter informações acesse a documentação da Amazon:

https://docs.aws.amazon.com/cognito/latest/developerguide/userinfo-endpoint.html

## Logout Endpoint

Para obter informações acesse a documentação da Amazon:

https://docs.aws.amazon.com/cognito/latest/developerguide/logout-endpoint.html

## Issuer e jwks_uri (JWT)

Para obter informações acesse a documentação da Amazon:

https://docs.aws.amazon.com/cognito/latest/developerguide/amazon-cognito-user-pools-using-tokens-verifying-a-jwt.html

# Próximos passos

[Authorization Code](/auth/cognito/authorization_code.md)
