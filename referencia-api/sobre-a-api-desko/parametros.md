# Parâmetros

A API possui suporte a dois métodos para o envio de parâmetros

### QueryString

{% tabs %}
{% tab title="Example" %}
```bash
curl --request POST 'https://api.desko.com.br/v1.1/oauth/token' \
--data-raw 'grant_type=client_credentials&client_id=942ff....e4e23676e'
```
{% endtab %}
{% endtabs %}

### JSON

{% tabs %}
{% tab title="Example" %}
```bash
curl --request POST 'https://api.desko.com.br/v1.1/oauth/token' \
--header   'Content-Type: application/json' \
--data-raw '{
  "grant_type" : "client_credentials",
  "client_id" : "942f....4e23676e",
  "client_secret" : "",
  "scope" : ""
}'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Para enviar um JSON, é necessário informar no header:\
**content-type: application/json**
{% endhint %}

## Search API Parameters

`... em contrução ...`

## Include API Parameters

`... em construção ...`

## Paginação

{% content-ref url="paginacao.md" %}
[paginacao.md](paginacao.md)
{% endcontent-ref %}

