[Início](/readme.md) &raquo; Compras / Resgates &raquo; Tipos de autenticação

# Tipos de autenticação

Os tipos de autenticação possíveis para os fluxos de compras são **Client Credentials e Authorization Code.**

## Client Credentials

O token obtido **não possui** os escopos necessários para consumo de recursos do CloudLoyalty que envolvam resgate de pontos, e informações de participantes.

O ausência do participante (usuário) no processo torna necessário o fluxo de [**impersonalização (User Impersonation).**](/participant/user_impersonation.md)

## Authorization Code

Para obter os dados do segmento do usuário, bem como o tenant id e login, acesse a documentação do openId Connect: [UserInfo Endpoint](/auth/cognito/well-known.md).

## Próximos passos

[Compras Internas](/purchase/internal.md)
