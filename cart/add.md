[Início](/readme.md) &raquo; Carrinho &raquo; Adicionar item ao carrinho

# Adicionar item físico ao carrinho

Recurso utilizado para incluir um item na cesta de compras


## Link da documentação no portal do desenvolvedor

> https://portal.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/CartCloudLoyalty_AddItem?&tags=Carrinho

## Dicionário de Erros

| Código | Mensagem | Sub | Descrição | Http Status |
|-|-|-|-|-|
| 77 | Problemas internos: O carrinho está vazio. | Não | Por algum motivo o carrinho se encontra vazio no momento da validação dos dados. Deve-se incluir um produto no carrinho e caso o erro persista, reportar como um item crítico. | 422
| 103 | Não é possível realizar esta operação. (Tipo de token inválido.) | Não | Verifique se o access_token informado foi gerado corretamente ou se possui permissões para executar a operação.| 401 |
| 116 | Quantidade deve ser maior que 0. | Não | desc | 422
| 118 | O produto não está mais disponível no estoque do parceiro. | Não | desc | 422
| 271 | Produto(s) não encontrado(s)! | Não | desc | 422
| 283 | O parâmetro VendorId é inválido ou Loja/parceiro não está vinculado a campanha. | Não | desc | 422
| 284 | Sku não pertence ao parceiro informado, o parâmetro VendorId ou SKU é inválido. | Não | desc | 422
| 285 | O campo Email é obrigatório para o sku informado. | Não | desc | 422
| 286 | Um Email válido é obrigatório para o sku informado. | Não | desc | 422
| 287 | Não foi possível atribuir o destinatário ao item voucher. | Não | desc | 422
| 288 | Os parâmetros VendorId e Sku são obrigatórios. | Não | desc | 422
| 289 | Há regras do carrinho que não foram atendidas. | **Sim\*** | desc | 422

### * Tabela Sub Erros - Código 289

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| 1 | Insira no máximo 2 itens no carrinho para Magazine Luiza. | desc |
| 2 | Insira no máximo 2 itens no carrinho. | ddd |
| 3 | O valor da compra não pode exceder R$x | ddd |
| 4 | Não é permitido Magalu e outra loja na mesma compra |
| 5 | Compre no máximo 1 produto por loja | ddd |
| 6 | Não aprovado pelas regras da promoção | ddd |

## Dicas de Uso

> Correlation Id: Utilize o parâmetro "X-Correlation-Id" para gerar uma correlação nos seus fluxos de sistema utilizando o CloudLoyalty.
[Saiba as vantagens acessando aqui.](/tips/readme.md)