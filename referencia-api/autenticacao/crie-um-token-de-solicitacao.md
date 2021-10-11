# Criando Token OAuth2

Para Autenticar na API do Desko, utilizamos o fluxo OAuth client_credential

O fluxo de credenciais do cliente é um fluxo de servidor para servidor. Não há autenticação de usuário envolvida no processo. 

Este fluxo é útil para sistemas que precisam executar operações de API quando nenhum usuário está presente. Podem ser operações noturnas ou outras que envolvam o contato de entre duas aplicações / sistemas

O Fluxo consiste em:

1. Fazer uma solicitação POST ao servidor OAuth
2. O servidor OAuth emite o Token de Acesso
3. Utilizar este Token de Acesso para o consumo da API

####  <a href="benefit" id="benefit"></a>

{% swagger baseUrl="https://api.desko.com.br" path="/v1.1/oauth/token" method="post" summary="Autenticar (Client API)" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="grant_type" type="object" %}
client_credentials
{% endswagger-parameter %}

{% swagger-parameter in="body" name="client_id" type="string" %}
ID do Cliente Da Aplicação
{% endswagger-parameter %}

{% swagger-parameter in="body" name="client_secret" type="string" %}
Secret do Cliente da Aplicação
{% endswagger-parameter %}

{% swagger-parameter in="body" name="scope" type="string" %}
Escopos que o cliente está solicitando acesso
{% endswagger-parameter %}

{% swagger-response status="200" description="Retorna JSON contendo o access_token JWT que deverá ser utilizado no Header Bearer Token nas requisições da API" %}
```bash
{
    "token_type": "Bearer",
    "expires_in": 3600,
    "access_token": "eyJ...yqU"
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Erro nas credenciais de acesso para gerar Token JWT" %}
```bash
{
    "error": 401,
    "id": "oauth_server",
    "message": "Client authentication failed"
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request POST 'https://api.desko.com.br/v1.1/oauth/token' \
--header 'Content-Type: application/json' \
--data-raw '{
	"grant_type" : "client_credentials",
	"client_id" : "943e47a1.....afc40e491",
	"client_secret" : "7gWtVs9P.....PEyjRVqz05QdyB",
    "scope" : "organization.show organization.upsert integration.checkin booking.show organization.remove"
}'
```
{% endtab %}
{% endtabs %}
