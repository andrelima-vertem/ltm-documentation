# Introdução



O estorno de um pedido, é a devolução do pagamento de parcial ou total, após todo o fluxo de pedido for realizado. É uma forma de cancelamento após já termos pago o pedido aos parceiros.

O que é importante salientar é que neste endpoint não estornamos a compra, mas cada pedido. A compra é composta de vários pedidos, que é composto de um grupo de produtos de um determinado parceiro. Sendo assim o estorno ocorre por pedido fechado no parceiro.

Existem 4 tipos de estorno hoje implementados : [Estorno total](reversal/total), [Estorno parcial - Valor da order](reversal/order-value), [Estorno parcial - Quantidade de produtos](reverval/product-quantity) e [Estorno parcial - valor de frete](shipping-value)

## Próximos passos

[Extorno Total](/reversal/total.md)