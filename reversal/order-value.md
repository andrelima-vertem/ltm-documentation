[Início](/readme.md) &raquo; Estorno &raquo; Estorno parcial &raquo; [Valor do pedido](/purchase/order-value.md)
# Estorno parcial - Valor do pedido
Caso seja necessário estornar parte do valor do pedido, deve-se preencher o valor a ser estornado, dentro do valor do pedido fora o frete, e sinalizando o estorno parcial.
	Segue um exemplo abaixo:

	curl --location --request POST 'https://api.ltm.digital/order-api/v3/orders/{id}/reversal/external' \
--header 'Authorization: {TOKEN AD}' \
--header 'Ocp-Apim-Subscription-Key: {Subscription}' \
--data-raw '{
  "executeTotalRefund": false,
  "currentRefundValue": {VALOR DO PEDIDO (SEM FRETE)},
  "refundMotiveDescription": "{DESCRIÇÃO DO MOTIVO}",
  "refundShippingValue": 0,
  "refundMotiveId": {ID DO MOTIVO},
  "refundType": 1,	
  "orderItems": []
}'
## Próximos passos
[Estorno parcial -  Quantidade de produtos](/reversal/product-quantity.md)