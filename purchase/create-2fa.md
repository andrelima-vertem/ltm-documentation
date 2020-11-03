[Início](/readme.md) &raquo; Compras / Resgates &raquo; Criar uma compra com 2FA (Two-factor Authentication)

# Two-factor Authentication (2FA)
O resgate de um produto ou serviço pode ser realizado utilizando a autenticação em duas etapas, que tem como objetivo aumentar a segurança dos participantes que realizam o resgate e das empresas envolvidas no processo, desde o cliente dono da campanha, parceiro que faz a entrega do produto final e a LTM que disponiliza as apis, a fim de evitar fraudes e ataques maliciosos à plataforma.

## 1. Configurações
A configuração do 2FA é realizada internamente pela LTM e é configurada por Campanha, então caso o cliente opte pela utilização da ferramenta, deve ser solicitado ao time da LTM a ativação e configuração na campanha.

## 2. Onboarding
Para a utilização dessa ferramenta deve ser implementado um fluxo de Onboarding que é responsável pelo cadastro do dispositivo de segurança que será utilizado pelo participante para efetuar a segunda autenticação, no caso a primeira é o login na plataforma, a segunda é um código que será enviado para esse dispositivo no momento de confirmação de resgate. Além do cadastro do dispositivo o participante deve fazer o envio de alguns documentos para a comprovação da sua identidade.

## 3. Processo de resgate
Caso a ferramenta do 2FA esteja ativa para o resgate/fechamento a api retornará solicitando a validação do token apresentando o número do dispositivo cadastrado para qual o token será enviado. em seguida deve-se chamar a api que confirma o token digitado/informado pelo participante.
Nos casos que o resgate não possui a ferramenta de 2FA ativa o processo de resgate se mantém o mesmo descrito na [página de resgate](/purchase/readme.md).

## 4. Dicionário de erros

| Código | Mensagem | Sub | Descrição | Http Status |
|-|-|-|-|-|
|11|O pagamento deste tipo de boleto só pode ser feito nos terminais de auto-atendimento.|Não||422|
|11|O telefone parece incorreto. Verifique e tente novamente.|Não||422|
|11|Não foi possível concluir o seu pedido. Tente novamente.|Não||422|


## Link da documentação no portal do desenvolvedor

 > https://portal.ltm.digital/docs/services/cloudloyalty-new-marketplace-api/operations/OrderCloudLoyalty_CreateOrderToken?&pattern=Valida%20o%20token%20na%20cria%C3%A7%C3%A3o%20da%20ordem


## Dicas de Uso

> Correlation Id: Utilize o parâmetro "X-Correlation-Id" para gerar uma correlação nos seus fluxos de sistema utilizando o CloudLoyalty.
[Saiba as vantagens acessando aqui.](/tips/readme.md)
