[Início](/readme.md) &raquo; Participante &raquo; User Impersonation para Administradores

# User Impersonation para Administradores

A **representação do usuário (User Impersonation)** permite que você entre temporariamente como um usuário diferente na sua rede. Usuários com permissões completas de representação podem representar todos os outros usuários em sua rede e executar qualquer ação, independentemente do nível de permissão de representação do usuário. Os personificadores aparecem como eles mesmos no histórico de alterações.

    A capacidade de representar requer permissões de função do usuário. Se essas opções não estiverem disponíveis para você, entre em contato com o time LTM Fidelidade.

Existem várias razões pelas quais você pode querer representar um usuário:

- Para ajudar outro usuário a solucionar um problema. Se suas funções de usuário estiverem configuradas de maneira diferente, é possível que sua interface do usuário pareça diferente da deles e você precisará se passar por outro usuário para poder ver o que vê.
- Você deseja fazer alterações em nome de outro usuário (por exemplo, o outro usuário não sabe como efetuar uma compra e precisa de auxilio, ou um backoffice necessita auxiliar o usuário por telefone).
- Você é um administrador que está configurando funções de usuário e deseja visualizar o que outros usuários poderão ver, dependendo das permissões concedidas a eles.
- Você só pode representar um usuário por vez.
- Você não pode modificar as configurações de notificação de outro usuário enquanto estiver se passando por esse usuário.

## Utilizando a impersonalização

Podemos encontrar os dados para impersonalização na busca de participantes por login ou CPF.

Acesse [Participantes - Fluxo Client Credentials](/participant/client_credentials.md) para saber como buscar participantes.

Exemplo de response da busca de participantes por login ou CPF:

    [
        {
            "segment": {
                "clientId": "30599",
                "campaignId": 40499,
                "catalogId": 40599,
                "name": "Gold"
            },
            "id": 28631365,
            "name": "Naldo",
            "username": "11431398012", ...
        }
    ]

O trecho do response acima expõe informarções suficientes para utilizar a feature de impersonalização.

Aconselhamos armazenar essas informações na aplicação cliente, seja utilizando um mecanismo de cache ou armazenamento em banco de dados.

Parâmetros obrigatórios enviados no cabaçalho das requisições, utilizando a feature de impersonalização:

- **participantid:** Id do participante
- **catalogId:** Segmento id do participante
- **customerId:** Tenant Id
- **impersonatorUser:** Como uma compra pode ser impersonada é obrigatório o preenchimento dessa informação. Pode ser o codigo de um agente de backoffice ou a identificação do ClientApp.
- **username:** login do participante, obrigatório em fluxos de compras, saldo, extrato e pontos a expirar.

## Exemplos de um fluxo de Impersonalização

Consulta de saldo de um participante:

    curl --location --request GET 'https://cloudloyalty.api.com/participant-api/v3/participant/balance' \
    --header 'Ocp-Apim-Subscription-Key: b916c59ce3684c1nabba307fb75817wa' \
    --header 'participantid: 28631399' \
    --header 'catalogId: 40599' \
    --header 'customerId: 30599' \
    --header 'impersonatorUser: AgentID=9999' \
    --header 'username: integration.test'
    --authorization 'Bearer xxx...' \

## Fluxo de impersonalização

![Impersonation Flow](/images/impersonator-diagram.svg)
