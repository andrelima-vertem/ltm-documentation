[Início](/readme.md) &raquo; Compras / Resgates &raquo; Qual o modelo de resgates adotar

# Qual o modelo de resgates adotar

## Resgate de pontos

Um resgate é o resultado de um ação em que há, de **um lado o usuário com pontuação disponível (participante)** e do outro, um **fornecedor / parceiro** de um produto ou serviço para ser utilizado por uma campanha como benefício, recompensa ou premiação.

O participante escolhe que produto ou serviço que vai resgatar, um **débito é feito na conta-corrente (Account)** de origem da campanha, o valor do resgate é convertido e enviado como pagamento para o parceiro e o participante recebe o produto / serviço.

## Fluxo genérico de um resgate

![Purchase Flow](/images/purchase-diagram.svg)

## Vendor (fornecedor ou parceiro)

Empresas parceiras que ofereçam produtos ou serviços como descritos acima, são donominadas: **parceiros (vendors)**.

**O CloudLoyalty** possui integrações com centenas de parceiros em diversos ramos de atividade como: varejo, promocional, entretenimento, moda, alimentação, viagens, pagamento de contas, recarga de celular, milhas, etc.

É um investimento feito para reduzir a complexidade e burocracia e que gerou uma vantagem competitiva.

A Ltm Fidelidade incorporou essa vantagem no portfólio do **CloudLoyalty.**

Clientes que utilizam o CloudLoyalty podem usufruir dessas integrações pois há contratos comerciais que credenciam a Ltm Fidelidade a atendê-los.

## Compras (Resgate)

Os resgates em parceiros do portfólio são **"Compras internas".**

### How it works

![Internal Purchase Flow](/images/purchase-internal-diagram.svg)

## Débito de Pontos (Authorize / Confirm)

Neste caso o **CloudLoyalty** atua como uma carteira ou conta corrente de pontos.

Neste cenário os parceiros **não fazem parte** do portfólio do CloudLoyalty e as **"compras são feitas externamente".**

    O CloudLoyalty não efetua chamadas em fornecedores nos casos de compras externas, neste cenário o CloudLoyalty atua apenas como conta-corrente (Account). Ou seja só o débito e estorno dos pontos. É responsabilidade da aplicação cliente efetuar a compra do produto / servico no parceiro / fornecedor (Vendor).

    Isso aumenta a autonomia da aplicação cliente e abre a possibilidade de integrar com qualquer serviço desejado.

Para tal é necessário um código de vendor (vendor id), pois neste caso é criado um parceiro genérico para representar todos os resgates. O vendor é necessário para finalidades de conciliação e outros tramites administrativos.

### How it works

- Autorização de compra

  ![Authorize Purchase](/images/purchase-external-1-diagram.svg)

- Compra externa (Responsabilidade da aplicação cliente)

  ![External Vendor](/images/purchase-external-2-diagram.svg)

- Confirmação de compra

  ![Confirm Purchase](/images/purchase-external-3-diagram.svg)

## Próximos passos

[Compras - Tipos de autenticação](/purchase/auth.md)
