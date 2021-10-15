---
description: Consulta de Reservas
---

# Bookings

{% swagger baseUrl="https://api.desko.com.br" path="/v1.1/bookings/{{booking_uuid}}" method="get" summary="Obter Reserva" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="{{booking_uuid}}" type="string" %}
UUID da Reserva
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Bearer <token>
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```bash
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Request" %}
```bash
curl --location --request GET 'https://api.desko.com.br/v1.1/bookings/77012570-4a47-4827-8d17-f5a1ddec06c1' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>'
```
{% endtab %}

{% tab title="Response" %}
```json
{
    "data": {
        "uuid": "85dfd756-70ac-41b5-b66b-dab31137ecc1",
        "start_date": "2021-09-27T18:00:00-03:00",
        "end_date": "2021-09-27T19:00:00-03:00",
        "place": {
            "uuid": "75e44930-9dce-4b06-8534-2e5810c7f1e9",
            "qrcode": "EST.AGUIAS.KMS.1/001",
            "type": "workspace",
            "name": "EST 1.001",
            "name_display": "EST 1.001",
            "capacity": 1,
            "area": {
                "address": "Rua Aguias, Porto Alegre",
                "floor": {
                    "uuid": "d1935978-f2f5-4dee-8724-c35dfe098235",
                    "name": "1º Andar",
                    "is_active": true
                },
                "building": {
                    "uuid": "f6ff259a-4cdb-4e44-ae37-c7b58a4f3daa",
                    "name": "Kamisama",
                    "is_active": true
                },
                "site": {
                    "uuid": "fa062508-472d-4612-842d-a8759bba510a",
                    "name": "Shinden",
                    "is_active": true
                }
            },
            "sector": {
                "uuid": "dacf8263-6f90-4419-a4b5-73140915ffda",
                "name": "Developer"
            },
            "external_resource_id": "",
            "is_mapped": true,
            "created_at": "2021-05-12T21:26:42-03:00",
            "updated_at": "2021-08-29T17:54:34-03:00"
        },
        "state": "reserved",
        "person": {
            "uuid": "ffefde9d-5005-4908-9400-1ff46cb773a6",
            "name": "Son Gohan",
            "name_display": "Son Gohan",
            "email": "gohan@pipedev.com.br",
            "enrollment": "",
            "created_at": "2021-05-12T21:07:25-03:00",
            "updated_at": "2021-05-12T21:07:25-03:00"
        },
        "owner": {
            "uuid": "ffefde9d-5005-4908-9400-1ff46cb773a6",
            "name": "Son Gohan",
            "name_display": "Son Gohan",
            "email": "gohan@pipedev.com.br",
            "enrollment": "",
            "created_at": "2021-05-12T21:07:25-03:00",
            "updated_at": "2021-05-12T21:07:25-03:00"
        },
        "created_at": "2021-09-27T16:12:49-03:00",
        "updated_at": "2021-09-27T16:12:49-03:00"
    }
}
```
{% endtab %}
{% endtabs %}

### Search API Parameters

Você pode filtrar os dados enviando o parâmetro `search` utilizando o separador `:` para chave e valor e `;`  para separar os parâmetros de busca.

```
exemplo: Buscando reservas válidas no mes de setembro

?search=period:2021/09/01,2021/09/30;state=reserved
```

**Parâmetros suportados no Search:**

| search        | tipo        | descrição                                                                                                                                                                                                                                                                                      |
| ------------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| period        | `date,date` | <p>Data de Inicio e Fim das reservas no formato <code>Y/m/d</code></p><p><code>exemplo: 2021/09/01,2021/09/30</code></p><p><code>default: Dia de Hoje</code></p>                                                                                                                               |
| state         | `string`    | <p>Situação da Reserva:</p><p></p><p><code>reserved</code> Reserva Válida<br><code>waiting</code> Aguardando Aprovação</p><p><code>fall</code> Reserva Expirada<br><code>last</code> Ocupação Encerrada<br><code>busy</code> Ocupação Andamento<br><code>rejected</code> Reserva Rejeitada</p> |
| type          | `string`    | <p>Tipo de Opção de Reserva</p><p><code>workspace, meetingroom, dininghall, parking, locker</code></p>                                                                                                                                                                                         |
| place         | `string`    | Nome ou QrCode de uma Opção de Reserva                                                                                                                                                                                                                                                         |
| sector_uuid   | `uuid`      | Reservas por Setor                                                                                                                                                                                                                                                                             |
| building_uuid | `uuid`      | Reservas por Prédio                                                                                                                                                                                                                                                                            |
| site_uuid     | `uuid`      | Reservas por Unidade                                                                                                                                                                                                                                                                           |
| floor_uuid    | `uuid`      | Reservas por andarndar                                                                                                                                                                                                                                                                         |
| squad_uuid    | `uuid`      | Reservas de um Grupo                                                                                                                                                                                                                                                                           |

{% swagger baseUrl="https://api.desko.com.br" path="/v1.1/bookings" method="get" summary="Listar Reservas" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Bearer Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="search" type="string" %}
filtros aplicados nas buscas
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="integer" %}
limite de reservas retornada

\




`max: 250`
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```bash
{
    "data": [
        {
            "uuid": "85dfd756-70ac-41b5-b66b-dab31137ecc1",
            "start_date": "2021-09-27T18:00:00-03:00",
            "end_date": "2021-09-27T19:00:00-03:00",
            "place": {
                "uuid": "75e44930-9dce-4b06-8534-2e5810c7f1e9",
                "qrcode": "EST.AGUIAS.KMS.1/001",
                "type": "workspace",
                "name": "EST 1.001",
                "name_display": "EST 1.001",
                "capacity": 1,
                "area": {
                    "address": "Rua Aguias, Porto Alegre",
                    "floor": {
                        "uuid": "d1935978-f2f5-4dee-8724-c35dfe098235",
                        "name": "1º Andar",
                        "is_active": true
                    },
                    "building": {
                        "uuid": "f6ff259a-4cdb-4e44-ae37-c7b58a4f3daa",
                        "name": "Kamisama",
                        "is_active": true
                    },
                    "site": {
                        "uuid": "fa062508-472d-4612-842d-a8759bba510a",
                        "name": "Shinden",
                        "is_active": true
                    }
                },
                "sector": {
                    "uuid": "dacf8263-6f90-4419-a4b5-73140915ffda",
                    "name": "Developer"
                },
                "external_resource_id": "",
                "is_mapped": true,
                "created_at": "2021-05-12T21:26:42-03:00",
                "updated_at": "2021-08-29T17:54:34-03:00"
            },
            "state": "reserved",
            "person": {
                "uuid": "ffefde9d-5005-4908-9400-1ff46cb773a6",
                "name": "Son Gohan",
                "name_display": "Son Gohan",
                "email": "gohan@pipedev.com.br",
                "enrollment": "",
                "created_at": "2021-05-12T21:07:25-03:00",
                "updated_at": "2021-05-12T21:07:25-03:00"
            },
            "owner": {
                "uuid": "ffefde9d-5005-4908-9400-1ff46cb773a6",
                "name": "Son Gohan",
                "name_display": "Son Gohan",
                "email": "gohan@pipedev.com.br",
                "enrollment": "",
                "created_at": "2021-05-12T21:07:25-03:00",
                "updated_at": "2021-05-12T21:07:25-03:00"
            },
            "created_at": "2021-09-27T16:12:49-03:00",
            "updated_at": "2021-09-27T16:12:49-03:00"
        },
        {
            "uuid": "3b9f6a7d-7e99-4ca9-8cd5-24e8cf4a748b",
            "start_date": "2021-09-27T17:00:00-03:00",
            "end_date": "2021-09-27T18:00:00-03:00",
            "place": {
                "uuid": "5c9aea04-fcc2-4ff8-b2e7-1529534518d4",
                "qrcode": "SL.AGUIAS.KMS.1/001",
                "type": "meetingroom",
                "name": "SL 1.001",
                "name_display": "SL 1.001",
                "capacity": 12,
                "area": {
                    "address": "Rua Aguias, Porto Alegre",
                    "floor": {
                        "uuid": "d1935978-f2f5-4dee-8724-c35dfe098235",
                        "name": "1º Andar",
                        "is_active": true
                    },
                    "building": {
                        "uuid": "f6ff259a-4cdb-4e44-ae37-c7b58a4f3daa",
                        "name": "Kamisama",
                        "is_active": true
                    },
                    "site": {
                        "uuid": "fa062508-472d-4612-842d-a8759bba510a",
                        "name": "Shinden",
                        "is_active": true
                    }
                },
                "sector": null,
                "external_resource_id": null,
                "is_mapped": true,
                "created_at": "2021-05-26T17:39:51-03:00",
                "updated_at": "2021-08-03T18:31:18-03:00"
            },
            "state": "reserved",
            "person": {
                "uuid": "ffefde9d-5005-4908-9400-1ff46cb773a6",
                "name": "Son Gohan",
                "name_display": "Son Gohan",
                "email": "gohan@pipedev.com.br",
                "enrollment": "",
                "created_at": "2021-05-12T21:07:25-03:00",
                "updated_at": "2021-05-12T21:07:25-03:00"
            },
            "owner": {
                "uuid": "ffefde9d-5005-4908-9400-1ff46cb773a6",
                "name": "Son Gohan",
                "name_display": "Son Gohan",
                "email": "gohan@pipedev.com.br",
                "enrollment": "",
                "created_at": "2021-05-12T21:07:25-03:00",
                "updated_at": "2021-05-12T21:07:25-03:00"
            },
            "created_at": "2021-09-27T16:13:16-03:00",
            "updated_at": "2021-09-27T16:13:16-03:00"
        }
    ],
    "links": {
        "prev": null,
        "next": "https://api.desko.com.br/v1.1/bookings?cursor=eyJib29raW5ncy5pZCI6MTEzNzg3LCJfcG9pbnRzVG9OZXh0SXRlbXMiOnRydWV9"
    },
    "meta": {
        "path": "https://api.desko.com.br/v1.1/bookings",
        "per_page": "25"
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request GET 'https://api.desko.com.br/v1.1/bookings?search=period:2021/09/27,2021/09/27' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' 
```
{% endtab %}
{% endtabs %}
