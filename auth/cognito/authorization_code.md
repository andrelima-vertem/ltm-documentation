[Início](/readme.md) &raquo; Autenticação &raquo; [Versão 2.0 - Integração de Autenticação](/auth/cognito/readme.md) &raquo;
[OpenId Connect / Single Sign On](/auth/cognito/sso.md) &raquo; Authorization Code

# Fluxo Authorization Code

Descritivo dos fluxos necessários para autenticação
em um [Tenant.](/starting.md)

## Introdução

Como os aplicativos Web comuns são aplicativos do lado do servidor em que o código-fonte não é exposto publicamente, eles podem usar o Fluxo Autorization Code (definido no [OAuth 2.0 RFC 6749, seção 4.1](https://tools.ietf.org/html/rfc6749#section-4.1)) para utilizar a autenticação de um usuário com o **CloudLoyalty Identity Server**, que troca um código de autorização por um token.

Seu aplicativo deve estar do lado do servidor, pois durante essa troca, você também deve transmitir o **Client Secret** do aplicativo, que deve sempre ser mantido seguro, e você precisará armazená-lo na sua aplicação client.

Para saber se o Authorization Code é o fluxo ideal para a sua integração consulte: [Qual fluxo de autenticação OAUTH2 devo escolher?](/auth/flows.md)

## How It Works

![Authorization Code Flow](/images/auth-sequence-auth-code.png)

- O usuário clica em Login no seu Web App.
- O **Web App (Front-End)** redireciona o usuário ao **Authorization Server do CloudLoyalty** ([Amazon Authorize Endpoint](https://docs.aws.amazon.com/cognito/latest/developerguide/authorization-endpoint.html)).

- O **Authorization Server do CloudLoyalty** redireciona o usuário para o prompt de login e autorização.

- O usuário se autentica usando uma das opções de login configuradas e pode ver uma página de consentimento listando as permissões que **Authorization Server do CloudLoyalty** concederá ao aplicativo Web.

- O **Authorization Server do CloudLoyalty** redireciona o usuário de volta ao aplicativo com um **código de autorização (authorization code)**.

- O Web APP (BackEnd) envia esse código ao **Authorization Server do CloudLoyalty** ([oauth2/token endpoint](https://docs.aws.amazon.com/cognito/latest/developerguide/token-endpoint.html)) junto com o client_id e o client_secret do aplicativo.

- O **Authorization Server do CloudLoyalty** verifica o código, o o client_id e o client_secret.

- O **Authorization Server do CloudLoyalty** responde com um token de identificação e um token de acesso (e, opcionalmente, um token de atualização).

- Seu aplicativo pode usar o token de acesso para chamar a **API do CloudLoyalty** para acessar informações sobre o usuário.

- A **API do CloudLoyalty** responde com os dados solicitados.

## Vamos a um passo-a-passo

### 1 - Acessar o discovery endpoint (Well-known)

Consulte [Discovery Endpoint](/auth/cognito/well-known.md) para saber mais.

Vamos utilizar o **authorization_enpoint** para montar nosso redirect.

### 2 - Redirect para o login

> https://authorization_endpoint? scope=YOUR_SCOPE& response_type=code& client_id=YOUR_CLIENT_ID& redirect_uri=https://YOUR_APP/callback& state=YOUR_OPAQUE_VALUE

demo:

    https://auth.tenant-demo.webpremios.digital/oauth2/authorize?client_id=
    1d27etn77kchrpokl5feg29999&redirect_uri=http://localhost/oauth/ callback&response_type=code&scope=profile webpremios.campaigns/{tenant_id} email
    openid&state=your_state

Vale uma pausa para entender o parâmetro **state**:

> ''
> -- **_State:_** _An opaque value the clients adds to the initial request. The authorization server includes this value when redirecting back to the client. This value must be used by the client to prevent [CSRF](https://en.wikipedia.org/wiki/Cross-site_request_forgery) attacks. **Optional but strongly recommended.**_

### 3 - Usuário efetua o login

Credenciais próprias do usuário.

### 4 - Recebendo o código de autorização

Depois que o **CloudLoyalty Authorization Server** verifica as credenciais do usuário, o mesmo é redirecionado para a URL que foi especificada no parâmetro de consulta redirect_uri original.

O redirecionamento também define um parâmetro de consulta code, que especifica o código de autorização obtido via usuário pelo **CloudLoyalty Authorization Server**.

    Ex: http://localhost/oauth/callback?code=5e9a7474-d191-4b8c-b0b8-e3f7924723be&state=your_state

### 5 - Obtendo tokens

O **Web App** hospedado na URL de redirecionamento pode extrair o código de autorização dos parâmetros da consulta e trocá-lo por tokens do **CloudLoyalty Authorization Server**.

A troca ocorre enviando uma solicitação POST para o **token_endpoint** informado no **well-known.**

- Utilizar Base64 do client_id e client_secret:

  - O **CloudLoyalty Authorization Server** requer uma credencial confidencial, o cabeçalho de autorização para essa solicitação é definido como **“Basic BASE64 (CLIENT_ID: CLIENT_SECRET)“**, em que BASE64 (CLIENT_ID:CLIENT_SECRET) é a representação base64 do Client Id e Client Secret concatenado com dois pontos.

- Utilizar o campo token_endpoint para gerar o token com os seguintes **application/x-www-form-urlencoded** parâmetros:

  - grant_type - Defina como **“authorization_code”** para este grant.
  - code - o código de autorização gerado ao usuário.
  - redirect_uri - O mesmo da solicitação no passo 2.
  - authorization - BASE64 (CLIENT_ID:CLIENT_SECRET)

Exemplo de request:

    curl -X POST \
    https://auth.padrao-uat.webpremios.digital/oauth2/token \
    -H 'Authorization: Basic xxx..' \
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d ‘grant_type=authorization_code&redirect_uri=https%3A%2F%2Flocalhost%2Fcallback&code=code'

- O JSON retornado na resposta resultante possui as seguintes chaves:
  - **id_token** - Um token válido de ID do pool de usuários. Observe que um token de ID só é fornecido se o escopo openid foi solicitado. (Este token é o que torna possível o SSO)
  - **access_token** - Um token de acesso do LTM Identity Server válido
  - **refresh_token** - Um token de atualização do LTM Identity Server válido. - Isso pode ser usado para recuperar novos tokens enviando-os por uma solicitação POST para **token_endpoint**, especificando os parâmetros _refresh_token, client_id e configurando o parâmetro grant_type como “refresh_token“._
    - O refresh_token por padrão é válido por 30 dias.
    - Encorajamos todas as aplicações cliente utilizarem o fluxo de **RefreshToken**, isso melhora a experiência do usuário e potencializa resgates.
  - **expires_in** - O período de tempo (em segundos) pelo qual o ID fornecido e / ou o (s) token (s) de acesso são válidos.
  - **token_type** - Defina como “Bearer".

#### Armazenando tokens

A LTM Fidelidade sugere uma solução técnica que é o uso do token em cache.

### 6 - Pronto!

Sua aplicação está pronta para consumir recursos do CloudLoyalty.

# Próximos passos

[Participante - Fluxo Authorization Code (SSO)](/participant/authorization_code.md)
