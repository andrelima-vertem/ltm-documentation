[Início](/readme.md) &raquo; Compras / Resgates &raquo; Qual o modelo de resgates adotar

# Qual o modelo de resgates adotar  

Um resgate é o resultado de um ação em que há de **um lado, o usuário com pontuação disponível (participante)** e do outro, um **fornecedor / parceiro** de um produto ou serviço para ser utilizado por uma campanha como benefício, recompensa ou premiação.

O participante escolhe que produto ou serviço que vai resgatar, um **débito é feito na conta-corrente (Account)** de origem da campanha, o valor do resgate é convertido e enviado como pagamento para o parceiro e o participante recebe o produto / serviço.

### Vendor (fornecedor ou parceiro)

Empresas parceiras que ofereçam produtos ou serviços como descritos acima, são donominadas: **parceiros (vendors)**.

**O CloudLoyalty** possui integrações com centenas de parceiros em diversos ramos de atividade como: varejo, promocional, entretenimento, moda, alimentação, viagens, pagamento de contas, recarga de celular, milhas, etc.

É um investimento feito para reduzir a complexidade e burocracia e que gerou uma vantagem competitiva.

A Ltm Fidelidade incorporou essa vantagem no portfólio do **CloudLoyalty.**

Clientes que utilizam o CloudLoyalty podem usufruir dessas integrações pois há contratos comerciais que credenciam a Ltm Fidelidade a atendê-los.

## Modelo 1 - Compra com carrinho LTM

Os resgates em parceiros do portfólio são **"Compras internas".**
Possuem o carrinho (cesta de compras) sob a gestão do **CloudLoyalty.**

### Fluxo genérico de uma compra com carrinho

![Simple Purchase Flow](/images/purchase-simple.svg)

### Fluxo efetuado pelo sistema para compra com carrinho.

![Internal Purchase Flow](/images/purchase-internal-diagram.svg)

## Modelo 2 - Authorize / Confirm (Apenas Débito no CloudLoyalty)

Neste caso o **CloudLoyalty** atua como uma carteira ou conta corrente de pontos.

Neste cenário os parceiros **não fazem parte** do portfólio do CloudLoyalty e as **"compras são feitas externamente".**

    O CloudLoyalty não efetua chamadas em fornecedores nos casos de compras externas, neste cenário o CloudLoyalty atua apenas como conta-corrente (Account). Ou seja só o débito e estorno dos pontos. É responsabilidade da aplicação cliente efetuar a compra do produto / servico no parceiro / fornecedor (Vendor).

    Isso aumenta a autonomia da aplicação cliente e abre a possibilidade de integrar com qualquer serviço desejado.

Para tal é necessário um código de vendor (vendor id), pois neste caso é criado um parceiro genérico para representar todos os resgates. O vendor é necessário para finalidades de conciliação e outros tramites administrativos.

### Segurança (Importante)

É requisito de segurança utilizar os endpoints de authorize e confirm encapsulados no backend do cliente.

**Diferente do fluxo com carrinho**, não é correto utilizar esse fluxo no frontend pelo fato de o backend do CloudLoyalty não possuir o controle do que está sendo vendido / debitado.

Todo o resgate no modelo **authorize e confirm** será permitido e fica a cargo do cliente fazer o controle do que é transacionado. Logo se isto está exposto no front-end o participante poderá autorizar e debitar, gerando problemas futuros para o próprio participante.

### Fluxo de Authorize e Confirm. Com cancelamento em caso de insucesso 

- Autorização de compra

  ![Authorize Purchase](/images/purchase-external-1-diagram.svg)

- Compra externa (Responsabilidade da aplicação cliente)
  - Não é um serviço do CloudLoyalty;
  - Pode ser vendido qualquer serviço ou produto terceiro;

  ![External Vendor](/images/purchase-external-2-diagram.svg)

- Confirmação de autorização

  ![Confirm Purchase](/images/purchase-external-3-diagram.svg)

- Cancelamento de autorização (não pode ter havido confirmação)

 ![Confirm Purchase](/images/purchase-external-4-diagram.svg)


## Próximos passos

[Compras - Tipos de autenticação](/purchase/auth.md)
