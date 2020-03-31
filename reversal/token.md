[Início](/readme.md) &raquo; Estorno &raquo; Estorno parcial &raquo; [token](/purchase/token.md)
# Token
As requests para geração de token, são realizadas como visto abaixo:

<code>curl --location --request POST 'https://login.microsoftonline.com/grupoltm.com.br/oauth2/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'client_id=XXXXXXX-XXXXXX-XXXXXXXX-XXXXXXX' \
--data-urlencode 'scope=XXXXXXXXXXXXXXXX' \
--data-urlencode 'client_secret=XXXXXXXXXXXXXXX' \
--data-urlencode 'grant_type=client_credentials'</code>

Os campos do post client_id, scope e client_secret terão que ser pedidos para a equipe de cofiguração responsável, poi por se tratar de informações sensíveis não podemos ceder em domínio aberto.
  
## Próximos passos

[Extorno Total](/reversal/total.md)