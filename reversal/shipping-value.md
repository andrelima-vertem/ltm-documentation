# Estorno parcial - Valor do Frete

Também poderemos estornar o frete, colocando o valor estornado no campo de valor de frete. e sinalizando como estorno parcial.
	Abaixo um exemplo abaixo:

		curl --location --request POST 'https://api.ltm.digital/order-api/v3/orders/{id}/reversal/external' \
--header 'Authorization: {TOKEN AD}' \
--header 'Ocp-Apim-Subscription-Key: {Subscription}' \
--data-raw '{
  "executeTotalRefund": false,
  "currentRefundValue": 0,
  "refundMotiveDescription": "{DESCRIÇÃO DO MOTIVO}",
  "refundShippingValue": 0,
  "refundMotiveId": {ID DO MOTIVO},
  "refundType": 1,	
  "orderItems": [{
      "orderItemId": {ID DO ITEM DO PEDIDO},
      "refundValue": 0,
      "refundQuantity": {QUANTIDADE A SER EXTORNADA}
    }]
}	'
