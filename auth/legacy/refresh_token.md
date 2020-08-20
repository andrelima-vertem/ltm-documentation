## Introdução ao Refresh Token

Os access token tem um tempo definido de duração, após esse tempo o access token torna-se inválido sendo necessário a geração de um novo token, essa informação é retornada junto ao access token. 
O expires_in é um número que representa quantos segundos o access token tem de duração. 
Para facilitar a renovação do access token e para uma melhor experiência do usuário pode ser adotado o método de refresh token, tornando desnecessário que o usuário ou a aplicação cliente informe as credenciais novamente.

## How It Works

### Refresh Token

- A aplicação cliente gera um token acessando normalmente o endpoint padrão (/token), porém informando um parâmetro chamado refresh_token_active com valor booleano true:

	- grant_type - fluxo que deseja ser utilizado, pode ser o "password"
	- campaign_id - id da campanha do cliente
	- username - username do usuário do qual se deseja obter autenticação 
	- password - password do usuário do qual se deseja obter autenticação 
	- refresh_token_active - para ativar o fluxo de refresh token deve informar o valor true, qualquer outro valor ou a falta do parâmetro não ativa o fluxo
	
	- OBS: No header da requisição é necessário informar o authorization basic passando o base64 do clientid:clientsecret e o content-type é o application/x-www-form-urlencoded

	- Exemplo de curl:
		curl --location --request POST 'http://marketplace-api.webpremios.com.br/token' \
		--header 'Authorization: Basic {base64 do clientid:clientsecret}' \
		--header 'Content-Type: application/x-www-form-urlencoded' \
		--data-urlencode 'username={username}' \
		--data-urlencode 'password={password}' \
		--data-urlencode 'grant_type=password' \
		--data-urlencode 'campaign_id={id da campanha}' \
		--data-urlencode 'refresh_token_active=true'
  
- Ao informar o parâmetro a api retornará um refresh token válido, que de preferência deve ser armazenado / controlado pela aplicação cliente, pois futuramente será necessário para renovação do access token.

	- O objeto retornado terá um formato:
	{
		"access_token": {token}, 
		"token_type": "bearer",
		"expires_in": 3599,
		"refresh_token": {refresh_token},
		"authorization_id": {authorization_id},
		"participant_id": {participant_id},
		"catalog_id": {catalog_id},
		"catalog_id": {catalog_id},
		"scopes": "scope_1, scope_2, scopr_3",
		"campaign_id": {campaign_id},
		"home_uri": "/",
		"name": "Usuário Teste",
		".issued": "Wed, 12 Aug 2020 13:51:00 GMT",
		".expires": "Wed, 12 Aug 2020 14:51:00 GMT"
	}
	
- Quando o access token atual expira, pode-se fazer uma chamada a api no endpoint padrão (/token), passando os paramêtros grant_type = refresh_token e refresh_token = { refresh token armazenado }. 

	- grant_type - fluxo informado deve ser o "refresh_token"
	- refresh_token - deve ser o refresh_token devolvido na requisição feita para obtenção do access token

	- OBS: No header da requisição é necessário informar o authorization basic passando o base64 do clientid:clientsecret e o content-type é o application/x-www-form-urlencoded

	- Exemplo de curl:
		curl --location --request POST 'http://marketplace-api.webpremios.com.br/token' \
		--header 'Authorization: Basic {base64 do clientid:clientsecret}' \
		--header 'Content-Type: application/x-www-form-urlencoded' \
		--data-urlencode 'refresh_token=88642e36-ef83-49fe-baf9-40afda247059' \
		--data-urlencode 'grant_type=refresh_token'

- A api irá validar se o refresh token é valido e caso seja irá retornar um novo access token e um novo refresh token que deve ser armazenado para futuras renovações.

	- O objeto retornado terá um formato:
	{
		"access_token": {token}, 
		"token_type": "bearer",
		"expires_in": 3599,
		"refresh_token": {refresh_token},
		"authorization_id": {authorization_id},
		"participant_id": {participant_id},
		"catalog_id": {catalog_id},
		"catalog_id": {catalog_id},
		"scopes": "scope_1, scope_2, scopr_3",
		"campaign_id": {campaign_id},
		"home_uri": "/",
		"name": "Usuário Teste",
		".issued": "Wed, 12 Aug 2020 14:52:00 GMT",
		".expires": "Wed, 12 Aug 2020 15:52:00 GMT"
	}

- Caso o refresh token seja inválido a api irá retornar o erro "invalid_grant".

	- O objeto retornado terá um formato:
	{
		"error": "invalid_grant"
	}

- **Importante ressaltar que mesmo que o parâmetro refresh_token_active não seja informado a api irá devolver um refresh token, porém esse será inválido para renovações de token.
