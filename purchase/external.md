## Compras externas (Resgate)

Os resgates em parceiros que **não aparecem** no portfólio são denominados **"Compras externas".**

Para entender melhor o portfólio de parceiros acesse:
[Qual o modelo de resgates devo adotar?](/purchase/readme.md)

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

[Authorização de compra](/purchase/authorize.md)
