[Início](/readme.md) &raquo; Estorno &raquo; [Estorno Total](/purchase/total.md)
# Estorno Total
O estorno total tem como objetivo estornar totalmente o valor de um determinado pedido feito no parceiro, que comtempla frete + valor total dos itens do pedido. Sendo assim o vetor de itens não deve ser preenchido, para não conflitar o estorno total e parcial.
O valor de frete deverá ser preenchido, para estornar todos os valores.
Segue um exemplo abaixo:

<code>curl --location --request POST 'https://api.ltm.digital/order-api/v3/orders/{id}/reversal/external' \
--header 'Authorization: {TOKEN AD}' \
--header 'Ocp-Apim-Subscription-Key: {Subscription}' \
--data-raw '{
  "executeTotalRefund": true,
  "currentRefundValue": 0,
  "refundMotiveDescription": "{DESCRIÇÃO DO MOTIVO}",
  "refundShippingValue": {VALOR DE FRETE},
  "refundMotiveId": {ID DO MOTIVO},
  "refundType": 2,	
  "orderItems": []
}'</code>

## Próximos passos

[Estorno parcial - Valor do pedido ](/reversal/order-value.md)