# Response

Todas as respostas retornam no formato **JSON** válido.

As datas são retornados no formato ISO8601.

{% tabs %}
{% tab title="Example" %}
```bash
{
  // ...
  "created_at": "2012-01-01T12:00:00Z",
  "updated_at": "2012-01-01T13:00:00Z",
  // ...
}
```
{% endtab %}
{% endtabs %}

Cada resposta retorna um código HTTP apropriado conforme especificação [https://tools.ietf.org/html/rfc7231#section-6](https://tools.ietf.org/html/rfc7231#section-6)

{% hint style="success" %}
#### Retornos Sucesso
{% endhint %}

| Códigos | Mensagem   | Descrição                                                                                            |
| ------- | ---------- | ---------------------------------------------------------------------------------------------------- |
| 200     | OK         | Requisição com êxito para um pedido GET, DELETE ou PATCH, PUT que se completou de forma síncrona     |
| 201     | Created    | Requisição com êxito para um pedido POST, PUT                                                        |
| 202     | Accepted   | Requisição aceita para um pedido POST, PUT, DELETE, ou PATCH que será processada de forma assíncrona |
| 204     | No Content | Requisição realizada com sucesso, entretanto não existem conteúdos para retornar                     |

{% tabs %}
{% tab title="Example" %}
```bash
{
    "data": {
        "uuid": "68b0327b-e0f9-40e2-a81c-15fb0d981ede",
        "name": "Grupo Teste",
        "is_checkin_home_office": false,
        "created_at": "2021-09-23T14:28:36-03:00",
        "updated_at": "2021-09-23T14:28:36-03:00"
    }
}
```
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
#### Retornos Erros
{% endhint %}

Na situação de retorno de algum erro, HTTP Status Code diferente de 2xx por exemplo, será gerado no corpo da resposta um erro estruturados e consistente.

| Campo   | Tipo      | Obrigatório       | Descrição                                                                     |
| ------- | --------- | ----------------- | ----------------------------------------------------------------------------- |
| error   | Int       | **`Obrigatório`** | Código do erro, mesmo código retornado no Status HTTP (legível para máquinas) |
| id      | String    | **`Obrigatório`** | Identificador do erro ocorrido, (legível para máquinas)                       |
| message | String    | **`Obrigatório`** | Mensagem amigável com a explicação do erro, legível para humanos.             |
| errors  | String\[] | `Opcional`        | Parâmetros dos erros, listando quais foram os erros informados na requisição. |

{% tabs %}
{% tab title="Example" %}
```bash
{
  "error": 422
  "id": "unprocessable_entity",
  "message": "The given data failed to pass validation.",
  "errors": {
    "email": ["The email field is required."],
    "name": ["The name field is required."]
  }
}
```
{% endtab %}
{% endtabs %}
