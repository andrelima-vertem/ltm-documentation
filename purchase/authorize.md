[Início](/readme.md) &raquo; Compras / Resgates &raquo; [Compras Externas](/purchase/external.md) &raquo; Autorização de compra

# Autorização de compra

Uma autorização de compra é o primeiro passo de uma compra externa.

Para saber mais sobre uma compra externa acesse: [Compras Externas.](/purchase/external.md)

O endpoint de autorização retorna um código de pedido, os pontos do participante ficam bloqueados (reservado) até que o próximos passos aconteçam.

Essa reserva deve ser **confirmada ou cancelada posteriormente.**

> A os pontos ficam reservados até que uma confirmação ou um cancelamento é processado.

Link da documentação técnica no portal do desenvolvedor

> https://cloudloyaltyuat1.portal.azure-api.net/docs/services/cloud-loyalty-marketplace-api/operations/OrderCloudLoyalty_Authorize

## Fluxo genérico

![Authorize Purchase](/images/purchase-external-1-diagram.svg)

## Tipos de autenticação

Para entender quais tipos de autenticação possíveis paraacesse: [Tipos de autenticação](/purchase/auth.md)

## Consistência

Para manter a consistência das informações enviadas, alguns pontos precisamos destacar.

### Shipping

As informações de entrega são enviadas nesse nó.
Nele temos o Customer (Destinatário) e ShippingAddress (Endereço).

    Caso o produto ou serviço oferecido não possua relevância passar essas informações, enviar os dados default do participante.

Os dados do shipping são meramente informados para efeitos de logs e relatórios. Ou seja, nesse fluxo a reponsabilidade de entrega do produto ou serviço é do parceiro.

### Items

O nó de itens possui algumas informações que devem ser enviadas com o padrão informado abaixo. Caso haja alguma especifidade a LTM Fidelidade informa o cliente pois é ela a reponsavél por informar os dados que precisam ser enviados.

**Items** representa um array com a quantidade de serviços ou produtos componentes da autorização de ordem.

#### ProductId

Valor padrão: "0", caso esse dado mude a LTM informará o parceiro / cliente.

#### VendorSku

Valor padrão: "0", caso esse dado mude a LTM informará o parceiro / cliente.

#### Sku

Valor padrão: "0", caso esse dado mude a LTM informará o parceiro / cliente.

#### Name

Favor informar um dado resumido, porém um pouco detalhado do item que está sendo vendido.

#### Quantity

Mais de um item da mesma clasificação poderá ser informado nesse campo.

#### Category

Informar a categoria do serviço / produto. Ex: viagens, restaurantes, milhas, aluguel de carros, atividades, etc.

#### CategoryId

Valor padrão: "0", caso esse dado mude a LTM informará o parceiro / cliente.

#### VendorId

Esta é uma informação informada pela LTM, esse dado é obrigatorio e deve ser informado de acordo com os dados de configuração informados previamente.

Para saber como obter esse dado, leia: [Primeiros passos com o **CloudLoyalty.**](/starting.md)

#### Parameters

O campo parameters é um dado dinâmico para fins de antifraude. É utilizado para passar informações mais especificas e contribuem para o sistema definir se a compra é segura. Logicamente a utilização do antifraude da LTM deve ser acordado previamente.

> Exemplo: dados de um serviço de passagens aéreas, alguel de carros, etc.

Alguns modelos recomendados de utilização.

**Passagens aéreas (sugestão)**

    "Parameters":{
        "AirFlightTicket":{
            "Quantity":1,
            "Name":"Aereo",
            "AirCarrier":"GOL Transportes Aéreos",
            "Transaction":{
                "AirMilesQuantity":"0"
            },
            "Flight":{
                "Type":"",
                "Passengers":[
                    {
                    "Name.0":"João",
                    "Surname.0":"Sereno",
                    "Phone.0":"",
                    "Document.0":"99996082228"
                    },
                    {
                    "Name.1":"Maria",
                    "Surname.1":"Eduarda",
                    "Phone.1":"",
                    "Document.1":"99996082228"
                    }
                ],
                "Ranges":[
                    {
                    "Way1":{
                        "AirCarrier":"GOL Transportes Aéreos",
                        "Class":"Y",
                        "FlightNumber":"1096",
                        "Seat":"",
                        "Origin":"GRU - Guarulhos",
                        "DepartureDate":"01/11/2019 18:05:00",
                        "Destination":"GIG - Galeão   Antônio Carlos Jobim",
                        "ArrivalDate":"01/11/2019 19:05:00"
                    }
                    }
                ]
            },
            "Locator":"99999"
        },
        "Hotelbooking":null,
        "Rentcar":null,
        "Activity":null,
        "Creditcard":null
    }

**Reservas de hotéis**

**Aluguel de carros**

    "Parameters": {
        "RentCar": {
            "Rental": "Alamo/Localiza",
            "Car": "SPIN 1.8 OU SIMILAR",
            "PickupDate": "2019-07-17T09:00:00",
            "ReturnDate": "2019-07-17T09:00:00",
            "PickupLocation": "2019-07-17T09:00:00",
            "ReturnLocation": "Florianópolis, Brasil - Hercílio Luz (FLN)",
            "Driver": [
                {
                        "Name.0": "miguel",
                        "Surname.0": "zuleta",
                        "Phone.0": "",
                        "Document.0": ""
                    }
            ]
        },
        "Creditcard": {
            "CardNumber": "000000000",
            "NameOnCard": "",
            "ExpirationMonth": 0,
            "ExpirationYear": 0,
            "Value": 0,
            "Parcels": 0,
            "ParcelValue": 0
        }
    }

**Compra de Passeios**

    "Parameters": {
        "Activity": {
            "Name": "Traslado de chegada em Miami",
            "City": "SPIN 1.8 OU SIMILAR",
            "Date": "2019-07-17T09:00:00",
            "Type": "2019-07-17T09:00:00",
            "Duration": "2019-07-17T09:00:00",
            "Participant": [
                {
                        "Name.0": "miguel",
                        "Surname.0": "zuleta"
                    }
            ]
        },
        "Creditcard": {
            "CardNumber": "000000000",
            "NameOnCard": "",
            "ExpirationMonth": 0,
            "ExpirationYear": 0,
            "Value": 0,
            "Parcels": 0,
            "ParcelValue": 0
        }
    }

**Reservas em restaurantes**

    "Parameters": {
        "ReservationTicket":{
            "date":"2020-03-11",
            "ambience":"58d189b73a501fd811745d3c",
            "people":2,
            "time":"13:00"
        }
    }

### ConversionRate

Informações sobre a conversão de pontos, esse campo é informado de acordo com a configuração de campanha que define se essa dado deve ser lido ou ignorado por essa api.

#### VendorId

Este campo deve ser informado com informação compatível com vendor informado.

Para saber como obter esse dado, leia: [Primeiros passos com o **CloudLoyalty.**](/starting.md)

#### ConversionFactor

Valor da taxa de conversão, a LTM deverá informar o valor deste dado ao parceiro / cliente.

### Payment

Informações de pagamento que devem condizer com a soma dos itens enviados no nó **ITEMS.**

#### Tipos de pagamentos (Points, ExternalCreditCard, CreditCard)

- Points = Valor informado de pontos a debitar do particiapnte.

- CreditCard = Cartão de crédito. Por padrão **essa opção é inativa** e deve ser negociado com a LTM a utilização de débito em cartões de crédito.

- ExternalCreditCard = cartão e crédito externo, ou seja, o participante efetuou a compra em cartão de crédito mas o **parceiro foi responsável pelo processamento do pagamento no gateway de sua escolha.** Deve-se informar o valor nesse campo para manter a consistência da ordem nos storages.

#### Tipos de pagamentos (Points, ExternalCreditCard, CreditCard)

## Próximos passos

[Compras Internas](/purchase/confirm.md)
