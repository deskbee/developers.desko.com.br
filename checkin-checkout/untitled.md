# Enviado Evento

Após configurar uma automação, é necessário implementar uma integração para o Desko receber um evento que alguém passou por uma catraca/dispositivo.

Para isso é necessário disparar um POST para a API com as informações de acesso.

{% hint style="warning" %}
Entre em contato com a empresa que fornece seu **Controle de Acesso** para realizar este implementação.
{% endhint %}

{% hint style="info" %}
Apenas as Opções de Reserva: **Estações de Trabalho**, **Estacionamentos**, **Lockers**, estão integradas a esta automação de checkin.
{% endhint %}

{% swagger baseUrl="https://api.desko.com.br" path="/v1.1/integrations/checkin" method="post" summary="Automatizar Checkin / Checkout" %}
{% swagger-description %}
Recebe o código da catraca e o identificador de pessoa (Número de Matrícula ou Documento). Busca as reservas para o prédio e a pessoa, caso encontre realiza o checkin / checkout para as reservas encontradas.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Token JWT Bearer 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="device" type="string" %}
Código do dispositivo / catraca
{% endswagger-parameter %}

{% swagger-parameter in="body" name="date" type="string" %}
Data de geração do evento no dispositivo
{% endswagger-parameter %}

{% swagger-parameter in="body" name="person" type="string" %}
Código Identifica a pessoa

\




**Matrícula**

 ou 

**Documento**
{% endswagger-parameter %}

{% swagger-parameter in="body" name="entrance" type="string" %}
status entrada / saida

\




**1 **

\= entrada | 

**0**

 \= saida
{% endswagger-parameter %}

{% swagger-response status="200" description="Reservas afetadas,  será retornado duas listas: 

Success: Lista de Checkins / Checkouts realizadas com sucesso
Fails: Lista de Checkins / Checkouts que falharam" %}
```bash
{
    "data": {
        "success": [],
        "fails": []
    }
}
```
{% endswagger-response %}

{% swagger-response status="204" description="Nenhuma reserva afetada" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% tabs %}
{% tab title="Exemplo" %}
```bash
curl --location --request POST 'https://api.desko.com.br/v1.1/integrations/checkin' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token>' \
--data-raw '{
    "device": "CATRACARG2", 
    "person": "06283401000",
    "date": "2021-08-23T21:37:28-03:00",
    "entrance": 1
}'
```
{% endtab %}
{% endtabs %}
