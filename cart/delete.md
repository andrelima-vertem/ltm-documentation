[Início](/readme.md) &raquo; Carrinho &raquo; Remover item do carrinho

# Remover um item do carrinho

Recurso utilizado para remover um item na cesta de compras  

## Link da documentação no portal do desenvolvedor

> https://portal.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/CartCloudLoyalty_RemoveItem?&tags=Carrinho

## Dicionário de Erros

| Código | Mensagem | Sub | Descrição | Http Status |
|-|-|-|-|-|
| 77 | Problemas internos: O carrinho está vazio. | Não | Por algum motivo o carrinho se encontra vazio no momento da validação dos dados. Deve-se incluir um produto no carrinho e caso o erro persista, reportar como um item crítico. | 422 |
| 103 | Não é possível realizar esta operação. (Tipo de token inválido.) | Não | Verifique se o access_token informado foi gerado corretamente ou se possui permissões para executar a operação.| 401 |
| 271 | Produto(s) não encontrado(s)! | Não | Os dados informados sobre o produto não são válidos, verifique o código do sku / produto. | 422 |