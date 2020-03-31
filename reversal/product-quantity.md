[Início](/readme.md) &raquo; Estorno &raquo; Estorno parcial &raquo; [Quantidade de produtos](/purchase/product-quatity.md)
# Estorno parcial -  Quantidade de produtos
O estorno por quantidade de produto, calcula o valor estornado pelo parâmetro de quantidade de um determinado item no payload.
	Segue um exemplo abaixo:
<code>curl --location --request POST 'https://api.ltm.digital/order-api/v3/orders/{id}/reversal/external' \
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
}'</code>

## Próximos passos

[Estorno parcial - Valor de frete](/reversal/shipping-value.md)