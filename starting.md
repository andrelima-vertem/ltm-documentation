[Início](/readme.md) &raquo; Antes de começar

# Antes de começar, é preciso saber

### **O que preciso para iniciar minha integração?**

Para começar sua integração é importante conhecer não só a mecânica de um programa de fidelidade / premiação da <a href="https://vertem.com" target="_blank">**LTM Fidelidade**</a>, mas também como seu produto ou serviço deve ser integrado ao nosso negócio (**LTM CloudLoyalty**).
Nosso objetivo aqui é guiá-lo assertivamente para agregar o máximo de valor ao seu trabalho, de sua empresa e principalmente na melhor experiência para seus clientes.

**LTM Fidelidade** é uma empresa da holding <a href="https://vertem.com" target="_blank">**Vertem.**</a>

### Perfis:

Os perfis de empresas ou times que usufruem dessa documentação são alguns, abaixo os perfis mais comuns de times que utilizam essa documentação.
Tais perfis deverão encontrar aqui o que precisam para desenvolver uma integração técnica.

- Agências de publicidade

  - Agências de publicidade que queiram implantar um catálogo de prêmios próprio para seus clientes utilizando as apis da **LTM CloudLoyalty**.

- Parceiro de um cliente da Vertem
  - Um parceiro de um cliente geralmente já fornece serviços específicos e necessitam utilizar a conta corrente do cliente para autorizar e confirmar resgates.
- Times internos da Vertem
  - Times internos (B2B2C) que precisem integrar plataformas administrativas, hotsites ou consumir informações em uma aplicação back-end.
- Parceiro estratégico da Vertem
  - É um parceiro que estratégicamente deve estar presente em catálogo(s) de **um ou mais** clientes da Vertem.
  - Suas aplicações possuem uma integração **multitenant** mais robusta e são capazes de atender qualquer nicho de negócio de loyalty (fidelidade).
- Outros departamentos de um cliente da Vertem
  - Outros departamentos/empresas que necessitem desenvolver uma integração em um produto interno do cliente, seja o responsável pelo catálogo de prêmios ou representem um subproduto.

Os perfis acima possuirão fluxos específicos listados nessa documentação, é importante um alinhamento prévio com o corpo técnico da LTM para melhor andamento.

> Se o seu perfil ou de sua empresa não aparece aqui, consulte nosso time técnico para entendermos melhor a sua necessidade. [Entre em Contato.](http://cloudloyalty.com.br/)

Temos ainda (nos próximos capítulos ou no [sumário](/readme.md)) um descritivo para auxiliá-lo a definir o modelo ideal de autenticação para o seu negócio. **Link:** [Qual fluxo de autenticação devo escolher?]()

# Subscription

Um subscription é uma credencial válida para sua aplicação iniciar as integrações e estar apto para consumir nossas apis.

O primeiro passo para obter sua subscrição é tornar-se um membro do [**CloudLoyalty.**](http://cloudloyalty.com.br/)

O **CloudLoyalty** é uma solução para atender os perfis listados acima com uma linguagem única, documentação padronizada e fluxos unificados independente da solução interna dentro da Vertem.

A Vertem possui um ecossistema orientado a **Squads ágeis**, o CloudLoyalty é onde todas as soluções convergem para desenvolver uma linguagem única perante o cliente.

**O time técnico da LTM Fidelidade** será responsável por fazer a ativação da sua subscrição.
A subscrição é o primeiro passo e informações posteriores a isso deverão ser fornecidas pela **LTM Fidelidade.**

Para criar sua subscrição [acesse aqui.](https://portal.ltm.digital/signin)

Para conhecer mais do [**CloudLoyalty** clique aqui.](http://cloudloyalty.com.br/)

## Acesso ao portal do desenvolvedor

Ao obter a ativação de sua subscrição, você estará apto a acessar a documentação técnica dos endpoints de nossas apis.
Tal documentação técnica encontra-se em nosso [**portal do desenvolvedor.**](https://portal.ltm.digital/)

Lá você encontra uma documentação técnica com o detalhamento de cada endpoint e seus respectivos requests, responses, mensagens de erro, códigos de resposta, dicionário de DTOs, etc.

Lá também você faz a gestão de sua **subscription key.**

### Subscription-key

A subscription-key é uma credencial alpha-numérica, não segura, obrigatória para permitir o acesso de sua aplicação às apis do marketplace.

Essa informação deverá ser enviada no cabeçalho da requisição (header), no parâmetro "Ocp-Apim-Subscription-Key"

Exemplo de uma request com subscription:

> curl --location --request GET 'https://cloudloyalty-host.com/v1/participants/me' \
> --header 'Ocp-Apim-Subscription-Key: your-key-here' \
> --header 'Authorization: Bearer XXX'

No painel do desenvolvedor é feita a gestão da subscrição do cliente. Para acessar, escolha a opção "Profile" em seu menu de usuário.

Ilustração:

> ![CLient Credentials Flow](/images/sub-key.png)

<br />

## Primeiros passos, informações que deverão ser fornecidas por LTM Fidelidade:

# User Acceptance Test Environment (UAT)

Para iniciar as intregrações possuímos um ambiente de homologação para clientes.
Nessa ambiente os resgates são apenas simulações, não gerando um resgate real nos parceiros da ltm ou na conta corrente do cliente.

Este ambiente contém além da api, monitoria 24H, catálogo de prêmios (front-end), user pool (identity server) de homologação e conta-corrente de testes para débitos e créditos de pontuação.

Os dados desse ambiente são fornecidos após as configurações do **Tenant Id**.

## URL para testes

Uma url de testes para as chamadas das apis.

# Tenant-Id / Campanha

O Tenant-Id é o código da campanha/catálogo de prêmios do cliente.
É o tenant-id que define as regras de CPP(Custo por ponto), proprietários (CNPJs do cliente), segmentos, customizações e origem dos pontos.

O Tenant-Id é vinculado a um **user-pool do Amazon Cognito**. Cada **tenant (campanha)** possui um user-pool diferenciado, com infraestrutura pópria e o credenciamento específico.

> Obs. Tenant-Id pode variar dependendo do ambiente (ex. UAT, Production), portanto deve-se evitar utilizá-lo como dado fixo.

## Credenciamento do Tenant

Cada um dos tópicos listados abaixo tem utilidade apenas para um **único user-pool e consequêntemente para um único Tenant.**

### Segmentação (Catálogos)

A segmentação é o que torna capaz uma campanha atender diversos segmentos de clientes finais.
É possivel atribuir um CPP, markup de produtos, etc.

Cada segmento possui um **Id** que deve retornar no token de acesso do participante (usuário final).
Em cenários que não há token de usuário, esses dados devem ser recuperados previamente como descrito no capítulo [**"Participante > Client Credentials."**]()

- Exemplo de seguimentação: Black, Platinnum, Ouro, Prata.

> Obs. Segmentos podem variar dependendo do ambiente (ex. UAT, Production), portanto deve-se evitar utilizá-los como dado fixo.

### Login para testes

No período de desenvolvimento, é fornecido credenciais de participantes-teste para simulações.
Essa informação contempla aplicações cliente que utilizarem o fluxo de Single Sign On / Authorization Code.

### Discovery Endpoint

O CloudLoyalty Identity Server expõe documentos de descoberta do OIDC (**https://auth.tenant-demo.webpremios.digital/.well-known/openid-configuration**). Estes podem ser usados para configurar aplicativos automaticamente.

Nos próximos capítulos detalharemos mais essa informação.
[Clique Aqui caso queira acessar agora.](/auth/cognito/well-known.md)

### Client Id

Id da aplicação cliente, dado alphanumérico. Dado público.

### Client Secret

Chave Secreta para uso no backend da sua aplicação.
Esse dado não pode ser público, deve ser protegido.

### Permited Scopes

- Fluxo Client Credentials
  - _webpremios.campaigns/{tenant-id}_
  - _webpremios.backoffice/all.read_
  - _webpremios.backoffice/all.write/_
- Fluxo SSO
  - _openid_
  - _profile_
  - _email_
  - _webpremios.campaigns/{tenant-id}_

### Callback URIs

URLs de redirect para o aplicativo cliente.

### SignOut URIs

Urls de logout para o aplicativo do cliente.

# Vendor Id

Informação útil apenas para integrações de parceiros que possuem compras externas.

Código do parceiro para efetivação de compras externas.

Para saber mais acesse:

[Qual o modelo de resgates devo adotar?](/purchase/auth.md)

# Parceiros de Serviços

Parceiros estratégicos da **Vertem** que pretendem atuar em diversas campanhas dos clientes possuirão mais de 1(um) tenant de integração.
Portanto suas aplicações devem suportar o endereçamento de diversos tenants

## Sugestões de domínio

Os sugestões de domínio remetem a um padrão multitenant com marcação específica do tenant em contexto.

- https://your-app-domain.com/9999 - (tenant-id)
- https://99999.your-app-domain.com

# Considerações finais

Ao fim da integração serão enviados os dados definitivos para o ambiente de produção.

Tais dados podem variar e recomendamos que sejam armazenadas em padrões como: varáveis de ambiente, chaves de aplicação, etc.
Evite a utilização desses dados fixos para evitar a necessidade de refatoração.

# Próximos passos

[Nova Integração de Autenticação (Single Sign On)](/auth/cognito/readme.md)
