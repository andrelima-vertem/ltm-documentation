[Início](/readme.md) &raquo; Participante &raquo; Fluxo Authorization Code (SSO)

# Obtendo o participante - Fluxo SSO

O token obitido por esse fluxo possui um perfil de um participante.
Possui o segmento do cliente, a origem do user pool (tenant id) e o id do cliente (dono da campanha).

Com ele é possível gerenciar recursos de apenas um participante.

Basicamente é o fluxo que em geral o próprio participante var tomar as ações. Geralmente em uma aplicação cliente que consome as apis do CloudLoyalty.

Link da documentação no portal do desenvolvedor

> https://api.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/ParticipantCloudLoyalty_Get?

Para obter os dados do segmento do usuário, bem como o tenant id e login, acesse a documentação do openId Connect:
[UserInfo Endpoint](/auth/cognito/well-known.md).

## Dicas de Uso

> Correlation Id: Utilize o parâmetro "X-Correlation-Id" para gerar uma correlação nos seus fluxos de sistema utilizando o CloudLoyalty.
[Saiba as vantagens acessando aqui](/tips/readme.md)

## Próximos passos

[Saldo de pontos.](/participant/balance.md)
