[Início](/readme.md) &raquo; Dicas de Uso CloldLoyalty

# Consumo de Apis

## Correlation Id

Os logs do CloudLoyalty seguem as boas práticas recomentadas do Twelve-Factor para arquiteturas com padrões para Cloud e Microsserviços.

É possível conhecer melhor da prática de uso do **Correlation Id** nos artigos:

> ["The Value of Correlation IDs"](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/). Rapid7 Blog. December 23, 2016. Retrieved April 13, 2018.

> Hilton, Peter. ["Correlation IDs for microservices architectures - Peter Hilton".](https://hilton.org.uk/blog/microservices-correlation-id) hilton.org.uk. Retrieved April 13, 2018.

O parâmetro **"X-Correlation-Id"** permite encadear as requisições correlacionando-as.
Assim um conjunto de requisições ou um fluxo passa a possuir o ciclo e a ordem utilizada até chegar no seu resultado.

Isto ajuda a entender certos cenários até a detecção de uma anomalia.

### Cabeçalho da Requisição

Para que isto ocorra basta enviá-lo na requisição do serviço com o valor desejado.
O CloudLoyalty armazena no ciclo de vida da mesma e a utiliza em logs e trace.

> Exemplo de uma requisição utilizando o parâmetro "X-Correlation-ID

    curl -v -X GET "https://api.ltm.digital/cloudloyalty/v1/carts/me"
    -H "Authorization: Bearer xxx..."
    -H "X-Correlation-Id: 26a2005b-4474-42c9-b47b-2a56e6f9d97c"
    -H "Ocp-Apim-Subscription-Key: {subscription key}"

### Cabeçalho de Resposta

Por padrão o CloudLoyalty retorna o parâmetro "X-Correlation-Id nos cabeçalhos de resposta de todas as requisições. Se o parametro foi informado na requisição será o mesmo valor retornado na resposta.

Ex:

![Authorize Purchase](/images/curl-x-correlation.jpg)

### Filas, CQRS, Sagas e eventos

É comum em arquiteturas baseadas em microsserviços, o uso do parâmetro "X-Correlation-Id" para viabilizar o trace de um processo entre seus serviços. 

O dado é enviado de evento a evento. Você pode implementar sua aplicação para enviar o parametro para um sistema de mensageria, sagas e etc.

O CloudLoyalty viabiliza essa abordagem pois viabiliza o uso tanto na entrada quando na saída de seus processos. Com isso qualquer aplicação pode correlacionar dados, seja ela interna ou externa ao CloudLoylayt.

Saiba mais sobre o parâmetro no [Wikpedia, clicando aqui.](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#cite_note-42)
