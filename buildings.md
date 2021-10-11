---
description: Api Estrutura Predial
---

# Buildings

### Include API Parameters

É possivel enviar parâmetro `include`, este parâmetro adiciona ao JSON de retorno, informações adicionais.

#### Parâmetros suportados no Include:

| include | tipo     | descrição                    |
| ------- | -------- | ---------------------------- |
| floors  | `string` | retorna os andares do prédio |
| site    | `string` | retorna a unidade do prédio  |

{% tabs %}
{% tab title="Example Parameters" %}
```bash
exemplo: Retornando Unidade e Andares

?include=floors;site
```
{% endtab %}

{% tab title="Example Response" %}
```
{
    "data": {
        "uuid": "99297322-1fe4-41a8-ab1f-98c2cf257be6",
        ...
        "floors": [
            {
                "uuid": "1492386f-2852-4073-a1ea-6f07d310a9ee",
                "name": "1º Andar",
                "is_active": true
            }
        ],
        "site": {
            "uuid": "fa062508-472d-4612-842d-a8759bba510a",
            "name": "Unidade POA",
            "is_active": true
        }
    }
}
```
{% endtab %}
{% endtabs %}

{% swagger baseUrl="https://api.desko.com.br" path="/v1.1/buildings/{{building_uuid}}" method="get" summary="Obter Prédio" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="{{building_uuid}}" type="string" %}
UUID do Prédio
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Bearer <token>
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```bash
{
    "data": {
        "uuid": "99297322-1fe4-41a8-ab1f-98c2cf257be6",
        "name": "Kamisama",
        "address": "Rua Aguias, 587, Porto Alegre",
        "is_active": true,
        "floors": [
            {
                "uuid": "1492386f-2852-4073-a1ea-6f07d310a9ee",
                "name": "1º Andar",
                "is_active": true
            }
        ],
        "site": {
            "uuid": "fa062508-472d-4612-842d-a8759bba510a",
            "name": "Shinden",
            "is_active": true
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

```bash
curl --location --request GET 'https://api.desko.com.br/v1.1/buildings/2e03b201-8b02-4c5a-8b0e-7b8c259810b6?include=site;floors' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>'
```

{% swagger baseUrl="https://api.desko.com.br" path="/v1.1/buildings" method="get" summary="Listar Prédios" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Bearer Token
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```bash
{
    "data": [
        {
            "uuid": "99297322-1fe4-41a8-ab1f-98c2cf257be6",
            "name": "Casa",
            "address": "Rua Aguias, 587, Porto Verde, Alvorada - 94858-570",
            "is_active": true,
            "floors": [
                {
                    "uuid": "1492386f-2852-4073-a1ea-6f07d310a9ee",
                    "name": "1º Andar",
                    "is_active": true
                }
            ],
            "site": {
                "uuid": "fa062508-472d-4612-842d-a8759bba510a",
                "name": "PipeDev",
                "is_active": true
            }
        },
        {
            "uuid": "f6ff259a-4cdb-4e44-ae37-c7b58a4f3daa",
            "name": "Kamisama",
            "address": "Rua Aguias, Porto Alegre",
            "is_active": true,
            "floors": [
                {
                    "uuid": "20d72acd-51df-43a0-9dd8-a020cc315560",
                    "name": "E1",
                    "is_active": true
                },
                {
                    "uuid": "d1935978-f2f5-4dee-8724-c35dfe098235",
                    "name": "1º Floor",
                    "is_active": true
                },
                {
                    "uuid": "bd1f2219-5b63-45aa-9262-bfb035d09250",
                    "name": "2º Floor",
                    "is_active": true
                }
            ],
            "site": {
                "uuid": "fa062508-472d-4612-842d-a8759bba510a",
                "name": "Shinden",
                "is_active": true
            }
        }
    ],
    "links": {
        "prev": null,
        "next": "https://api.desko.com.br/v1.1/buildings?limit=2&include=floors%3Bsite&cursor=eyJhcmVhcy5pZCI6Mjg0NCwiX3BvaW50c1RvTmV4dEl0ZW1zIjp0cnVlfQ"
    },
    "meta": {
        "path": "https://api.desko.com.br/v1.1/buildings",
        "per_page": "2"
    }
}
```
{% endswagger-response %}
{% endswagger %}
