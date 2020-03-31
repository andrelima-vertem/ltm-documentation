[Início](/readme.md) &raquo; Estorno &raquo; Estorno parcial &raquo; [Valor do pedido](/purchase/order-value.md)
# Estorno parcial - Valor do pedido
As requests de estorno, são realizadas como visto abaixo:
<code>curl --location --request POST 'https://api.ltm.digital/order-api/v3/orders/{id}/reversal/external' \
--header 'Authorization: {TOKEN AD}' \
--header 'Ocp-Apim-Subscription-Key: {Subscription}' \
--data-raw '{
  "executeTotalRefund": false,
  "currentRefundValue": 0,
  "refundMotiveDescription": "teste",
  "refundShippingValue": 0,
  "refundMotiveId": 16,
  "refundType": 1,	
  "orderItems": [{
      "orderItemId": 11111111,
      "refundValue": 0,
      "refundQuantity": 0
    }]
}'</code>

Variável da URL:
- id : Identificador do pedido que foi realizado em um parceiro

Header:
- Authorization: token de acesso do active directory da azure da LTM
- Ocp-Apim-Subscription-Key: subscription de acesso aos endpoints do cloudloyalty

Abaixo descrevo os campos do payload:
- executeTotalRefund : sinaliza o extorno parcial ou total do pedido

- currentRefundValue : valor a ser estornado, caso a flag executeTotalRefund esteja com valor true este campo deverá assumir o valor 0

- currentRefundValue : valor a ser estornado, caso a flag executeTotalRefund esteja com valor true este campo deverá assumir o valor 0

- refundMotiveId: Id do motivo de estorno que pode assumir os seguintes valores :
    - 1	Erro no Serviço do Parceiro
    - 2	Pagamento recusado
    - 3	Produto não entregue
    - 4	Cancelamento de Pedido
    - 5	Produto danificado
    - 6	Mudou-se
    - 7	Ausente
    - 8	Não procurado
    - 9	Recusado
    - 10	Não existe numero indicado
    - 11	Desconhecido
    - 12	Endereço insuficiente
    - 13	Indisponibilidade
    - 14	Estorno de frete
    - 15	Pedido Teste
    - 16	Arrependimento do Cliente
    - 17	Pedido Bloqueado
    - 18	Pedido Extraviado
    - 19	Pedido não gerado
    - 20	Desconto no Produto
    - 21	Automático
    - 22	Pedido não efetivado
    - 23	Reclamação não atendida dentro do prazo pelo parceiro
    - 24	Dificuldade na região
    - 25	Frete indevido
    - 26	Email inválido
    - 27	Destinatario ausente 
    - 28	Pedido roubado
    - 29	Pedido extraviado
    - 30	Endereço insuficiente 
    - 31	Não atende a região
    - 32	Não retirou o produto nos Correios
    - 33	Endereço não localizado
    - 34	Mudou-se
    - 35	Pedido não gerado no parceiro
    - 36	Pedido não processado pelo parceiro
    - 37	Pedido bloqueado
    - 38	Frete indevido
    - 39	Estorno de frete 
    - 40	E-mail inválido
    - 41	Arrependimento do cliente
    - 42	Não cumprimento do SLA
    - 43	Pedido avariado
    - 44	Pedido teste
    - 45	Indisponibilidade
    - 46	Desconto no produto
    - 47	Pedido não migrado
    - 48	Erro no POS
    - 49	Arrependimento - Liberação Cliente
    - 50	Pontuação expirada - Liberação cliente
- refundType: identificador do tipo do estorno que pode assumir os valores abaixo:
    - 1 - Quantidade : este iten sinaliza que o estorno será realizado pelos campos de quantidade (orderItem.refundQuantity)
	- 2 - Valor : este iten sinaliza que o estorno será realizado pelos campos de valor (orderItem.refundValue e currentRefundValue)
- orderItems: lista de itens do pedido a serem estornados
    - orderItemId: Identificador do item de pedido
    - refundValue: valor a ser estornado do item
    - refundQuantity: quantidade de itens a serem estornados, este campo deverá ser preenchido se a

  
## Próximos passos

[Token](/reversal/token.md)