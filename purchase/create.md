[Início](/readme.md) &raquo; Compras / Resgates &raquo; Criar uma compra com carrinho

# Criar nova compra

Recurso utilizado para criar uma nova compra.

## Link da documentação no portal do desenvolvedor

> https://portal.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/OrderCloudLoyalty_CreateOrder?&tags=Compra

## Dicionário de Erros

| Código | Mensagem | Sub | Descrição | Http Status |
|-|-|-|-|-|
| 76 | Problemas internos: Endereço de entrega não atribuído. | Não | - | 422 |
| 77 | Problemas internos: O carrinho está vazio. | Não | Por algum motivo o carrinho se encontra vazio no momento da validação dos dados. Deve-se incluir um produto no carrinho e caso o erro persista, reportar como um item crítico. | 422 |
| 86 | O pagamento deste tipo de boleto só pode ser feito nos terminais de auto-atendimento. | Não | - | 422 |
| 87 | O telefone parece incorreto. Verifique e tente novamente. | Não | - | 422 |
| 97 | Não foi possível finalizar seu pedido. Tente novamente. | Não | - | 422 |
| 99 | Problemas com o processamento do token. | Não | - | 400 |
| 100 | Encontramos dificuldades para realizar a operação. Tente novamente em instantes. - Consulta de Saldo indisponível, tente novamente. | Não | - | 400 |
| 103 | Não é possível realizar esta operação. (Tipo de token inválido.) | Não | Verifique se o access_token informado foi gerado corretamente ou se possui permissões para executar a operação. | 401 |
| 120 | Sistema indisponível no momento. Tente novamente em instantes. | Não | - | - |
| 122 | Bandeira não encontrada na base de configuração! | Não | - | - |
| 123 | Quantidade de parcelas excedentes | Não | - | - |
| 279 | Catálogo não permite a utilização de pagamento total no dinheiro! | Não | - | - |
| 289 | Há regras do carrinho que não foram atendidas. | **Sim\*** | As regras são relativas a cada catalogo, parceiro ou campanha. Ou seja, pode ou não estar ativas e trazem esse especícico critério. Consulte as regras de sua campanha e seus respectivos catálogos e parceiros para conhecer quais regras considerar. | 422 |
| 312 | Uma tentativa de resgate com parametros nulos foi efetuada. | Não | Erro ao executar um resgate, motivo: ausência dos parâmetros necessários.  | 400 |
| 313 | Uma tentativa de resgate inválida com cartão de crédito foi efetuada. | Não | Erro ao executar um resgate, motivo: os dados informados do cartão de crédito estão incorretos. | 422 |
| 314 | Uma tentativa de resgate sem informar o Canal foi efetuada. | Não | Erro ao executar um resgate, motivo: o canal informado não foi informado ou está incorreto. | 422 |
| 315 | Uma tentativa de resgate foi efetuada, erros na validação de regras do carrinho. | Não | Erro ao executar um resgate, motivo: há regras  do carrinho que não foram atendidadas. Para maiores informações, consulte **código 289**.  | 422 |
| 316 | O produto selecionado não é permitido para compras com o contexto informado. | **Sim\*** | Erro ao executar um resgate, motivo: o contexto utilizado não aceita somente dinheiro. | 422 |
| 317 | Uma tentativa de resgate foi efetuada, porém erros no cálculo de frete impediram a conclusão. | Não | Erro ao executar um resgate, motivo: incoerências nos cálculos de frete. | 422 |
| 318 | Uma tentativa de resgate foi efetuada, porém há divergência(s) no(s) item(s) - preço / estoque. | Não | Erro ao executar um resgate, motivo: preço divergente ou item sem estoque.  | 422 |
| 319 | Uma tentativa de resgate foi efetuada, porém PointsValue é inválido. | Não | Erro ao executar um resgate, motivo: quantidade insulficiente de Pontos | 422 |
| 320 | Uma tentativa de resgate foi efetuada, problemas com pontos e dinheiro (cash). | Não | Erro com o valor dos pontos. | 422 |
| 321 | Uma tentativa de resgate foi efetuada, problemas com o saldo do participante. | Não | Erro ao executar um resgate, motivo: problemas com o valor dos pontos ou do dinheiro (cash). | - |
| 322 | Encontramos dificuldades para realizar a operação. Entre em contato com o administrador do sistema. | **Sim\*** | ERRO GENÉRICO | 422 |
| 323 | Uma tentativa de resgate foi efetuada, problemas apenas com dinheiro(cash). | Não | Erro ao executar um resgate, motivo: incosistências dos dados. | 500 |
| 324 | Validando retorno do Banking, avaliando requisição para token. | Não | Erro ao executar um resgate, motivo: problemas com o dinheiro (cash). | - |
| 325 | Para sua segurança não foi possível concluir a sua transação. | Não | - | - |
| 326 | Para sua segurança não foi possível concluir a sua transação. Entre em contato com a Central para que possamos confirmar algumas informações. | Não | - | - |
| 327 | Para sua segurança não foi possível concluir a sua transação. Tente novamente em alguns minutos. | Não | - | - |
| 328 | Para sua segurança não foi possível concluir a sua transação. Entre em contato com a Central para que possamos confirmar algumas informações. | Não | - | - |
| 329 | Para sua segurança não foi possível concluir a sua transação. | Não | - | - |
| 330 | Para sua segurança não foi possível concluir a sua transação. | Não | - | - |
| 331 | Não foi possível concluir a sua transação. | Não | - | - |

### * Tabela Sub Erros - Código 289

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| 1 | Insira no máximo 2 itens no carrinho para Magazine Luiza. | "Maximo de itens por parceiro": Os itens excederam a quantidade máxima total de produtos por compra permitida pelo parceiro. Ex: Quantidade Máxima 3 itens: 2 geladeiras, 2 fogões foi negado por exceder 3 itens. |
| 2 | Insira no máximo 2 itens no carrinho. | "Maximo de itens por sku e parceiro": A quantidade máxima para cada item por compra permitida pelo parceiro foi excedida, Ex: Quantidade Máxima 3 por item: 2 geladeiras, 2 fogões não foi negado por não exceder a quantidade por item. |
| 3 | O valor da compra não pode exceder R$x | "Valor máximo por parceiro": o valor total de itens de um mesmo parceiro foi excedido. |
| 4 | Não é permitido Magalu e outra loja na mesma compra | "Somente um supplier no carrinho": Apenas produtos de um mesmo parceiro é permitido por compra. |
| 5 | Compre no máximo 1 produto por loja | Somente um sku do supplier no carrinho: Apenas 1 unidade de um produto para um determinado parceiro. |
| 6 | Não aprovado pelas regras da promoção | Regras da avon no cluster: Apenas para cliente Avon, regra para cluster de usuários. |

### * Tabela Sub Erros - Código 316

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| 1 | 4785d50b21c64707adc3 | SKU do produto adicionado não permitido |
| 2 | Pontos/Cash | Tipo do contexto inválido(ponto ou dinheiro). |

### * Tabela Sub Inconsistências - Código 322

| Código (Type) | Mensagem (Message) | Descrição |
|-|-|-|
| 1 | 4785d50b21c64707adc3 | SKU do produto adicionado não permitido |
| 2 | Pontos/Cash | Tipo do contexto inválido(ponto ou dinheiro). |

## Dicas de Uso

> Correlation Id: Utilize o parâmetro "X-Correlation-Id" para gerar uma correlação nos seus fluxos de sistema utilizando o CloudLoyalty.
[Saiba as vantagens acessando aqui.](/tips/readme.md)
