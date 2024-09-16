---
description: Api de Gestão de Grupos
---

# Squads (Grupos)

## Criar Grupo

<mark style="color:green;">`POST`</mark> `https://api.desko.com.br/v1.1/squads`

#### Headers

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| Authorization | string | Bearer      |

#### Request Body

| Name | Type   | Description   |
| ---- | ------ | ------------- |
| name | string | Nome do Grupo |

{% tabs %}
{% tab title="201 " %}
```bash
{
    "data": {
        "uuid": "10d48357-f011-4c18-84d3-23ee3992990a",
        "name": "Developer",
        "created_at": "2021-09-27T11:36:04-03:00",
        "updated_at": "2021-09-27T11:36:04-03:00"
    }
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request POST 'https://api.desko.com.br/v1.1/squads' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
    "name": "Developer"
}'
```
{% endtab %}
{% endtabs %}

## Editar Grupo

<mark style="color:orange;">`PUT`</mark> `https://api.desko.com.br/v1.1/squads/{{squad_uuid}}`

#### Path Parameters

| Name              | Type   | Description   |
| ----------------- | ------ | ------------- |
| \{{squad\_uuid\}} | string | UUID do Grupo |

#### Headers

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| Authorization | string | Bearer      |

#### Request Body

| Name | Type   | Description                                            |
| ---- | ------ | ------------------------------------------------------ |
| name | string | <p>Nome do Grupo</p><p>\</p><p><code>unique</code></p> |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": {
        "uuid": "3ba50c76-4c55-469c-adf2-76a5abb3b27a",
        "name": "Grupo Teste",
        "created_at": "2021-09-23T17:21:46-03:00",
        "updated_at": "2021-09-23T17:21:46-03:00"
    }
}
```
{% endtab %}

{% tab title="404 UUID não encontrado" %}
```bash
{
    "error": 404,
    "id": "not_found",
    "message": "Oops ... Página não encontrada!"
}

```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request PUT 'https://api.desko.com.br/v1.1/squads/3ba50c76-4c55-469c-adf2-76a5abb3b27a' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
    "name" : "Grupo Teste"
}'
```
{% endtab %}
{% endtabs %}

## Obter Grupo

<mark style="color:blue;">`GET`</mark> `https://api.desko.com.br/v1.1/squads/{{squad_uuid}}`

#### Path Parameters

| Name              | Type   | Description   |
| ----------------- | ------ | ------------- |
| \{{squad\_uuid\}} | string | UUID do Grupo |

#### Headers

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| Authorization | string | Bearer      |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": {
        "uuid": "3ba50c76-4c55-469c-adf2-76a5abb3b27a",
        "name": "Grupo Teste",
        "created_at": "2021-09-23T17:21:46-03:00",
        "updated_at": "2021-09-23T17:21:46-03:00"
    }
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request GET 'https://api.desko.com.br/v1.1/squads/3ba50c76-4c55-469c-adf2-76a5abb3b27a' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>'
```
{% endtab %}
{% endtabs %}

### Search API Parameters

Ao listar grupos você pode filtrar os dados enviando o parâmetro `search`.\
Neste parâmetro você deve usar o separador `:` para chave e valor e `;` para separar os parâmetros de busca.

```
exemplo: Buscando grupos por nome

?search=name:Developer
```

**Parâmetros suportados no Search**

| Search | Tipo     | Descrição     |
| ------ | -------- | ------------- |
| name   | `string` | Nome do Grupo |

## Listar Grupos

<mark style="color:blue;">`GET`</mark> `https://api.desko.com.br/v1.1/squads`

#### Headers

| Name          | Type   | Description  |
| ------------- | ------ | ------------ |
| Authorization | string | Bearer Token |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": [
        {
            "uuid": "61786427-7133-492e-b3af-1376f1f792b8",
            "name": "Developer",
            "created_at": "2021-09-27T12:36:20-03:00",
            "updated_at": "2021-09-27T12:36:20-03:00"
        },
        {
            "uuid": "a5242750-1523-457a-b0d3-377e1312573c",
            "name": "Equipe TI",
            "created_at": "2021-09-11T00:19:12-03:00",
            "updated_at": "2021-09-27T16:02:24-03:00"
        },
    ],
    "links": {
        "prev": null,
        "next": null
    },
    "meta": {
        "path": "https://api.desko.com.br/v1.1/squads",
        "per_page": 1
    }
}

```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request GET 'https://api.desko.com.br/v1.1/squads' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>'
```
{% endtab %}
{% endtabs %}

## Remover Grupo

<mark style="color:red;">`DELETE`</mark> `https://api.desko.com.br/v1.1/squads/{{squad_uuid}}`

#### Path Parameters

| Name              | Type   | Description   |
| ----------------- | ------ | ------------- |
| \{{squad\_uuid\}} | string | UUID do Grupo |

#### Headers

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| Authorization | string | Bearer      |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": {
        "uuid": "bea898d9-2bb7-4aa3-9597-3b3390167a38",
        "name": "Developer",
        "created_at": "2021-09-27T12:42:06-03:00",
        "updated_at": "2021-09-27T12:42:06-03:00"
    }
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request DELETE 'https://api.desko.com.br/v1.1/squads/bea898d9-2bb7-4aa3-9597-3b3390167a38' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>'
```
{% endtab %}
{% endtabs %}
