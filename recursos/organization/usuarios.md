---
description: API de Gestão de Usuários
---

# Users

## Criar Usuário

<mark style="color:green;">`POST`</mark> `https://api.desko.com.br/v1.1/users`

#### Headers

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| Authorization | string | Bearer      |

#### Request Body

| Name           | Type    | Description                                                                                                     |
| -------------- | ------- | --------------------------------------------------------------------------------------------------------------- |
| name           | string  | Nome do usuário                                                                                                 |
| email          | string  | <p>E-mail do usuário</p><p>\</p><p><code>unique</code></p>                                                      |
| status         | boolean | <p>Situação do usuário, se está ativo no sistema</p><p>\</p><p><code>default: true</code></p>                   |
| enrollment     | string  | <p>Número de matrícula / identificador da pessoa na empresa</p><p>\</p><p><code>unqiue</code></p>               |
| is\_send\_mail | boolean | <p>Define se envia e-mail ao usuário com as informações de acesso:</p><p>\</p><p><code>default: true</code></p> |
| squad\_uuid    | string  | UUID Identificador de um Grupo                                                                                  |
| documents      | object  | <p>Lista de documentos</p><p>\</p>                                                                              |

{% tabs %}
{% tab title="201 " %}
```bash
{
    "data": {
        "uuid": "d5cd06be-583b-45de-b6ee-e6cc11cce08e",
        "name": "Michele Luna Bonilha Neto",
        "name_display": "Michele Neto",
        "email": "corona.lucas@example.com",
        "enrollment": "MATR01",
        "source": "api_client",
        "access_type": "user_password",
        "profile": "employee",
        "locale": {
            "timezone": "America\/Sao_Paulo",
            "language": "pt_BR"
        },
        "status": true,
        "person": {
            "uuid": "0318f7d6-a417-4f0b-8cdc-326ff56c52c3",
            "documents": [
                {
                    "type": "rg",
                    "doc": "292030274",
                    "is_verified": 0
                },
                {
                    "type": "cpf",
                    "doc": "81479113603",
                    "is_verified": 0
                }
            ]
        },
        "created_at": "2021-09-24T18:01:14-03:00",
        "updated_at": "2021-09-24T18:01:14-03:00"
    }
}
```
{% endtab %}

{% tab title="422 " %}
```bash
{
    "error": 422,
    "id": "unprocessable_entity",
    "message": "Foram enviados dados inválidos",
    "errors": {
        "name": [
            "{{name}} é obrigatório."
        ],
        "email": [
            "{{email}} é obrigatório."
        ]
    }
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request POST 'https://api.desko.com.br/v1.1/users' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
	"name": "Joaquin Camacho Serna Filho",
	"email": "toledo.anderson@example.org",
	"is_send_mail": false,
	"enrollment": "MATR01",
	"squad_uuid": "cd820598-e324-4f3e-9548-ce126b834704",
	"status": false,
	"documents": {
		"rg": "14.318.334-6",
		"cpf": "722.055.718-34"
	}
}'
```
{% endtab %}
{% endtabs %}

## Editar Usuário

<mark style="color:orange;">`PUT`</mark> `https://api.desko.com.br/v1.1/users/{{user_uuid}}`

#### Path Parameters

| Name             | Type   | Description     |
| ---------------- | ------ | --------------- |
| \{{user\_uuid\}} | string | UUID do Usuário |

#### Headers

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| Authorization | string | Bearer      |

#### Request Body

| Name       | Type    | Description                                                                                       |
| ---------- | ------- | ------------------------------------------------------------------------------------------------- |
| name       | string  | Nome do usuário                                                                                   |
| email      | string  | <p>E-mail do usuário</p><p>\</p><p><code>unique</code></p>                                        |
| enrollment | string  | <p>Número de matrícula / identificador da pessoa na empresa</p><p>\</p><p><code>unique</code></p> |
| status     | boolean | <p>Situação do usuário, se está ativo no sistema</p><p>\</p><p><code>default: true</code></p>     |
| documents  | object  | Lista de documentos                                                                               |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": {
        "uuid": "d5cd06be-583b-45de-b6ee-e6cc11cce08e",
        "name": "Michele Luna Bonilha Neto",
        "name_display": "Michele Neto",
        "email": "corona.lucas@example.com",
        "enrollment": null,
        "source": "api_client",
        "access_type": "user_password",
        "profile": "employee",
        "locale": {
            "timezone": "America\/Sao_Paulo",
            "language": "pt_BR"
        },
        "status": false,
        "person": {
            "uuid": "0318f7d6-a417-4f0b-8cdc-326ff56c52c3",
            "documents": [
                {
                    "type": "cpf",
                    "doc": "84561752854",
                    "is_verified": 0
                }
            ]
        },
        "created_at": "2021-09-24T18:01:14-03:00",
        "updated_at": "2021-09-24T18:01:15-03:00"
    }
}
```
{% endtab %}

{% tab title="404 UUID do usuário não encontrado" %}
```
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
curl --location --request PUT 'https://api.desko.com.br/v1.1/users/d5cd06be-583b-45de-b6ee-e6cc11cce08e' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
    "name": "Michele Luna Bonilha Neto",
    "email": "corona.lucas@example.com",
    "enrollment": "",
    "status": false,
    "documents": {
        "cpf": "845.617.528-54"
    }
}'
```
{% endtab %}
{% endtabs %}

## Obter Usuário

<mark style="color:blue;">`GET`</mark> `https://api.desko.com.br/v1.1/users/{{user_uuid}}`

#### Path Parameters

| Name             | Type   | Description  |
| ---------------- | ------ | ------------ |
| \{{user\_uuid\}} | string | UUID Usuário |

#### Query Parameters

| Name    | Type   | Description                          |
| ------- | ------ | ------------------------------------ |
| include | string | adiciona items no retorno dos dados. |

#### Headers

| Name          | Type   | Description |
| ------------- | ------ | ----------- |
| Authorization | string | Bearer      |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": {
        "uuid": "0fd24564-c901-4da8-81a9-538bef791407",
        "name": "Rafael Marin Neto",
        "name_display": "Rafael Neto",
        "email": "ketlin74@example.org",
        "enrollment": null,
        "source": "api_client",
        "access_type": "user_password",
        "profile": "employee",
        "locale": {
            "timezone": "America\/Sao_Paulo",
            "language": "pt_BR"
        },
        "status": true,
        "person": {
            "uuid": "2b7ee489-d881-45ad-a8d1-c9fa655b7dde",
            "documents": [
                {
                    "type": "cpf",
                    "doc": "49749841956",
                    "is_verified": 0
                }
            ]
        },
        "created_at": "2021-09-24T18:22:07-03:00",
        "updated_at": "2021-09-24T18:22:08-03:00",
        "squads": [
            {
                "uuid": "0e3d030a-f54d-4af6-ab7d-047ac75e5489",
                "name": "Developer",
                "created_at": "2021-09-24T18:22:07-03:00",
                "updated_at": "2021-09-24T18:22:07-03:00"
            }
        ]
    }
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request GET 'https://api.desko.com.br/v1.1/users/0fd24564-c901-4da8-81a9-538bef791407?include=squads' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>'
```
{% endtab %}
{% endtabs %}

### Include API Parameters

É possivel enviar parâmetro `include`, este parâmetro adiciona ao JSON de retorno, informações adicionais.

#### Parâmetros suportados no Include:

| include | tipo   | descrição                 |
| ------- | ------ | ------------------------- |
| squads  | string | Retorna dados de um Grupo |

{% tabs %}
{% tab title="Example Parameters" %}
```bash
exemplo: Retornando Grupos de um Usuário

?include=squads
```
{% endtab %}

{% tab title="Example Response" %}
```
{
    "data": {
        "uuid": "0fd24564-c901-4da8-81a9-538bef791407",
        "name": "Rafael Marin Neto",
        ...
        "squads": [
            {
                "uuid": "0e3d030a-f54d-4af6-ab7d-047ac75e5489",
                "name": "Developer",
                "created_at": "2021-09-24T18:22:07-03:00",
                "updated_at": "2021-09-24T18:22:07-03:00"
            }
        ]
    }
}
```
{% endtab %}
{% endtabs %}

### Search API Parameters

Você pode filtrar os dados enviando o parâmetro `search` utilizando o separador `:` para chave e valor e `;` para separar os parâmetros de busca.

```
exemplo: Buscando colaboradores que nao estão em nenhum Grupo

?search=profile:employee;is_squad=false
```

**Parâmetros suportados no Search:**

| search      | tipo      | descrição                                                                                          |
| ----------- | --------- | -------------------------------------------------------------------------------------------------- |
| email       | `string`  | Busca por e-mail de usuário                                                                        |
| name        | `string`  | Busca usuário por nome                                                                             |
| squad\_uuid | `uuid`    | Busca todos usuários do Grupo, pelo UUID do Grupo informado                                        |
| is\_squad   | `boolean` | Busca usuários que estão ou não vinculados a grupos                                                |
| profile     | `string`  | <p>Busca usuários pelo perfil de acesso</p><p><code>employee, assistant, manager, admin</code></p> |

## Listar Usuários

<mark style="color:blue;">`GET`</mark> `https://api.desko.com.br/v1.1/users`

#### Query Parameters

| Name    | Type    | Description                                                          |
| ------- | ------- | -------------------------------------------------------------------- |
| search  | string  | Filtros aplicados nas buscas                                         |
| limit   | integer | <p>limite de dados retornado</p><p>\</p><p><code>max: 250</code></p> |
| include | string  | inclui items ao retorno de dados                                     |

#### Headers

| Name          | Type   | Description  |
| ------------- | ------ | ------------ |
| Authorization | string | Bearer token |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": [
        {
            "uuid": "8fd9007b-c05e-4937-b681-a972e6d2a404",
            "name": "Dev Team",
            "name_display": "Dev Team",
            "email": "cleber@inventsys.com.br",
            "enrollment": null,
            "source": "user_password",
            "access_type": "user_password",
            "profile": "master",
            "locale": {
                "timezone": "America\/Sao_Paulo",
                "language": "pt_BR"
            },
            "status": true,
            "person": {
                "uuid": "c11ca28e-888e-477f-862f-3c5b01c39d94",
                "documents": []
            },
            "created_at": "2021-09-23T22:53:02-03:00",
            "updated_at": "2021-09-23T22:53:02-03:00",
            "squads": []
        },
        {
            "uuid": "098c9226-1a78-45ff-8f1e-fbeeaabe9ff9",
            "name": "Taís Delgado Filho",
            "name_display": "Taís Filho",
            "email": "gustavo79@example.org",
            "enrollment": null,
            "source": "api_client",
            "access_type": "user_password",
            "profile": "employee",
            "locale": {
                "timezone": "America\/Sao_Paulo",
                "language": "pt_BR"
            },
            "status": false,
            "person": {
                "uuid": "5da58826-cea8-4e98-b62f-621a79cf4763",
                "documents": [
                    {
                        "type": "cpf",
                        "doc": "95753926207",
                        "is_verified": 0
                    }
                ]
            },
            "created_at": "2021-09-24T18:28:57-03:00",
            "updated_at": "2021-09-24T18:28:58-03:00",
            "squads": [
                {
                    "uuid": "db3fdf4d-15cf-42ee-92a4-81d3f4e044a7",
                    "name": "voluptate",
                    "created_at": "2021-09-24T18:28:57-03:00",
                    "updated_at": "2021-09-24T18:28:57-03:00"
                }
            ]
        }
    ],
    "links": {
        "prev": "https://api.desko.com.br/v1.1/users?include=squads&limit=25&cursor=eyJuYW1lIjoiRHIuIEFnb3N0aW5obyBGbG9yZXMgSmltZW5lcyBKci4iLCJfcG9pbnRzVG9OZXh0SXRlbXMiOmZhbHNlfQ",
        "next": null
    },
    "meta": {
        "path": "https://api.desko.com.br/v1.1/users",
        "per_page": 25
    }
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request GET 'https://api.desko.com.br/v1.1/users?search=email:cleber@inventsys.com.br;is_squad:true' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>'
```
{% endtab %}
{% endtabs %}

## Remover Usuário

<mark style="color:red;">`DELETE`</mark> `https://api.desko.com.br/v1.1/users/{{user_uuid}}`

#### Path Parameters

| Name             | Type   | Description     |
| ---------------- | ------ | --------------- |
| \{{user\_uuid\}} | string | UUID do Usuário |

#### Headers

| Name          | Type   | Description  |
| ------------- | ------ | ------------ |
| Authorization | string | Bearer token |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": {
        "uuid": "649ceaee-a047-48c8-9327-6dfd7f64ef39",
        "name": "Luara Colaço Gomes",
        "name_display": "Laura Gomes",
        "email": "hugo15@example.com",
        "enrollment": null,
        "source": "api_client",
        "access_type": "user_password",
        "profile": "employee",
        "locale": {
            "timezone": "America\/Sao_Paulo",
            "language": "pt_BR"
        },
        "status": false,
        "person": {
            "uuid": "f36e7e9e-ae57-4305-b14a-3d9f4fa66d5f",
            "documents": []
        },
        "created_at": "2021-09-24T20:31:46-03:00",
        "updated_at": "2021-09-24T20:31:46-03:00"
    }
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request DELETE 'https://api.desko.com.br/v1.1/users/649ceaee-a047-48c8-9327-6dfd7f64ef39' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' 
```
{% endtab %}
{% endtabs %}

## Usuários em Grupos

## Add Usuários à Grupos

<mark style="color:green;">`POST`</mark> `https://api.desko.com.br/v1.1/users/squads/add`

Adicionar vários Usuários em um ou Mais Grupos

#### Headers

| Name          | Type   | Description  |
| ------------- | ------ | ------------ |
| Authorization | string | Bearer Token |

#### Request Body

| Name   | Type  | Description                 |
| ------ | ----- | --------------------------- |
| users  | array | Matriz de UUIDs de Usuários |
| squads | array | Matriz de UUIDs de Grupos   |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": [
        {
            "uuid": "1cbb45ce-1da3-4b71-b0e1-d59190a9e413",
            "name": "Jasmin Lovato Jr.",
            "name_display": "Jasmin Jr.",
            "email": "allison90@example.org",
            "enrollment": null,
            "source": "user_password",
            "access_type": "user_password",
            "profile": "employee",
            "locale": {
                "timezone": "America\/Sao_Paulo",
                "language": "pt_BR"
            },
            "status": true,
            "person": {
                "uuid": "a0614c23-ba26-43e7-9c3b-fee0a31dcb23",
                "documents": []
            },
            "created_at": "2021-09-25T19:54:12-03:00",
            "updated_at": "2021-09-25T19:54:12-03:00"
        },
        {
            "uuid": "80a0079d-3ee2-4785-b41e-529bb4e68ee6",
            "name": "Kevin Zambrano Lira Filho",
            "name_display": "Kevin Filho",
            "email": "qbenites@example.com",
            "enrollment": null,
            "source": "user_password",
            "access_type": "user_password",
            "profile": "employee",
            "locale": {
                "timezone": "America\/Sao_Paulo",
                "language": "pt_BR"
            },
            "status": true,
            "person": {
                "uuid": "e718aea3-a52e-4090-81b5-50406b77592e",
                "documents": []
            },
            "created_at": "2021-09-25T19:54:12-03:00",
            "updated_at": "2021-09-25T19:54:12-03:00"
        }
    ]
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request POST 'https://api.desko.com.br/v1.1/users/squads/add' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
    "squads": [
        "a3ed0ca6-c809-48e7-baae-543fe8fc55a2",
        "bc4bdb6b-4def-4cd9-a7fe-b5fa481101cd"
    ],
    "users": [
        "1cbb45ce-1da3-4b71-b0e1-d59190a9e413",
        "80a0079d-3ee2-4785-b41e-529bb4e68ee6"
    ]
}'
```
{% endtab %}
{% endtabs %}

## Usuários dos Grupos

<mark style="color:red;">`DELETE`</mark> `https://api.desko.com.br/v1.1/users/squads/remove`

Remove um ou mais usuários de um ou mais grupos, caso os mesmos estejam em algum grupo informado pelo UUID

#### Headers

| Name          | Type   | Description  |
| ------------- | ------ | ------------ |
| Authorization | string | Bearer token |

#### Request Body

| Name   | Type   | Description                 |
| ------ | ------ | --------------------------- |
| users  | string | Matriz de UUIDs de usuários |
| squads | string | Matriz de UUIDs de Grupos   |

{% tabs %}
{% tab title="200 " %}
```bash
{
    "data": [
        {
            "uuid": "4a5f996f-89a7-485d-9ba7-0bed43c5417e",
            "name": "Ashley Serra",
            "name_display": "Ashley Serra",
            "email": "medina.samanta@example.org",
            "enrollment": null,
            "source": "user_password",
            "access_type": "user_password",
            "profile": "employee",
            "locale": {
                "timezone": "America\/Sao_Paulo",
                "language": "pt_BR"
            },
            "status": true,
            "person": {
                "uuid": "c2730193-1402-491b-932a-dbdead4bd0f2",
                "documents": []
            },
            "created_at": "2021-09-25T20:00:32-03:00",
            "updated_at": "2021-09-25T20:00:32-03:00"
        },
        {
            "uuid": "ada97a59-d864-4e44-a828-94b0a70efa24",
            "name": "Gabriela Madeira",
            "name_display": "Gabriela Madeira",
            "email": "isadora.dacruz@example.org",
            "enrollment": null,
            "source": "user_password",
            "access_type": "user_password",
            "profile": "employee",
            "locale": {
                "timezone": "America\/Sao_Paulo",
                "language": "pt_BR"
            },
            "status": true,
            "person": {
                "uuid": "1f56398e-fc53-4827-af77-06c2c758888c",
                "documents": []
            },
            "created_at": "2021-09-25T20:00:32-03:00",
            "updated_at": "2021-09-25T20:00:32-03:00"
        }
    ]
}
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Example Request" %}
```bash
curl --location --request DELETE 'https://api.desko.com.br/v1.1/users/squads/remove' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
    "squads": [
        "fc86198f-c6d5-442a-9299-d922443c8d13",
        "40fac8e4-c171-4e88-8a49-3465037cd5c2"
    ],
    "users": [
        "4a5f996f-89a7-485d-9ba7-0bed43c5417e",
        "ada97a59-d864-4e44-a828-94b0a70efa24"
    ]
}'
```
{% endtab %}
{% endtabs %}
