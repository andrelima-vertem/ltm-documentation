[Início](/readme.md) &raquo; Carrinho &raquo; Calcular o Frete para um carrinho

# Adicionar / Alterar endereço de entrega no carrinho

Recurso utilizado para calcular o frete do carrinho baseado em um CEP (Token de acesso do tipo Participante)

## Link da documentação no portal do desenvolvedor

> https://portal.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/CartCloudLoyalty_CalculateFreight?&tags=Carrinho

## Dicionário de Erros

| Código | Mensagem | Sub | Descrição | Http Status |
|-|-|-|-|-|
| 70 | Infelizmente não podemos entregar os produtos destes parceiros no mesmo pedido, mas você pode fazer um novo pedido para cada um dos parceiros. |  **\*Sim** | Ocorre quando não foi possível calcular o frete de um carrinho. Lembrando que um carrinho pode haver mais de um parceiro. Sendo assim, no retorno é apresentado o detalhe do parceiro que ocorreu o erro. Atenção: o parâmetro sub pode contar tipos duplicados duplicados, em caso de carrinho com mais de um parceiro isso é possível. | 422 |
| 77 | Problemas internos: O carrinho está vazio. | Não | Por algum motivo o carrinho se encontra vazio no momento da validação dos dados. Deve-se incluir um produto no carrinho e caso o erro persista, reportar como um item crítico. | 422 |
| 103 | Não é possível realizar esta operação. (Tipo de token inválido.) | Não | Verifique se o access_token informado foi gerado corretamente ou se possui permissões para executar a operação. | 401 |
| **131** | Não conseguimos calcular o frete. Seu CEP pode estar digitado errado ou nosso parceiro não atende à sua região. | Não | Trata-se de um dos erros mais comuns no cálculo de frete. Ocorre quando um parceiro não entrega o produto em uma determinada região ou se o produto não consta mais no estoque do parceiro. *Importante.* | **404** |
| 271 | Produto(s) não encontrado(s)! | Não | Os dados informados sobre o produto não são válidos, verifique o código do sku / produto. | 422 |
| 290 | Não foi possível calcular o frete. | **\*Sim** | O CloudLoyalty viabiliza um canal de comunicação para o parceiro apresentar os erros diretamente ao usuário. O código 290 é meio que será apresentado um erro oriundo do parceiro para regras mais genéricas. O nosso sub conterá apenas o encadeamento de informações. O Sub não contêm o tipo. | 422 |

### * Tabela Sub Erros - Código 70

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| 1 | 62 | Apresenta o código do parceiro que apresentou o erro. Atenção este código pode vir em duplicidade na resposta. |
| 2 | Magazine Luiza | Apresenta o nome do parceiro que apresentou o erro. Atenção este código pode vir em duplicidade na resposta. |
| 3 | [\"3de7e58205c94d1a9936\"] | Trata-se de uma matriz deserialidada (JSON) com os códigos dos skus envolvidos para cada parceiro. Atenção este código pode vir em duplicidade na resposta.|
| 4 | [\"Teclado Numérico 5+ 015-0041 USB ABNT2 Preto\"] | Trata-se de uma matriz deserialidada (JSON) com os nomes dos skus envolvidos para cada parceiro. Atenção este código pode vir em duplicidade na resposta. |

### * Tabela Sub Erros - Código 290

| Código | Mensagem Exemplo | Descrição |
|-|-|-|
| -1, -1, ... | Produto não disponível, Magazine Luiza, ... | Apresenta uma cadeia de informações alphanuméricas que ou devem ser apresentadas ou para fins de logs na aplicação cliente. O CloudLoyalty sempre vai apresentar o nome do parceiro que apresentou a mensagem em uma das cadeias. |

## Dicas de Uso

> Correlation Id: Utilize o parâmetro "X-Correlation-Id" para gerar uma correlação nos seus fluxos de sistema utilizando o CloudLoyalty.
[Saiba as vantagens acessando aqui.](/tips/readme.md)