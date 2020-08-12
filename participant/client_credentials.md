[Início](/readme.md) &raquo; Participante &raquo; Fluxo Client Credentials

# Fluxo Client Credentials

O token obitido por esse fluxo possui um perfil acima do permissionamento da participantes.
Com ele é possível gerenciar recursos de um ou mais participantes.
Portanto é necessário escolher qual participante se quer obter.

Para tal precisamos utilizar a busca do participante por login ou CPF.

Link da documentação no portal do desenvolvedor

> https://portal.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/ParticipantCloudLoyalty_GetByLoginOrDocument?

Exemplo de response

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
            "username": "11431398012",
            "documentNumber": "29973639855",
            "rg": null,
            "birthDate": "1996-02-29T03:00:00+00:00",
            "persontype": "INDIVIDUAL",
            "genderType": "MALE",
            "maritalStatus": "MARRIED",
            "status": "INACTIVE",
            "emails": [
                {
                    "email": "11431398012@mailinator.com",
                    "type": "PERSONAL"
                }
            ],
            "phones": [
                {
                    "areaCode": "11",
                    "number": "55223366",
                    "type": "HOME"
                },
                {
                    "areaCode": "51",
                    "number": "995058289",
                    "type": "MOBILE"
                }
            ],
            "address": {
                "street": "Alameda Rio Negro",
                "number": "585",
                "complement": "Bloco C - 12 Andar",
                "district": "Alphaville Centro Industrial e Empresarial/Alphaville.",
                "city": "Barueri",
                "state": "SP",
                "zipCode": "06454000",
                "reference": null
            }
        }
    ]

## User Impersonation

O token obtido **não possui** os escopos necessários para consumo de recursos do CloudLoyalty que envolvam resgate de pontos, e informações de participantes.

O ausência do participante (usuário) no processo torna necessário o fluxo de [**impersonalização (User Impersonation).**](/participant/user_impersonation.md)

Acesse a documentação da impersonalização a seguir.

## Próximos passos

[User Impersonation para Administradores.](/participant/user_impersonation.md)
