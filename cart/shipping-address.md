[Início](/readme.md) &raquo; Carrinho &raquo; Endereço de entrega no carrinho

# Adicionar / Alterar endereço de entrega no carrinho

Recurso utilizado para adicionar ou alterar um endereço de entrega na cesta de compras.

## Link da documentação no portal do desenvolvedor

> https://portal.ltm.digital/docs/services/cloud-loyalty-marketplace-api/operations/CartCloudLoyalty_UpdateShippingAddress?&tags=Carrinho

## Dicionário de Erros

| Código | Mensagem | Sub | Descrição | Http Status |
|-|-|-|-|-|
| 77 | Problemas internos: O carrinho está vazio. | Não | Por algum motivo o carrinho se encontra vazio no momento da validação dos dados. Deve-se incluir um produto no carrinho e caso o erro persista, reportar como um item crítico. | 422 |
| 103 | Não é possível realizar esta operação. (Tipo de token inválido.) | Não | Verifique se o access_token informado foi gerado corretamente ou se possui permissões para executar a operação. | 401 |
| 291| Não recebemos seus dados de endereço. Por favor, verifique sua requisição. | Não | - | 422 |
| 292 | O Cliente é obrigatório. Por favor, verifique o parâmetro customer. | Não | - | 422 |
| 293 | O Campo Nome é obrigatório. Por favor, verifique o parâmetro customer. | Não | - | 422 |
| 294 | O Campo Nome é inválido. Por favor, verifique o parâmetro customer. | Não | - | 422 |
| 295 | O Campo Data de nascimento é inválido. | Não | - | 422 |
| 296 | O Campo Gênero é inválido. | Não | - | 422 |
| 297 | O Campo Tipo Pessoa é inválido. | Não | - | 422 |
| 298 | O Campo Documento é inválido. | Não | - | 422 |
| 299 | O Campo CEP é inválido. | Não | - | 422 |
| 300 | O Campo Estado é inválido. | Não | - | 422 |
| 301 | O Campo Rua é obrigatório. | Não | - | 422 |
| 302 | O Campo Rua precisa conter entre 3 e 100 caracteres. | Não | - | 422 |
| 303 | O Campo Bairro é obrigatório. | Não | - | 422 |
| 304 | O Campo Bairro precisa conter entre 3 e 100 caracteres. | Não | - | 422 |
| 305 | O Campo Cidade é obrigatório. | Não | - | 422 |
| 306 | O Campo Cidade precisa conter entre 3 e 100 caracteres. | Não | - | 422 |
| 307 | O Campo Complemento é inválido. | Não | - | 422 |
| 308 | O Campo Número precisa conter menos de 50 caracteres. | Não | - | 422 |
| 309 | O Campo Telefone é inválido. |  Não | - | 422 |
| 310 | O Campo Tipo Telefone é inválido. | Não | - | 422 |
| 311 | O Campo Email é inválido. | Não | - | 422 |