[Início](/readme.md) &raquo; Carrinho &raquo; Adicionar item ao carrinho

# Adicionar item virtual ao carrinho

Recurso utilizado para incluir um item na cesta de compras

## Link da documentação no portal do desenvolvedor

> https://portal.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/CartCloudLoyalty_AddItem?&tags=Carrinho

## Dicionário de Erros

| Código | Mensagem | Sub | Descrição | Http Status |
|-|-|-|-|-|
| 77 | Problemas internos: O carrinho está vazio. | Não | Por algum motivo o carrinho se encontra vazio no momento da validação dos dados. Deve-se incluir um produto no carrinho e caso o erro persista, reportar como um item crítico. | 422
| 103 | Não é possível realizar esta operação. (Tipo de token inválido.) | Não | Verifique se o access_token informado foi gerado corretamente ou se possui permissões para executar a operação.| 401 |
| 116 | A quantidade informada está fora do permitido, deve-se informar o mínimo permitido.
 | 422
| 118 | O produto não está mais disponível no estoque do parceiro. | Não | Ao validar a disponibilidade e o preço atualizado do produto perante o parceiro o produto nos apresentou indisponibilidade de preço ou estoque. | 422
| 271 | Produto(s) não encontrado(s)! | Não | Os dados informados sobre o produto não são válidos, verifique o código do sku / produto. | 422
| 283 | O parâmetro VendorId é inválido ou Loja/parceiro não está vinculado a campanha. | Não | O parceiro não foi encontrado na campanha, deve-se verificar o parametro VendorId (parceiro ID). | 422
| 284 | Sku não pertence ao parceiro informado, o parâmetro VendorId ou SKU é inválido. | Não | Certificar-se que o sku corresponde ao parceiro (vendor) informado. | 422
| 285 | O campo Email é obrigatório para o sku informado. | Não | É obrigatorio informar um email válido para um sku do tipo voucher (entrega virtual).
 | 422
| 286 | Um Email válido é obrigatório para o sku informado. | Não | É obrigatorio informar um email válido para um sku do tipo voucher (entrega virtual). | 422
| 287 | Não foi possível atribuir o destinatário ao item voucher. | Não | Erro crítico ao atribuir o email de entrega do voucher, favor informar o administrador. | 422
| 288 | Os parâmetros VendorId e Sku são obrigatórios. | Não | Algum dos parâmetros ou ambos não foram informados, campos obrigatórios. | 422
| 289 | Há regras do carrinho que não foram atendidas. | **Sim\*** | As regras são relativas a cada catalogo, parceiro ou campanha. Ou seja, pode ou não estar ativas e trazem esse especícico critério.
Consulte as regras de sua campanha e seus respectivos catálogos e parceiros para conhecer quais regras considerar.
 | 422

### * Tabela Sub Erros - Código 289

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| 1 | Insira no máximo 2 itens no carrinho para Magazine Luiza. | 1 - "Maximo de itens por parceiro": Os itens excederam a quantidade máxima total de produtos por compra permitida pelo parceiro. Ex: Quantidade Máxima 3 itens: 2 geladeiras, 2 fogões foi negado por exceder 3 itens. |
| 2 | Insira no máximo 2 itens no carrinho. | "Maximo de itens por sku e parceiro": A quantidade máxima para cada item por compra permitida pelo parceiro foi excedida, Ex: Quantidade Máxima 3 por item: 2 geladeiras, 2 fogões não foi negado por não exceder a quantidade por item. |
| 3 | O valor da compra não pode exceder R$x | "Valor máximo por parceiro": o valor total de itens de um mesmo parceiro foi excedido. |
| 4 | Não é permitido Magalu e outra loja na mesma compra | "Somente um supplier no carrinho": Apenas produtos de um mesmo parceiro é permitido por compra. |
| 5 | Compre no máximo 1 produto por loja | Somente um sku do supplier no carrinho: Apenas 1 unidade de um produto para um determinado parceiro. |
| 6 | Não aprovado pelas regras da promoção | Regras da avon no cluster: Apenas para cliente Avon, regra para cluster de usuários. |

## Dicas de Uso

> Correlation Id: Utilize o parâmetro "X-Correlation-Id" para gerar uma correlação nos seus fluxos de sistema utilizando o CloudLoyalty.
[Saiba as vantagens acessando aqui.](/tips/readme.md)