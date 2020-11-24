
[Início](/readme.md) &raquo; Compras / Resgates &raquo; Criar uma compra com carrinho

# Criar nova compra

Recurso utilizado para criar uma nova compra.

## Link da documentação no portal do desenvolvedor

> https://portal.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/OrderCloudLoyalty_CreateOrder?&tags=Compra

## Dicionário de Erros

| Código | Mensagem |Sub Mensagem| Sub | Descrição | Http Status |
|-|-|-|-|-|-|
| 76 | Problemas internos: Endereço de entrega não atribuído. |Não| Não | Uma tentativa de resgate foi efetuada com um carrinho montado incorretamente no fluxo de checkout (validação de carrinho). | 422 |
| 77 | Problemas internos: O carrinho está vazio. |Não| Não | Por algum motivo o carrinho se encontra vazio no momento da validação dos dados. Deve-se incluir um produto no carrinho e caso o erro persista, reportar como um item crítico. | 422 |
| 86 | O pagamento deste tipo de boleto só pode ser feito nos terminais de auto-atendimento. |Não| Não | - | 422 |
| 87 | O telefone parece incorreto. Verifique e tente novamente.|Não| Não | - | 422 |
| 97 | Não foi possível finalizar seu pedido. Tente novamente. |Não| Não | - | 422 |
| 99 | Problemas com o processamento do token.|Não| Não | - | 400 |
| 100 | Encontramos dificuldades para realizar a operação. Tente novamente em instantes. - Consulta de Saldo indisponível, tente novamente. |Não| Não | - | 400 |
| 103 | Não é possível realizar esta operação. (Tipo de token inválido.) |Não| Não | Verifique se o access_token informado foi gerado corretamente ou se possui permissões para executar a operação. |-| 401 |
| 120 | Sistema indisponível no momento. Tente novamente em instantes. |Não| Não | - | - |
| 122 | Bandeira não encontrada na base de configuração! |Não| Não | - | - |
| 123 | Quantidade de parcelas excedentes |Não| Não | - | - |
| 279 | Catálogo não permite a utilização de pagamento total no dinheiro! |-| Não | - | - |
| 289 | Há regras do carrinho que não foram atendidas. |Não| **Sim\*** | As regras são relativas a cada catalogo, parceiro ou campanha. Ou seja, pode ou não estar ativas e trazem esse especícico critério. Consulte as regras de sua campanha e seus respectivos catálogos e parceiros para conhecer quais regras considerar. | 422 |
| 312 | Uma tentativa de resgate com parametros nulos foi efetuada. |Não | Não | Erro ao executar um resgate, motivo: ausência dos parâmetros necessários.  | 400 |
| 313 | Uma tentativa de resgate inválida com cartão de crédito foi efetuada. |Não| Não|- | Não | Erro ao executar um resgate, motivo: os dados informados do cartão de crédito estão incorretos. | 422 |
| 314 | Uma tentativa de resgate sem informar o Canal foi efetuada. |Não| Não | Erro ao executar um resgate, motivo: o canal não foi informado ou está incorreto. | 422 |
| 315 | Uma tentativa de resgate foi efetuada, erros na validação de regras do carrinho. |Não| Não | Erro ao executar um resgate, motivo: há regras  do carrinho que não foram atendidadas. Para maiores informações, consulte **código 289**.  | 422 |
| 316 | O produto selecionado não é permitido para compras com o contexto informado. |Não| **Sim\*** | Erro ao executar um resgate em um contexto somente pontos ou somente dinheiro. __Consulte a regra "Somente Cash" / "Somente Pontos"__ Este erro ocorre pois um carrinho está inválido para o resgate. Neste caso é informado o contexto e o(s) skus envolvidos. | 422 |
| 317 | Uma tentativa de resgate foi efetuada, porém erros no cálculo de frete impediram a conclusão. |-| **Sim** | Erro ao executar um resgate, motivo: incoerência no cálculo de frete. | 422 |
| 318 | Uma tentativa de resgate foi efetuada, porém há divergência(s) no(s) item(s) - preço / estoque. |**Sim\***| Não | Erro ao executar um resgate, motivo: preço divergente ou item sem estoque.  | 422 |
| 319 | Uma tentativa de resgate foi efetuada, porém PointsValue é inválido. |Não| Não | Erro ao executar um resgate, motivo: quantidade insulficiente de Pontos | 422 |
| 320 | Uma tentativa de resgate foi efetuada, problemas com pontos e dinheiro (cash). |Não| Não | Erro com o valor dos pontos. | 422 |
| 321 | Uma tentativa de resgate foi efetuada, problemas com o saldo do participante. |Não| Não | Erro ao executar um resgate, motivo: problemas com o valor dos pontos ou do dinheiro (cash). | - |
| 322 | Encontramos dificuldades para realizar a operação. Entre em contato com o administrador do sistema. |Não| **Sim\*** | - | 422 |
| 323 | Uma tentativa de resgate foi efetuada, problemas apenas com dinheiro(cash). |Não| Não | Erro ao executar um resgate, motivo: incosistências dos dados. | 500 |
| 324 | Validando retorno do Banking, avaliando requisição para token. |Não| Não | Erro ao executar um resgate, motivo: problemas com o dinheiro (cash). | - |
| 325 | Não foi possível concluir {type} |**Sim\***| Não | Negado pela análise de risco. (Significa que o pedido tem algum dado em BLACKLIST, pedido em situação irreversível.) | 422 |
| 326 | Para sua segurança não foi possível concluir {type} |**Sim\***| Não | Rejeitado por infringir uma ou mais regra de rejeição global. (Significa que foi negado por alguma regra de bloqueio, por exemplo, valor ou quantidade. Sujeito a reversão ou liberação do pedido.) | 422 |
| 327 | Não foi possível concluir {type} |**Sim\***| Não | Pedido em análise externa. (Pedido esta em análise, essa mensagem não funciona hoje, por que não temos resgate offline no sonar ainda.) | 422 |
| 328 | Sua transferência {type} |**Sim\***| Não | Pedido rejeitado por análise externa. (Negado por analise externa, ou seja, fora do ambiente sonar, por exemplo a ClearSale não aprovou o pedido por causa dos dados de cartão de credito por exemplo. Sujeito a reversão ou liberação do pedido.) | 422 |
| 329 | Por questões de segurança, {type} |**Sim\***| Não | Rejeitado por análise de Score. SONAR | 422 |
| 330 | Para sua segurança não foi possível concluir a sua transação. |Não |Não| Erro genérico do Sonar, quando não foi informado o motivo real da recusa. | - |
| 331 | Não foi possível concluir a sua transação. |Não | Não| Erro genérico no fechamento de pedido | 422 |
| 332 | Você não tem pontos suficientes para fazer {type} |**Sim\***| Não | Saldo insuficiente do cliente | 422 |
| 333 | Não foi possível concluir a sua transação. Erro no pagamento |Não |Não| Erro Pontos + Cash- Erro de validação pontos com dinheiro | 422 |
| 334 | Não foi possível concluir a sua transação. Erro no pagamento |Não |Não| Erro Só Cash - Erro de validação pontos com dinheiro | 422 |
| 335 | Sua transação não foi autorizada. Vamos fazer uma nova tentativa? |**Sim\*** |Não| Cartão de crédito - Não Autorizada.  | 422 |
| 336 | Você excedeu o tempo limite para realizar essa compra |**Sim\*** |Não| Cartão de crédito. - Timed Out.  | 422 |
| 337 | Parece que seu cartão está cancelado |**Sim\*** |Não| Cartão de crédito- Cartão Cancelado.  | 422 |
| 338 | Problemas com o Cartão de Crédito |**Sim\*** |Não| Problemas com o Cartão de Crédito (#70) | 422 |
| 339 | Este cartão está bloqueado |**Sim\*** |Não|  Cartão de crédito - Cartão Bloqueado. | 422 |
| 340 | Este cartão está expirado Erro no pagamento |**Sim\*** |Não|  Cartão de crédito - Cartão Expirado.| 422 |


### * Tabela Sub Erros - Código 289

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| 1 | Insira no máximo 2 itens no carrinho para Magazine Luiza. | "Maximo de itens por parceiro": Os itens excederam a quantidade máxima total de produtos por compra permitida pelo parceiro. Ex: Quantidade Máxima 3 itens: 2 geladeiras, 2 fogões foi negado por exceder 3 itens. |
| 2 | Insira no máximo 2 itens no carrinho. | "Maximo de itens por sku e parceiro": A quantidade máxima para cada item por compra permitida pelo parceiro foi excedida, Ex: Quantidade Máxima 3 por item: 2 geladeiras, 2 fogões não foi negado por não exceder a quantidade por item. |
| 3 | O valor da compra não pode exceder R$x | "Valor máximo por parceiro": o valor total de itens de um mesmo parceiro foi excedido. |
| 4 | Não é permitido Magalu e outra loja na mesma compra | "Somente um supplier no carrinho": Apenas produtos de um mesmo parceiro é permitido por compra. |
| 5 | Compre no máximo 1 produto por loja | Somente um sku do supplier no carrinho: Apenas 1 unidade de um produto para um determinado parceiro. |
| 6 | Não aprovado pelas regras da promoção | Regras da avon no cluster: Apenas para cliente Avon, regra para cluster de usuários. |

### * Tabela Sub Erros - Código 313

| Código (Type) | Mensagem Exemplo (Message) | Descrição |
|-|-|-|
| 1 | Número do cartão não informado. | Ao validar os dados do cartão encontrou-se inconsistência nos dados do cartão infomado (Validação de entrada apenas) |
| 1 | Nome do titular do cartão não informado. | Ao validar os dados do cartão encontrou-se inconsistência nos dados do cartão infomado (Validação de entrada apenas) |
| 1 | Validade do cartão não informado. | Ao validar os dados do cartão encontrou-se inconsistência nos dados do cartão infomado (Validação de entrada apenas) |
| 1 | Bandeira do cartão não infomado. | Ao validar os dados do cartão encontrou-se inconsistência nos dados do cartão infomado (Validação de entrada apenas) |
| 1 | Validade do cartão não inválida. | Ao validar os dados do cartão encontrou-se inconsistência nos dados do cartão infomado (Validação de entrada apenas) |
| 1 | Numero do cartão inválido | Validação do cartão de crédito (Regex) |

### * Tabela Sub Erros - Código 316

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| 1 | 4785d50b21c64707adc3 | SKU do produto adicionado não permitido |
| 2 | Pontos/Cash | Tipo do contexto inválido(ponto ou dinheiro). |

### * Tabela SubMensagem - Código 318

| Sub Mensagem |
|-|
|Existem produtos que não possuem estoque disponível. Verifique produtos similares, pois temos muitas opções.|


### * Tabela Sub Erros - Código 317

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| -1 | Cep não disponível para a região | Erros no cálculo de frete, caráter informativo apenas, Erro genérico do parceiro. |
| -1 | Quantidade de itens excedeu o limite permitido | Erros no cálculo de frete, caráter informativo apenas, Erro genérico do parceiro. |



### * Tabela Sub Inconsistências - Código 322

| Código (Type) | Mensagem (Message) | Descrição |
|-|-|-|
| 1 | Valor do frete não foi informado. |  |
| 2 | Não há itens no pedido. |  |
| 3 | Valor do pedido é diferente do valor do produto mais o valor do frete. |  |
| 4 | Valor do pedido é diferente do valor dos pagamentos (Pontos + Complemento). |  |
| 5 | Valor do resgate menor que o valor do estorno. |  |
| 6 | Pedido sem participante válido. |  |
| 7 | Pedido sem fornecedor válido. |  |
| 8 | Pedido sem dados de entrega. |  |
| 9 | Quantidade de item inválida. |  |
| 11 | Dados de pagamento não fornecido. |  |
| 12 | Sku do produto inválido ou inexistente. |  |
| 13 | Preço de va do produto não fornecido. |  |
| 14 | Data prevista de entrega não fornecido. |  |
| 15 | Cpf ou Cnpj do participante não fornecido. |  |
| 16 | Email do participante não fornecido. |  |
| 17 | Tipo de pessoa do participante não fornecido. |  |
| 18 | Genêro não fornecido. |  |
| 19 | Nome do participante não fornecido. |  |
| 20 | Nome da empresa não fornecido. |  |
| 21 | Telefone não fornecido. |  |
| 22 | Nome do contato de entrega não fornecido. |  |
| 23 | Nome do endereço não fornecido. |  |
| 24 | Endereço não fornecido. |  |
| 25 | Número do endereço de entrega não fornecido. |  |
| 26 | Bairro do endereço não fornecido. |  |
| 27 | Cidade do endereço não fornecido. |  |
| 28 | Estado do endereço não fornecido. |  |
| 29 | Cep não fornecido ou inválido. |  |
| 30 | A quantidade máxima de produtos permitida é de até 9 itens. |  |
| 31 | A quantidade máxima do mesmo produto é de até 5 itens. |  |
| 32 | Ponto de Referência deve ter no mínimo 4 caracteres. |  |
| 33 | Informações como Operadora, DDD e número do celular não foram informados. |  |
| 34 | Número do endereço informado deve conter apenas números. |  |
| 35 | O pagamento só poderá ser realizado com até 2 dias de antecedência do vencimento do seu boleto |  |
| 36 | Os campos Nº do boleto, Data de Vencimento, CPF e Valor da conta são obrigatórios. |  |
| 37 | O horário permitido para pagamento é entre 8:00 e 21:00 e os dias da semana permitidos são Segunda, Terça, Quarta, Quinta e Sexta-Feira. |  |
| 38 | Ponto de Referência deve ter no máximo 100 caracteres. |  |
| 39 | Complemento deve ter no máximo 20 caracteres. |  |
| 40 | Número deve ter no máximo 5 caracteres para o parceiro Magazine Luiza. |  |
| 41 | Campo complemento obrigatório para esse parceiro, favor preencher (Ex.: Casa/Loja) |  |
| 42 | Complemento deve ter no máximo 100 caracteres. |  |
| 43 | Sobrenome do destinatário não fornecido. |  |
| 44 | Você já realizou um pagamento em menos de 24 horas. Aguarde o prazo para efetuar um novo pagamento |  |

### * Tabela Sub Mensagem e Type - Código 325
| Sub Mensagem |
|-|
|Entre em contato com a Central para que possamos confirmar algumas informações.|

| Type (Tipo de Fechamento) | Mensagem Exemplo | Descrição |
|-|-|-|
| DOAÇÕES | Não foi possível concluir essa transferência. | Negado pela análise de risco. (Significa que o pedido tem algum dado em BLACKLIST, pedido em situação irreversível.) |
| RECARGA DE CELULAR | Não foi possível concluir esse resgate. | Rejeitado por infringir uma ou mais regra de rejeição global. (Significa que foi negado por alguma regra de bloqueio, por exemplo, valor ou quantidade. Sujeito a reversão ou liberação do pedido.) |
| E-COMMERCE | Não foi possível concluir sua compra. | Pedido em análise de externa. (Pedido esta em analise, essa mensagem não funciona hoje, por que não temos resgate offline no sonar ainda.) |
| SHOPPING | Não foi possível concluir sua compra. | Pedido rejeitado por análise externa. (Negado por analise externa, ou seja, fora do ambiente sonar, por exemplo a ClearSale não aprovou o pedido por causa dos dados de cartão de credito por exemplo. Sujeito a reversão ou liberação do pedido).

### * Tabela SubMensagem - Código 326

| Sub Mensagem |
|-|
|Tente novamente mais tarde ou entre em contato com a Central.|

| Type (Tipo de Fechamento) | Mensagem Exemplo | Descrição |
|-|-|-|
| DOAÇÕES | Não foi possível concluir essa transferência. | Negado pela análise de risco. (Significa que o pedido tem algum dado em BLACKLIST, pedido em situação irreversível.) |
| RECARGA DE CELULAR | Não foi possível concluir esse resgate. | Rejeitado por infringir uma ou mais regra de rejeição global. (Significa que foi negado por alguma regra de bloqueio, por exemplo, valor ou quantidade. Sujeito a reversão ou liberação do pedido.) |
| E-COMMERCE | Não foi possível concluir sua compra. | Pedido em análise de externa. (Pedido esta em analise, essa mensagem não funciona hoje, por que não temos resgate offline no sonar ainda.) |
| SHOPPING | Não foi possível concluir sua compra. | Pedido rejeitado por análise externa. (Negado por analise externa, ou seja, fora do ambiente sonar, por exemplo a ClearSale não aprovou o pedido por causa dos dados de cartão de credito por exemplo. Sujeito a reversão ou liberação do pedido). |

### * Tabela SubMensagem - Código 327

| Sub Mensagem |
|-|
|Tente novamente mais tarde ou entre em contato com a Central.|

| Type (Tipo de Fechamento) | Mensagem Exemplo | Descrição |
|-|-|-|
| DOAÇÕES | Não foi possível concluir essa transferência. | Negado pela análise de risco. (Significa que o pedido tem algum dado em BLACKLIST, pedido em situação irreversível.) |
| RECARGA DE CELULAR | Não foi possível concluir esse resgate. | Rejeitado por infringir uma ou mais regra de rejeição global. (Significa que foi negado por alguma regra de bloqueio, por exemplo, valor ou quantidade. Sujeito a reversão ou liberação do pedido.) |
| E-COMMERCE | Não foi possível concluir sua compra. | Pedido em análise de externa. (Pedido esta em analise, essa mensagem não funciona hoje, por que não temos resgate offline no sonar ainda.) |
| SHOPPING | Não foi possível concluir sua compra. | Pedido rejeitado por análise externa. (Negado por analise externa, ou seja, fora do ambiente sonar, por exemplo a ClearSale não aprovou o pedido por causa dos dados de cartão de credito por exemplo. Sujeito a reversão ou liberação do pedido).

### * Tabela SubMensagem - Código 328

| Sub Mensagem |
|-|
|Tente novamente mais tarde ou entre em contato com a Central.|

| Type (Tipo de Fechamento) | Mensagem Exemplo | Descrição |
|-|-|-|
| DOAÇÕES | Não foi possível concluir essa transferência. | Negado pela análise de risco. (Significa que o pedido tem algum dado em BLACKLIST, pedido em situação irreversível.) |
| RECARGA DE CELULAR | Não foi possível concluir esse resgate. | Rejeitado por infringir uma ou mais regra de rejeição global. (Significa que foi negado por alguma regra de bloqueio, por exemplo, valor ou quantidade. Sujeito a reversão ou liberação do pedido.) |
| E-COMMERCE | Não foi possível concluir sua compra. | Pedido em análise de externa. (Pedido esta em analise, essa mensagem não funciona hoje, por que não temos resgate offline no sonar ainda.) |
| SHOPPING | Não foi possível concluir sua compra. | Pedido rejeitado por análise externa. (Negado por analise externa, ou seja, fora do ambiente sonar, por exemplo a ClearSale não aprovou o pedido por causa dos dados de cartão de credito por exemplo. Sujeito a reversão ou liberação do pedido).

### * Tabela SubMensagem - Código 329

| Sub Mensagem |
|-|
|Entre em contato com a central de atendimento para confirmar algumas informações. |

| Type (Tipo de Fechamento) | Mensagem Exemplo | Descrição |
|-|-|-|
| DOAÇÕES | Não foi possível concluir essa transferência. | Negado pela análise de risco. (Significa que o pedido tem algum dado em BLACKLIST, pedido em situação irreversível.) |
| RECARGA DE CELULAR | Não foi possível concluir esse resgate. | Rejeitado por infringir uma ou mais regra de rejeição global. (Significa que foi negado por alguma regra de bloqueio, por exemplo, valor ou quantidade. Sujeito a reversão ou liberação do pedido.) |
| E-COMMERCE | Não foi possível concluir sua compra. | Pedido em análise de externa. (Pedido esta em analise, essa mensagem não funciona hoje, por que não temos resgate offline no sonar ainda.) |
| SHOPPING | Não foi possível concluir sua compra. | Pedido rejeitado por análise externa. (Negado por analise externa, ou seja, fora do ambiente sonar, por exemplo a ClearSale não aprovou o pedido por causa dos dados de cartão de credito por exemplo. Sujeito a reversão ou liberação do pedido).

### * Tabela Sub Erros - Código 332

| Sub Mensagem* |
|-|
|Verifique o seu saldo de pontos e ajuste o valor desejado.|
***Não haverá Sub Mensagem para E-Commerce**

| Type (Tipo de Fechamento) | Mensagem Exemplo | Descrição |
|-|-|-|
| DOAÇÕES | Você não tem pontos suficientes para fazer essa transferência. | Saldo Insuficiente / Nâo tem saldo |
| RECARGA DE CELULAR |  Você não tem pontos suficientes para fazer esse resgate. | Saldo Insuficiente / Nâo tem saldo |
| MILHAS |  Você não tem pontos suficientes para fazer essa transferência. | Saldo Insuficiente / Nâo tem saldo
| E-COMMERCE | - | - |

### * Tabela SubMensagem - Código 326

| Sub Mensagem |
|-|
|Tente novamente mais tarde ou entre em contato com a Central.|

### * Tabela SubMensagem - Código 335

| Sub Mensagem |
|-|
|Verifique os dados do cartão ou tente com outro cartão.|

### * Tabela SubMensagem - Código 336

| Sub Mensagem |
|-|
|Recarregue a página e tente novamente.|

### * Tabela SubMensagem - Código 337

| Sub Mensagem |
|-|
|Tente com outro cartão.|

### * Tabela SubMensagem - Código 338

| Sub Mensagem |
|-|
|Verifique os dados do cartão ou tente com outro cartão.|

### * Tabela SubMensagem - Código 339

| Sub Mensagem |
|-|
|Tente com outro cartão.|

### * Tabela SubMensagem - Código 340

| Sub Mensagem |
|-|
|Tente com outro cartão. |

## Dicas de Uso

> Correlation Id: Utilize o parâmetro "X-Correlation-Id" para gerar uma correlação nos seus fluxos de sistema utilizando o CloudLoyalty.
[Saiba as vantagens acessando aqui.](/tips/readme.md)
