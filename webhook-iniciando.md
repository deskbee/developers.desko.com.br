# Configurando

{% hint style="info" %}
É necessário que a url do cliente esteja em **https**, caso contrário irá falhar a solicitação
{% endhint %}

Acesse o Painel do Desko (Usuário Admin ou Master) e Configure um WebHook

### Re-Tentativas

Em caso de falha, por exempol: o cliente retornar um Http Status diferente de **200**, tentamos mais 5x, para não sobrecarregar a fila e não sobrecarregar o cliente, vamos esperar algum tempo entre cada tentativa.

Por padrão, esperamos 10 segundos entre a primeira e a segunda tentativa, 100 segundos entre a terceira e a quarta, 1000 entre a quarta e a quinta e assim por diante.

A quantidade máxima de segundos que esperaremos é 100.000, o que é cerca de 27 horas.

### Validação WebHook

O Cliente deve validar a origem do POST, isto é, se ele foi realmente enviado pelo Desko, para fazer isso, deve-se calcular o HMAC-SHA1 do body da requisição HTTP e compará-lo com o header X-Hub-Signature.

Descrição dos parâmetros que utilizamos nos exemplos abaixo:

| parâmetro no exemplo             | descrição                                      |
| -------------------------------- | ---------------------------------------------- |
| {chave de integração do webhook} | chave de segurança configurado no painel desko |
| {conteudo do payload}            | JSON recebido no payload/body do POST          |
| {signature}                      | signature recebido em X-Hub-Signature          |

**Exemplos**

{% tabs %}
{% tab title="PHP" %}
```php
$signature = hash_hmac('sha256', file_get_contents('php://input'), {chave de integração do webhook});
if ($signature === $_SERVER['HTTP_SIGNATURE']) {
  printf('Assinatura Valida, foi recebido pelo Desko');
}
```
{% endtab %}

{% tab title="Curl" %}
```bash
EXPECTED_SIGNATURE=`cat {conteudo do payload} | openssl dgst -sha1 -hmac "{chave de integração do webhook}"`
SIGNATURE={signature}
if [ "$SIGNATURE" = "$EXPECTED_SIGNATURE" ]; then
  echo "Assinatura Valida, foi recebido pelo Desko"
fi
```
{% endtab %}

{% tab title="NodeJS" %}
```javascript
import { createHmac } from 'crypto'
const signature = createHmac('sha1', {chave de integração do webhook}).update({conteudo do payload}).digest('hex')
if (equals(signature, {signature})) {
  console.log('Assinatura Valida, foi recebido pelo Desko')
}
```
{% endtab %}
{% endtabs %}
