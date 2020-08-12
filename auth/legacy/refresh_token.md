## Introdu��o ao Refresh Token

Os access token tem um tempo definido de dura��o, ap�s esse tempo o access token torna-se inv�lido sendo necess�rio a gera��o de um novo token, essa informa��o � retornada junto ao access token. 
O expires_in � um n�mero que representa quantos segundos o access token tem de dura��o. 
Para facilitar a renova��o do access token e para uma melhor experi�ncia do usu�rio pode ser adotado o m�todo de refresh token, tornando desnecess�rio que o usu�rio ou a aplica��o cliente informe as credenciais novamente.

## How It Works

![Refresh Token]

- A aplica��o cliente gera um token acessando normalmente o endpoint padr�o (/token), por�m informando um par�metro chamado refresh_token_active com valor booleano true:

	- grant_type - fluxo que deseja ser utilizado, pode ser o "password"
	- campaign_id - id da campanha do cliente
	- username - username do usu�rio do qual se deseja obter autentica��o 
	- password - password do usu�rio do qual se deseja obter autentica��o 
	- refresh_token_active - para ativar o fluxo de refresh token deve informar o valor true, qualquer outro valor ou a falta do par�metro n�o ativa o fluxo
	
	- OBS: No header da requisi��o � necess�rio informar o authorization basic passando o base64 do clientid:clientsecret e o content-type � o application/x-www-form-urlencoded

	- Exemplo de curl:
		curl --location --request POST 'http://marketplace-api.webpremios.com.br/token' \
		--header 'Authorization: Basic {base64 do clientid:clientsecret}' \
		--header 'Content-Type: application/x-www-form-urlencoded' \
		--data-urlencode 'username={username}' \
		--data-urlencode 'password={password}' \
		--data-urlencode 'grant_type=password' \
		--data-urlencode 'campaign_id={id da campanha}' \
		--data-urlencode 'refresh_token_active=true'
  
- Ao informar o par�metro a api retornar� um refresh token v�lido, que de prefer�ncia deve ser armazenado / controlado pela aplica��o cliente, pois futuramente ser� necess�rio para renova��o do access token.

	- O objeto retornado ter� um formato:
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
		"name": "Usu�rio Teste",
		".issued": "Wed, 12 Aug 2020 13:51:00 GMT",
		".expires": "Wed, 12 Aug 2020 14:51:00 GMT"
	}
	
- Quando o access token atual expira, pode-se fazer uma chamada a api no endpoint padr�o (/token), passando os param�tros grant_type = refresh_token e refresh_token = { refresh token armazenado }. 

	- grant_type - fluxo informado deve ser o "refresh_token"
	- refresh_token - deve ser o refresh_token devolvido na requisi��o feita para obten��o do access token

	- OBS: No header da requisi��o � necess�rio informar o authorization basic passando o base64 do clientid:clientsecret e o content-type � o application/x-www-form-urlencoded

	- Exemplo de curl:
		curl --location --request POST 'http://marketplace-api.webpremios.com.br/token' \
		--header 'Authorization: Basic {base64 do clientid:clientsecret}' \
		--header 'Content-Type: application/x-www-form-urlencoded' \
		--data-urlencode 'refresh_token=88642e36-ef83-49fe-baf9-40afda247059' \
		--data-urlencode 'grant_type=refresh_token'

- A api ir� validar se o refresh token � valido e caso seja ir� retornar um novo access token e um novo refresh token que deve ser armazenado para futuras renova��es.

	- O objeto retornado ter� um formato:
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
		"name": "Usu�rio Teste",
		".issued": "Wed, 12 Aug 2020 14:52:00 GMT",
		".expires": "Wed, 12 Aug 2020 15:52:00 GMT"
	}

- Caso o refresh token seja inv�lido a api ir� retornar o erro "invalid_grant".

	- O objeto retornado ter� um formato:
	{
		"error": "invalid_grant"
	}

- **Importante ressaltar que mesmo que o par�metro refresh_token_active n�o seja informado a api ir� devolver um refresh token, por�m esse ser� inv�lido para renova��es de token.