# Paginação

Algumas requisições realizadas na API irão retornar uma lista de informações, estas informações não serão retornadas em uma única resposta, isso ocorre pois algumas respostas podem ter muitas informações, por isso estas requisições são paginadas.

A Api do Desko utiliza paginação por **cursor**, nesta paginação é utilizado um parâmetro chave.

O cliente recebe uma variável nomeada **cursor** junto com a resposta. Este cursor é um ponteiro que aponta para um item específico que precisa ser enviado com uma solicitação. O servidor então usa o cursor para buscar o outro conjunto de itens.

A paginação baseada em cursor é mais complexa e é preferida ao lidar com um conjunto de dados em tempo real.

Segue abaixo um exemplo de uma resposta JSON paginada por cursor:

### Request

Descrição dos parâmetros que podem ser enviados na paginação da API Desko

| Parâmetros | Descrição                                                                                           |
| ---------- | --------------------------------------------------------------------------------------------------- |
| limit      | <p>Número de objetos individuais que são devolvidos em cada página.</p><p><code>max: 250</code></p> |

{% tabs %}
{% tab title="Example" %}
```bash
curl -i -X GET 'https://api.desko.com.br/v1.1/users?limit=1' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <token>'
```
{% endtab %}
{% endtabs %}

### Response

Descrição dos parâmetros recebidos na paginação da API Desko

| Parâmetros | Descrição                                                                                                         |
| ---------- | ----------------------------------------------------------------------------------------------------------------- |
| links.next | <p>Url que informa qual a próxima página a ser requisitada. <br>Se não for exibida, esta será a última página</p> |
| links.prev | <p>Url que informa a página de dados anterior. <br>Se não for exibida, esta é a primeira página</p>               |

{% tabs %}
{% tab title="Example" %}
```bash
{
  "data": [{
    ...
  }, {
    ...
  }, {
    ...
  }],
  "links": {
    "prev": "https://api.desko.com.br/v1.1/users?cursor=eyJuYW1lIjoiS3VyaXJpbiIsIl9wb2ludHNUb05leHRJdGVtcyI6ZmFsc2V9",
    "next": "https://api.desko.com.br/v1.1/users?cursor=eyJuYW1lIjoiS3VyaXJpbiIsIl9wb2ludHNUb05leHRJdGVtcyI6dHJ1ZX0"
  },
  "meta": {
    "path": "https://api.desko.com.br/v1.1/users",
    "per_page": "2"
  }
}
```
{% endtab %}
{% endtabs %}

